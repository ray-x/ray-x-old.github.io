---
layout: post
title: "Dockerfile"
subtitle: 'Build your own docker'
author: "Ray"
header-style: text
tags:
  - Docker

---
We can use 
* storage volume
* `docker exec`, 
* ansible (and similer software) 
* `docker run` with options, 
* container based on container
* etc
 
to build a customized a docker. But with dockerfile it is easy to build a customized docker.


## Share system variable
As discussed early, we can use a infrastructure container to share system variable to other container. (e.g use consul)
and generate configure file based on system variable. e.g. a nginx file in /etc/nginx/conf.d/
```
# server.config

{
  server_name $MY_NGX_SERVER_NAME;
  listen $NGX_IP:$NGX_PORT;
  root $WEB_ROOT;
}
```

## Dockerfile
* Source code for building Docker images. It contains all the comnands to assemble a image
* Use docker build to access dockerfile

### Dockerfile format
  * `# Comment`
  * INSTRUCTION arguments
    * Instruction is **NOT** casesensitive, but it is a convention to use UPPERCASE to distinguish them from arguments more easily
  * Docker runs instructions in a Dockerfile in order
  * The first instruction must be `FROM` in order to specify the Base Docker Image from which your are building.

### Docker ignore file  .dockerignore 
Same as .gitignore

### Environment variable and replacement
* env variable (declared with **ENV** statement) can also be used in instructions as variables to be interpreted by Dockerfile
* Env variable are notated in Dockerfile with $variable_name or ${variable_name}
* ${variable_name} support bash modifiers
  * ${var:-word} if var is set, return var value, otherwise return word
  * ${var:+word} if var is set, return word value, otherwise return empty

### Dockerfile instructions
* From 
  * Need to be first un-comment statement.
  * Base image can be either local image or docker registry (e.g docker hub)
  * Syntax (either)
    * FROM <repository>[:<tag>] (repository is image name e.g nginx, redis, or ray-x/busybox-httpd)
    * FROM <repository>@<digest-hash> 
e.g.
```Dockerfile
FROM busybox:latest
```


*  MAINTAINER (depreacted)
  e.g `MAINTAINER "rayxu <rayx@rayx.me>"`

* LABELS
  * Usage: `LABEL <key>=<value> [<key>=<value> ...]`
  * The LABEL instruction adds metadata to an image in format of key=value e.g  `MAINTAINER="rayxu <rayx@rayx.me>"`

### COPY
  * Syntax:
    *  COPY <src> [<src> ...] <dest>
    *  COPY ["<src>", ... "<dest>"]
  * Copies new files or directories from <src> and adds them to the filesystem of the image at the path <dest>.
  * <src> may contain wildcards and matching will be done using Go’s filepath.Match rules.
  * <dest> is an absolute path, or a path relative to WORKDIR.
  * If <dest> doesn’t exist, it is created along with all missing directories in its path.
  * If space existed in <src> use "<src>" e.g. "my src folder"

