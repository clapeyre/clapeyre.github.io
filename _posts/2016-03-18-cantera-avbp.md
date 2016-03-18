---
layout: post
title:  "Cantera (AVBP fork) easy install on Mac using homebrew"
date:   2016-03-18 14:40:00
categories: cantera avbp homebrew
---

# Installation instructions for Cantera on a Mac

## The Cantera software

[Cantera](http://www.cantera.org/) is a powerful suite of software for chemical
kinetics.  It is now fairly easy to install on a Mac thanks to the 
[Homebrew](http://brew.sh/) package manager.  Once homebrew is installed,
Cantera can simply be installed using:

```
brew install homebrew/science/cantera
```

This will tap the homebrew/science tap into your brew install directory, and 
install the cantera formula.

## The CERFACS fork

A fork of Cantera is developed at [CERFACS](http://cerfacs.fr/cantera), which
includes the most recent developments in reduced chemical schemes and other
recent features not included in the official repository.  It can be downloaded
from the CERFACS website and compiled manually of course, but why bother?  The
Homebrew tap system can directly search any [GitHub](https://github.com/)
repository for formula.  The result:

```
brew install clapeyre/cantera-avbp/cantera-avbp
```

Several comments on what was done to make it work:

-   Using the patch system of homebrew, where a git diff can be added to change a
    file, several SConscript files are modified so gfortran can be found.
-   An issue with the detection of numpy version is resolved in
    site_scons/buildutils.py. It was based on string lexicographic order, which
    is broken since numpy version 1.10. Now based on integer order.
-   An argument pointing to the gfortran library directory is passed to `scons`
    when building to find the gfortran library. It writes:

        gfortran_lib_dir=#{Formula.factory('gcc').lib}/gcc/5

    This is a strange way to define the library path, but the directory
    architecture of the gcc libraries are odd. I'm surprised by the `5`, which
    indicates that this might break if one day gcc switches to a version 6.

## Updating with brew

The Cantera version distributed by cerfacs is a flavor of Cantera V 2.1.1. This
never changes, so Homebrew cannot know that it is supposed to update its
version. If you wish to update your version, you must *reinstall* Cantera. _But
that *still* isn't enough!_ Because Homebrew caches its downloads, it will
simply untar the last tarball you downloaded and not update it. You must
manually delete it, than you can reinstall:

    rm /Library/Caches/Homebrew/cantera-avbp-211.tar.gz
    brew reinstall cantera-avbp

## More on the subject

For more info in this subject, go to [Cantera Mac details](http://clapeyre.github.io/cantera/avbp/homebrew/2015/11/04/cantera-avbp.html).
