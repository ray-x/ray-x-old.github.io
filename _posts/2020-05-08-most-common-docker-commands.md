---
layout: post
title: "Useful docker commands"
subtitle: 'practical docker'
author: "Ray"
header-style: text
tags:
  - Docker

---

Some most used docker commands.
On ubuntu, if docker install with snap, add /snap/bin/ to PATH

Most docker command should have two levels. But for comparability reason commands can be both top level command and command with sub commands.

e.g.

`docker pull nginx` should be `docker` _`image`_ `pull nginx` in latest docker versions.  I will use `docker [image] pull` to indicate the command can either be `docker image pull` or `docker pull`

### Docker image vs container
From article [How to Automate Docker Deployments](http://paislee.io/how-to-automate-docker-deployments/)
An image is an inert, immutable, file that's essentially a snapshot of a container. Images are created with the *build* command, and they'll produce a container when started with *run*. 

### Useful commands

|Command  	    | Command description	| Command example  	|
| ------------- |-------------        |-----------|
|`docker version`|  version number 	||
|`docker info`| docker info (build, file system etc)  	||
|`docker search`| Search a image by name	|search nginx image `docker search nginx`|
|`docker [image] pull`| Pull a image by name	|pull nginx image `docker image pull nginx` or to specific a version `docker image pull nginx:stable-alpine` or `docker image pull nginx:1.16.1-alpine`|
|`docker [image] ls`| list downloaded images	||

### Docker cheat sheet

A good summary [Docker Cheet Sheet](https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf) 

### Base command

from latest cmd line reference [Docker(base command)](https://docs.docker.com/engine/reference/commandline/docker/) 



