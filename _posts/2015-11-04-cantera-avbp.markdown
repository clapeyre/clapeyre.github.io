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

```
brew install homebrew/science/cantera
```

This will tap the homebrew/science tap into your brew install directory, and
install the cantera formula.

## The CERFACS fork

A fork of Cantera is developed at [CERFACS](http://cerfacs.fr/cantera), which
includes the most recent developments in reduced chemical schemes and other
recent features not included in the official repository.  It can be downloaded
from the CERFACS website and compiled manually of course, but why bother?  As I
recently discovered, the Homebrew tap system can directly search any
[GitHub](https://github.com/) repository for formula.  The result:

```
brew install --without-check clapeyre/cantera-avbp/cantera-avbp
```

As you can see, I have also added the `--without-check` option, because for now
the testing stages do not suite work.  Hopefully this will be resolved soon.
What I'm not sure about yet is if you can make both the official and the custom
fork live well together.

### Edit :

The `--without-check` thing is resolved. This formula can now be installed
simply via:

```
brew install clapeyre/cantera-avbp/cantera-avbp
```

Several comments on what was done to make it work:

* Using the patch system of homebrew, where a git diff can be added to change a
  file, several SConscript files are modified so gfortran can be found.
* An issue with the detection of numpy version is resolved in
  site_scons/buildutils.py. It was based on string lexicographic order, which
  is broken since numpy version 1.10. Now based on integer order.
* An argument pointing to the gfortran library directory is passed to `scons`
  when building to find the gfortran library. It writes:

  ```
  gfortran_lib_dir=#{Formula.factory('gcc').opt_prefix}/lib/gcc/5
  ```

  This is a strange way to define the library path, but the directory
  architecture of the gcc libraries are odd. I'm surprised by the `5`, which
  indicates that this might break if one day gcc switches to a version 6.

