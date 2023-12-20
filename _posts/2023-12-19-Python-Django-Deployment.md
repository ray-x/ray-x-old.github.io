---
layout: post
author: "Ray"
header-style: text
tags:
  - python
  - django
  - CICD
---

# Normally there are following way to deploy python service

## ECS/EKS

## EC2

## EBS (elastic beanstalk)

## Lambda

# WSGI

## WSGI is the Web Server Gateway Interface. It is a specification that describes how a web server communicates with web applications

## why we need a gateway mediator

### flexiblity

1.  If you directly point your web server to your application, it
    reduces the flexibility\* \*of your application. Since your web
    server now directly points to your web application, you are unable
    to swap out web stack components.

    ::: {.DRAWER .drawer}
    let's say you've decided to deploy your application using Gunicorn,
    but several years later, you decide to switch from Gunicorn to
    mod~wsgi~. In this situation, you could easily switch to mod~wsgi~
    without making any changes in the application or framework because
    you used WSGI. WSGI provides flexibility to your application.
    :::

### scalability

1.  WSGI is capable of serving thousands of requests at a time. The WSGI
    server is responsible for handling the requests from the web server
    and making decisions for carrying out the communication of those
    requests to an application framework's process. we can divide the
    responsibilities among the servers for scaling web traffic.

## [How to use Django with Gunicorn](https://docs.djangoproject.com/en/4.2/howto/deployment/wsgi/gunicorn/)

## [How to use Django with uWSGI](https://docs.djangoproject.com/en/4.2/howto/deployment/wsgi/uwsgi/)

## [How to use Django with Apache and mod~wsgi~](https://docs.djangoproject.com/en/4.2/howto/deployment/wsgi/modwsgi/)

## [How to authenticate against Django's user database from Apache](https://docs.djangoproject.com/en/4.2/howto/deployment/wsgi/apache-auth/)

# ASGI

## ASGI (*Asynchronous Server Gateway Interface*)

## [How to use Django with Daphne](https://docs.djangoproject.com/en/4.2/howto/deployment/asgi/daphne/)

## [How to use Django with Hypercorn](https://docs.djangoproject.com/en/4.2/howto/deployment/asgi/hypercorn/)

## [How to use Django with Uvicorn](https://docs.djangoproject.com/en/4.2/howto/deployment/asgi/uvicorn/)

\*
