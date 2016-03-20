---
layout: post
title:  "Details of the Homebrew formula for Cantera's AVBP fork"
date:   2015-11-04 22:44:00
categories: cantera avbp homebrew
post_url: cantera_details
---

I decided that the easyest way to distribute Cantera_AVBP was by automating the
install process using Homebrew.

## What is in the formula?

Several things were needed to make it work:

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


## Initial status (Nov 4th, 2015)

As of november 2015, Cantera_AVBP could be installed with:

```
brew install --without-check clapeyre/cantera-avbp/cantera-avbp
```

The issues remaining were: 

-   that the checks could not be performed, hence the `--without-check` option
-   that the MD5 checksum had to be disabled, because CERFACS has a script
    which recreates the tarball every day, thus changing the timestamp and the
    sum even if no changes were made to the version

## Update (Nov 20th, 2015)

Nov 20th, 2015 : The `--without-check` thing is resolved. This formula can now
be installed simply via:

```
brew install clapeyre/cantera-avbp/cantera-avbp
```
