+++
url = "/guides/gitlab/"
title = "How to Install GitLab"
layout = "howto"
hidden = true
tags = [ "development" ]
+++

[GitLab](https://about.gitlab.com/) is a software development platform with wiki, bug tracking, code review, integration and continuous deployment...

It is possible to install it on the **[Private Cloud - dedicated servers and Gold](accounts/billing/private-cloud-prices)**, here are the steps to follow.

\*\*RDBMS [PostgreSQL](databases/postgresql) and [Redis](databases/redis) will need to be installed on the server. \* If not, [contact support](https://admin.alwaysdata.com/support/add).

The installation must be performed on a **blank account**. We will make the following information for our example:

- Account name: `foobar`
- Ruby version: `2.7`
- Node.js version: `14.17`

GitLab impeded the need for these versions that are to be defined in the **Environment** menu.

## Setup

1. Create the PostgreSQL database in the **Databases > PostgreSQL** menu by enabling the `pg_trgm` and `btree_gist` extensions.

2. If you are using an inferior [RAM limit](advanced/system-resources-alerts-and-limitations) at 10GB, increase it in the **Advanced> Resources** menu.

3. Run the following commands in [SSH](remote-access/ssh) at the root of the account:

```sh
npm install --global yarn

git clone https://gitlab.com/gitlab-org/gitaly. it -b 14-4-stable gitaly
cd gitaly/
mkdir ~/local
make git GIT_PREFIX=~/local/
export PATH=~/local/bin/:$PATH
cd
rm -en ~/gitaly

git clone https://gitlab. om/gitlab-org/gitlab-foss. it -b 14-4-stable gitlab
cd gitlab/

cp config/gitlab.yml.example config/gitlab.yml
sed -i "s,/home/git/,/home/$(whoami)/,g" config/gitlab. ml
sed -i "s,# user: git,user: $(whoami)," config/gitlab.yml
sed -i "s,bin_path: /usr/bin/git,bin_path: /home/$(whoami)/local/bin/git," config/gitlab.yml
```

---

**Edit `config/gitlab.yml` file**

```sh
nano config/gitlab.yml
```

In the _production > gitlab_ section edit:

- the line `host: localhost` to provide the desired address of the GitLab site. This can for example be the account address: `foobar.alwaysdata.net`.
- the `email` paragraph by the required email information. For example:

```yml
email_from: foobar@alwaysdata.net
email_reply_to: foobar@alwaysdata.net
```

---

```sh
cp config/secrets.yml.example config/secrets.yml
chmod 0600 config/secrets.yml
mkdir -p public/uploads
chmod 0700 public/uploads

cp config/puma. b.example config/puma.rb
sed -i "s,/home/git/,/home/$(whoami)/,g" config/puma.rb

git config --global gc. uto 0
git config --global repack.writeBitmaps true
git config --global receive.advertisePushOptions true
git config --global core. syncObjectFiles true

cp config/resque.yml.example config/resque.yml

cp config/database.yml.postgresql config/database.yml
```

---

**Changing `config/database.yml` file**

```sh
nano config/database.yml
```

Replace the `database`, `username` , `host` and `password` keys and the first section (production) with your account. Example:

```yml
database: foobar_gitlab
username: foobar
password: "his password"
host: postgresql-foobar.alwaysdata.net
```

The database is the one created at the beginning of this guide.

---

```sh
bundle config set --local deployment 'true'
bundle config set --local without 'development test mysql aws kerberos'
bundle install

bundle exec rake gitlab:shell:install RAILS_ENV=production

bundle exec rake "gitlab:workhorse:install[/home/$(whoami)/gitlab-workhorse]" RAILS_ENV=production

cd
git clone https://gitlab.com/gitlab-org/gitlab-pages.git
cd gitlab-pages
git checkout v$(<~/gitlab/GITLAB_PAGES_VERSION)
make

cd ~/gitlab
bundle exec rake "gitlab:gitaly:install[/home/$(whoami)/gitaly,/home/$(whoami)/repositories]" RAILS_ENV=production
~/gitlab/bin/daemon_with_pidfile ~/gitlab/tmp/pids/gitaly.pid ~/gitaly/_build/bin/gitaly ~/gitaly/config.toml >> ~/gitlab/log/gitaly.log 2>&1 &

bundle exec rake gitlab:db:configure RAILS_ENV=production

cp lib/support/init.d/gitlab ~/init
cp lib/support/init.d/gitlab.default.example ~/default
sed -i "s,/etc/default/gitlab,~/default,g" ~/init
sed -i 's,^exit$,[ "$2" = "-f" ] \&\& sleep infinity,g' ~/init
sed -i "s,app_user=\"git\",app_user=\"$(whoami)\"," ~/default
sed -i 's,-listenNetwork unix -listenAddr $socket_path/gitlab-workhorse.socket,-listenNetwork tcp -listenAddr [::]:8100,' ~/default

bundle exec rake gettext:compile RAILS_ENV=production
yarn install --production --pure-lockfile

bundle exec rake gitlab:assets:compile RAILS_ENV=production NODE_ENV=production
```

It is the latter command that requires a large amount of RAM. The amount required varies depending on the number of hores and it may be necessary to increase it if you encounter errors at this stage.

## Create service

Create an [service](services) with the following details:

- _Name_: GitLab
- _Command_: `~/init restart -f`

## Site creation

Create an [site](sites/add-a-site) with the following details:

- _Name_: GitLab
- _Type_: User Program
- _Addresses_: the address in config.yml - In our example `foobar.alwaysdata.net`
- _Command_: `true`

This site must not listen on port `8100`, check in the explanatory text of the field _Command_. This is normally the case, since it is the only site.

{{% notice note %}}
Default account username is _root_. You will choose its password when you first log in to the site and will be able to change its username later.
{{%/notice %}}
