---
layout: post
title:  "Cantera AVBP easy install on Mac using homebrew"
date:   2015-11-04 22:44:00
categories: cantera avbp homebrew
---

## The Cantera software

[Cantera](http://www.cantera.org/) is a powerful suite of software for chemical
kinetics.  It is now fairly easy to install on a Mac thanks to the
[Homebrew](http://brew.sh/) package manager.  Once homebrew is installed,
Cantera can simply be installed using:

{% highlight sh %}
brew install homebrew/science/cantera
{% endhighlight %}

This will tap the homebrew/science tap into your brew install directory, and
install the cantera formula.

## The CERFACS fork

A fork of Cantera is developed at [CERFACS](http://cerfacs.fr/cantera), which
includes the most recent developments in reduced chemical schemes and other
recent features not included in the official repository.  It can be downloaded
from the CERFACS website and compiled manually of course, but why bother?
As I recently discovered, the Homebrew tap system can directly search any
[GitHub](https://github.com/) repository for formula.  The result:

{% highlight sh %}
brew install --without-check clapeyre/cantera-avbp/cantera-avbp
{% endhighlight %}

As you can see, I have also added the `--without-check` option, because for now
the testing stages do not suite work.  Hopefully this will be resolved soon.
What I'm not sure about yet is if you can make both the official and the custom
fork live well together.

