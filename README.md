# ubuntu-python
This repository provides some Dockerfiles to make python images which are built on Ubuntu.

## Motivation
The [official python images](https://hub.docker.com/_/python/) on the [Docker hub](https://hub.docker.com/) is based on Debian ([debian:stretch](https://github.com/docker-library/buildpack-deps/blob/master/stretch/curl/Dockerfile#L1)).
But there are needs to use source-built python images base on the Ubuntu for some reasons.

## Usage
You can replace your base image in your Dockerfile from python official(debian based) to this.

from:
```
FROM python:3.7                         # Debian "stretch" based
```
to:
```
FROM ubuntu-python:xenial-3.7           # Ubuntu "xenial" based; Build required
```
or
```
FROM grf53/ubuntu-python:xenial-3.7     # Ubuntu "xenial" based; Pull from Docker Hub
```

## How to build
Dockerfile for your target Ubuntu & Python version is under `[project dir]/[codename]/[pyversion]/` .
There are also slim version Dockerfiles under `[project dir]/[codename]/[pyversion]/slim/` .

Recommended tag name: `ubuntu-python:[codename]-[pyversion]`
> codename: Ubuntu version abbreviated codename e.g.) trusty, xenial, bionic, etc.

> pyversion: Python version formatted as 'major'.'minor' e.g) 2.7, 3.7, etc.

### Build Command

```shell
$ docker build -t ubuntu-python:[codename]-[pyversion] -f [project dir]/[codename]/[pyversion]/Dockerfile .
```
### Examples
```shell
# 1) Building python3.5 on Ubuntu 16.04 Xenial Xerus
$ docker build -t ubuntu-python:xenial-3.5 -f xenial/3.5/Dockerfile .

# 2) Building python3.6 on Ubuntu 18.04 Bionic Beaver (not supported)
$ docker build -t ubuntu-python:bionic-3.6 -f bionic/3.6/Dockerfile .

# 3) Building python3.7 on Ubuntu 16.04 Xenial slim version
$ docker build -t ubuntu-python:xenial-3.6-slim -f xenial/3.7/slim/Dockerfile .
```
## References
* [docker-library/python](https://github.com/docker-library/python)
* [docker-library/buildpack-deps](https://github.com/docker-library/buildpack-deps)
    * [/stretch](https://github.com/docker-library/buildpack-deps/tree/master/stretch)
    * [/xenial](https://github.com/docker-library/buildpack-deps/tree/master/xenial)
* [python - Docker Official Images](https://hub.docker.com/_/python)
* [ubuntu - Docker Official Images](https://hub.docker.com/_/ubuntu)
* [debian - Docker Official Images](https://hub.docker.com/_/debian)