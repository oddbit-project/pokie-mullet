# pokie-mullet
[![pypi](https://img.shields.io/pypi/v/pokie-mullet.svg)](https://pypi.org/project/pokie-mullet/)
[![license](https://img.shields.io/pypi/l/pokie-mullet.svg)](https://git.oddbit.org/OddBit/pokie-mullet/src/branch/master/LICENSE)

Barebones HTTP proxy for Python-powered SPA applications - Mounts a Flask or Pokie application on a slug (/api by default)
and proxies all other requests to a running HTTP server (such as a NodeJS dev server), or to a static SPA on a folder. 

## Installation

```shell
$ pip3 install pokie-mullet
```

## Basic Usage

Show usage parameters:
```shell
$ mullet --help
```

Proxy a local Flask or Pokie API application from *main.py* and a development SPA application running on http://localhost:3000:
```shell
$ mullet
```

Proxy a local Flask or Pokie API application and a development SPA application locally installed on *../dist*:
```shell
$ mullet -fe ../dist/
```

Proxy a local Flask or Pokie API application on "/slug"  and a development SPA application running on http://localhost:3000:
```shell
$ mullet --slug "/slug"
```

## Static Serving

If a local folder is specified for frontend serving, mullet will always serve contents, even if the required resource 
doesn't exist. The behaviour is as follows:
- empty or non-existing routes are served as /index.html (or other index file name you may have specified);
- existing files are served as files (mimetypes is used to attempt to identify the correct mime type);
- existing directories are served as /index.html (or other index file name you may have specified);
