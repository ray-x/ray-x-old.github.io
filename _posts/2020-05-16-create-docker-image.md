---
layout: post
title: "Create a docker image"
subtitle: 'basic instruction'
author: "Ray"
header-style: text
tags:
  - Docker

---

Create a new image from a container's changes

* Usage:
  
  * Docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

e.g:
Get a busy box image and create a file inside container



```
docker run --name base1 -it busybox
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
d9cbbca60e5f: Pull complete 
Digest: sha256:836945da1f3afe2cfff376d379852bbb82e0237cb2925d53a13f53d6e8a8c48c
Status: Downloaded newer image for busybox:latest
/ #mkdir -p /data/html
vi index.html
<h1>Busybox httpd server. </h1>

```
In another terminal create a new image and check it
```
docker commit -p  -a "rayx1" -m "a base image with index.html" base1
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
<none>              <none>              64e381aeac90        55 seconds ago       1.22MB

```
you will see a un-named image. 
To tag a image use `docker tag`

```
Usage:  docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
```

e.g tag it to user rayx1 with name httpd-busybox and tag v0.1
```
docker tag 64e381aeac90 rayx1/httpd-busybox:v0.1
```
Also you could use multiple tags
```
docker tag rayx1/httpd-busybox:v0.1 rayx1/httpd:latest
```
You will see:
```
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
rayx1/httpd-busybox   v0.1                64e381aeac90        6 minutes ago       1.22MB
rayx1/httpd           latest              64e381aeac90        6 minutes ago       1.22MB
```
You could remove a tag with image rm

```
docker image rm rayx1/httpd
Untagged: rayx1/httpd:latest

```

You can change docker file fields

```
docker inspect base1

[
    {
        ...
        "Config": {
            ...
            "Cmd": [
                "sh"
            ],
            ...
        },
        
    }
]

```

Create a new image with Cmd start a httpd with version v0.2
```
docker commit -a "rayx1 <ray@myemail.com>" -c 'CMD ["/bin/httpd", "-f", "-h", "/data/html"]' -p base1 rayx1/httpd-busybox:v0.2
```
Run the new image
`docker run --name base2 rayx1/httpd-busybox:v0.2`
Use `docker inspect base2` get the ipaddress `"IPAddress": "172.17.0.3",`
and you can check the http with `lynx 172.17.0.3`

login into docker hub and push the image
`docker login -u rayx1`
`docker push rayx1/httpd-busybox `