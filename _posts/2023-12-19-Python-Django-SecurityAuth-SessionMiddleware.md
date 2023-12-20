---
layout: post
language: python
tags:
    - django
    - backend
    - python
---

# Login, session and cookie

## An \*HTTP cookie\* (web cookie, browser cookie) is a small piece of data that a server sends to a user\'s web browser. The browser may store the cookie and send it back to the same server with later requests. Typically, an HTTP cookie is used to tell if two requests come from the same browser---keeping a user logged in, for example. It remembers stateful information for the [stateless](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#http_is_stateless_but_not_sessionless) HTTP protocol.

## Cookies are mainly used for three purposes:

### Session management, e.g. Logins, shopping carts, game scores, or anything else the server should remember

### Personalization, e.g. User preferences, themes, and other settings

### Tracking. Recording and analyzing user behavior

## sessions are saved on the server side while cookies are saved on the client side.

# Cross Site Request Forgery protection

## The CSRF middleware and template tag provides easy-to-use protection against [Cross Site Request Forgeries](https://www.squarefree.com/securitytips/web-developers.html#CSRF). This type of attack occurs when a malicious website contains a link, a form button or some JavaScript that is intended to perform some action on your website, using the credentials of a logged-in user who visits the malicious site in their browser.

## `csrf_exempt(view)`

### This decorator marks a view as being exempt from the protection ensured by the middleware. Example:

``` python
from django.http import HttpResponse
from django.views.decorators.csrf import csrf_exempt
@csrf_exempt
def my_view(request):
    return HttpResponse("Hello world")
```

## `csrf_protect(view)` {#csrf_protectview collapsed="true"}

### Decorator that provides the protection of CsrfViewMiddleware to a view. Usages:
```python
    from django.shortcuts import render
    from django.views.decorators.csrf import csrf_protect
    @csrf_protect
    def my_view(request):
        return render(request, "a_template.html", {})
```


# Django Middleware

## Class with `process_request` Input middleware

### if process~request~ return anything, the request will not forward to view.py, it will return the result

### if nothing return, continue with next middleware and then go to view

## `proccess_response(self, request, response)` output middleware

# Auth middleware

## middleware/auth.py

``` python
from django.utils.deprecation import MiddlewareMixin
from django.shortcuts import HttpResponse, redirect


class AuthMiddleware(MiddlewareMixin):

    def process_request(self, request):

        # 0.排除不需要的页面 否则容易死循环【【【
        if request.path_info == "/login/":
            return

        # 1.读取当前访问的用户的session信息,如果能读到,说明已登录过,就可以继续向后走
        info_dict = request.session.get("info")
        if info_dict:
            return

        # 2.如果没有登录信息
        return redirect("/login/")

```

## setting.py

``` python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
    'employee_management.middleware.auth.AuthMiddleware',
]
```

## logout

### clean session data

### view.py

``` python
def logout(request):
    """ 注销 """
    # clean session
    request.session.clear()
    return redirect("/login/")
```

