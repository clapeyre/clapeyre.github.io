---
layout: post
title: "Compelling Python APIs"
categories: python
post_url: beautiful_python_apis
---

## Python: an explosively popular language

In the fast-paced world of programming languages, Python is not
a newcomer. Since its first release in 1991, its popularity has gradually
increased, but according to the [TIOBE
index](https://www.tiobe.com/tiobe-index/python/) it wasn't until 2004
that it reached true fame, when it rapidly became the 5th most used
programming language overall.
[Stackoverflow](https://insights.stackoverflow.com/trends?tags=python%2Cjavascript%2Cjava%2Cc%23%2Cphp%2Cc%2B%2B&utm_source=so-owned&utm_medium=blog&utm_campaign=gen-blog&utm_content=blog-link&utm_term=incredible-growth-python)
popularity measures show a clear trend in more recent years: since 2012,
questions asked about Python have increased steadily, growing from 6th to
second place in the number of questions asked, and now only topped by
Javascript.

<img src="/data/Stackoverflow_popularity.png" width="500" align="center" style="border:30px solid transparent">

On [GitHub](http://githut.info/), Python is now only topped by Java and
Javascript in terms of active repositories, and CSS is added to that list
in total number of pushes. One could argue that Javascript and CSS are
heavily biased, since *e.g* a Python server like Django will have both
generated and stored in it, even though developers would consider it
a Python project.

In depth analysis of the recent growth of Python supports the claim that
it is the [fastest-growing major programming
language](https://stackoverflow.blog/2017/09/06/incredible-growth-python/)
today.


## Python packages

Part of the popularity of python comes from its "batteries included"
philosophy: the standard installation contains useful tools that enable to
start usual tasks with some level of support. However, a dedicated server
called [PyPI](https://pypi.org/) and maintained by the [Python Software
Foundation](https://www.python.org/psf/) hosts other packages built by the
community. To this date, there are currently over 120,000 packages listed
on PyPI. The "[Wall of Superpowers](https://python3wos.appspot.com/)"
lists the most downloaded ones. Ignoring those concerning specific
wrappers for a technology (*e.g* AWS), some of the notable ones are:

  - requests: "HTTP for Humans"
  - Jinja2, Flask, Django, Werkzeug, gunicorn: mostly web technologies
  - python-dateutil, pytz: date manipulation
  - nose, pytest, coverage, coveralls, pytest-cov, mock: unit testing
  - numpy, scipy, matplotlib, pandas: scientific software
  - pep8, flake8, pylint: code linting and quality metrics
  - SQLAlchemy: database interaction
  - etc...


## Python APIs

A common trait in many of the documentations of these packages is that it
starts with a simple example of what you can do with it, with a strong emphasis
on how easily it is achieved. Often, an example of the same code written with
the standard library is included, and it is much longer and more convoluted.

Check out these three simple examples taken directly from the docs: Flask,
requests and pytest. See if you get a sense of what they do, even if you
have no clue how they work.

### Flask

``` python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"
```

Yes, at this point you actually have a full web server running at
localhost/, that says `Hello World`.

### requests

```python
import requests

r = requests.get('https://api.github.com', auth=('user', 'pass'))

print r.status_code
print r.headers['content-type']
```

You have just talked to an API over HTTP with a single line.

### pytest

Say you have the following function:

```python
def inc(x):
    return x + 1
```

then the matching unit test writes:

```python
def test_answer():
    assert inc(3) == 5
```

Of course, this test fails.

## What does it change?

>   Really, that's **it**?

I cannot say how many times I have heard (or said myself) this incredulous
sentence in recent years. While this is of course achievable with other
languages, the python community is centered on open-source, and has built
its momentum by attracting users, not through coercion. This has forced
Python APIs to be compelling. There is a necessary "wow" factor. At first
glance, curious programmers must think: *This looks so easy. I need to try
it out*.

Python star and hyperactive [Kenneth Reitz](kennethreitz.com) puts it in
layman's terms when describing his projects as "*for humans*". He is the
author of the `requests` package featured above, subtitled "*HTTP for
humans*". This package is number 4 (!) on the Wall of Superpowers, with
100 Million downloads. That's more than `pip`!

Personally I believe that this follows a more general trend about the
simplification of user experience (or UX). UX has been shoved forward very
fast thanks to web and mobile apps, where user retention is largely based
on product "lovability". With the "UX" keyword, much talk can be found
such as *e.g.* [a recent post by Wayne
Chang](https://hackernoon.com/the-quintessential-guide-for-building-an-unforgettable-first-time-user-experience-19720a7447d2)
where he states:

>   A new user is extremely impatient. They don’t trust you yet. They
>   don’t know what to expect, and they’re trying to decide (as quickly as
>   possible) if you’re going to make their life easier, faster, and more
>   efficient, or slower, more annoying, and boring.

While this is said of a web/mobile app, I believe the developer is no
different, and has a trove of libraries at his disposal. If a library is
to retain his attention, every step of the journey has to be crafted to
make it "*lovable*" - from first contact to full blown usage.

## What to look for

I'll attempt here to summarize the very subjective list of important
points that seem common between popular Python APIs:

  - **Intuitive start**. You look at a simple example, and you already know
  what it does. There is no need to refer to a documentation or
  specification at this stage. This is at the heart of the Python
  philosophy, right there in the zen of python:

    > Explicit is better than implicit

  - **Excellent documentation**. The docs must be easy to find, available
  online, searchable, and contain concrete examples to start building an
  app that leverages the library. Again this stems from the open-source
  nature of the Python community, where users are spread out and cannot
  have access to "experts" on a given library easily.

  - **Pythonic**. This is very hard to define simply, but there is a general
  philosophy in Python which becomes recognizable when one reads good
  code. Some libraries intentionally force you to write code that is
  "non-pythonic", mostly by defining strict ways in which they must be
  used. This gets on the nerves of pythonistas very fast. A great example
  that I see often is the use of getters and setters for attributes that
  do not need them.

  - **Nothing to hide**. A common discussion point in Python concerns
  "private" variables, which don't exist apart from a naming convention.
  This is because of an approach sometimes referred to as the "We're all
  adults here" principle. Popular APIs do not hide their inner workings.
  `numpy` helps you abstract the memory used for your vectors, but gives
  you full access to it if you want. Pandas wraps data in a useful
  structure, but can spit out the raw data at any point. The idea is not
  to *hide* something that the user shouldn't see. Rather, it is to build
  layers of abstractions, so that the user can aim for the one best suited
  for his needs.

## Final thoughts

So, whether you go library hunting, or you want to write the next big
library at the top of the Wall of Superpowers, remember that a great
library should offer great functionality but not get in the user's way,
whatever his field of application.
