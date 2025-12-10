+++
url = "/guides/deployer-app-react/"
title = "Deploy a Create React App app"
layout = "howto"
hidden = true
tags = [ "deploy", "static", "React", "front-end" ]
+++

An application consistent with [React](https://reactjs.org/) is essentially made up of static _assets_ for its production part.

Si le cycle de développement fait intervenir Node.js pour servir les pages/vues dans un serveur HTTP avec tout le
confort des outils de développement (_hot-reloading_, etc.), elle n'est pas nécessaire pour sa mise en production. A simple
web server will do the deal:

> Set up your favorite HTTP server so that a visitor to your site is served index.html, and requests to static paths
> like /static/js/main.[hash].js are served with the contents of the /static/js/main.[hash].js file.

## _Alwaysdata_

Simply create a [Static Files](sites/static-files) site pointing to the directory of your choice (e.g.
`www/my-app`).

## Development co-operation

Start by adding in your `package.json` file an entry telling the build the final , for example:

```json
"homepage": "https://[account].alwaysdata.net/my-app"
```

In your local development environment, run the _build_ task. If you used a tool like Create
React App to initialize your project, this is available _via_ the _npm_
`npm run build`. This command will produce the static _assets_ in a `build` directory.

Vous pouvez ensuite déployer ces fichiers résultant du _build_ dans le répertoire indiqué précédemment lors de la
création du site, par exemple via [_rsync/SSH_](remote-access/ssh) :

```sh
rsync -rz --mkpath build/ [account]@ssh-[account].alwaysdata.net:www/my-app
```
