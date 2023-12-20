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
