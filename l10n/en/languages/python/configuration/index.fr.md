+++
url = "/languages/python/configuration/"
title = "Configure Python"
layout = "man"
hidden = true
tags = [ "python" ]
+++

`[paquet]` and `[version]` are to be replaced by the package name and version to install.

## Supported Versions

|                                                                                                                                                                                                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 3.14 \\|3.13 \\| 3.12 \\| 3.11 \\| 3.10 \\| 3.9 \\| 3.8 \\| 3.7 \\| 3.6 \\| 3.5 \\| 3.4 \\| 3.3 |
| 2.7 \\| 2.6 \\| 2.5 \\| 2.4                                                                                                                                                                                                             |

The default version can be changed in the alwaysdata administration, **Environment > Python**. This version is especially used when you start `python`.

Versions are not forcefully [already installed](languages#versions).

## Error logs

Python is running behind [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/), you can check the error logs in the `$HOME/admin/logs/uwsgi/[id]file. og`, or [id] is the identifier of your site, specified in the **Web > Sites** section.

An excerpt of these logs is present in the alwaysdata administration interface (Logs - 📄).

## Binary to use

You must always use `python` (or `/usr/bin/python`). Never use `python3`, `python2`, `python2.7`, or any other command.

To force a different Python version to the default one, set the `PYTHON_VERSION` environment variable:

```sh
$ PYTHON_VERSION=2.7 python
```

In your scripts, use `/usr/bin/python` as _shebang_:

```
#!/usr/bin/python
```

To force a particle Python version:

```
#!/usr/bin/eval PYTHON_VERSION=2.7 python
```

Other binaries included in Python (`2to3`, `pep8`, `pip`, `pydoc`...) work in the same way.

## Environments|Environment

Your Python environment is initially empty, without any library preinstalled outside the standard library. You can use `pip` to install packages, this is the standard Python tool:

```sh
$ python -m pip install [paquet]
```

Packages are installed in the standard$HOME/.local`directory and are automatically added to`sys.path\` by Python.

Warning, you will need to reinstall the packages if you are switching to a major version of Python (3.5 and 3. are two major versions different, while 3.5.1 and 3.5.2 have the same major version).

It is recommended to use virtual environments if you are using multiple separate Python applications so that each has its own remote environment.

With Python 3, use `venv`:

```sh
$ python -m venv myenv
```

With Python 2, use `virtualenv`:

```sh
$ virtualenv
```

Once your virtual environment is installed, you can activate it with:

```sh
$ source myenv/bin/activate
```

### Install Package

Install the latest version of a package:

```sh
$ python -m pip install [paquet]
```

You can specify a specific version:

```sh
$ python -m pip install [paquet]==[version]
```

To install a set of packages defined in a `requirements.txt` file:

```sh
$ python -m pip install -r requirements.txt
```

### Uninstall Package

```sh
$ python -m pip uninstall [paquet]
```

### Install a package with Distutils

You can install a package using Distutils without pip:

```sh
$ python setup.py install --user
```

If you are using a virtual environment, it is not necessary to specify `--user`.

## WSGI Deployment

For an [WSGI]application (https://wsgi.readthedocs.io) to be accessible via the web, you need to add a site in the **Web > Sites** section of the backend:

{{< fig "images/python-wsgi.png" "">}}

- type: choose _Python WSGI_;
- application path: The file path of your WSGI application.

You can also fill in several optional fields:

- the working directory of your application;
- environment variables to be defined;
- a specific Python version to use;
- the virtualenv directory to use.

## ASGI Deployment

Apps based on standard [ASGI](https://asgi.readthedocs.io) such as asynchronous Python frameworks can use the site type _[User Program](sites/user-program)_ in the **Web > Sites** section. Best known HTTP server is [Uvicorn](https://www.uvicorn.org/).

{{< fig "images/user-program.en.png" "User Program Site Type" >}}

You will need to listen to the HTTP server on IPv6 and on the given port. For example:

- Command: `uvicorn example:app --reload --port $PORT --host $IP`

---

- [Deploy a Fastapi application (asyncio)](https://vincent.jousse.org/blog/fr/tech/comment-deployer-fastapi-chez-alwaysdata/) (platform user guide)
