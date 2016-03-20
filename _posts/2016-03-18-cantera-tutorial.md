---
layout: post
title:  "Cantera (AVBP fork) easy install on Mac using homebrew"
date:   2016-03-18 14:40:00
categories: cantera avbp homebrew
post_url: cantera_tutorial
---

# Installation instructions for Cantera on a Mac

## The Cantera software
[Cantera](http://www.cantera.org/) is a powerful suite of software for chemical
kinetics.  It is now fairly easy to install on a Mac thanks to the 
[Homebrew](http://brew.sh/) package manager.  Once homebrew is installed,
Cantera can simply be installed using:

    brew install homebrew/science/cantera

This will tap the homebrew/science tap into your brew install directory, and 
install the cantera formula.

## The CERFACS fork
A fork of Cantera is developed at [CERFACS](http://cerfacs.fr/cantera), which
includes the most recent developments in reduced chemical schemes and other
recent features not included in the official repository.  It can be downloaded
from the CERFACS website and compiled manually of course, but why bother?  The
Homebrew tap system can directly search any [GitHub](https://github.com/)
repository for formula.  The result:

    brew install clapeyre/cantera-avbp/cantera-avbp

## Switching between official and AVBP Cantera distributions
In some cases it can be practical to have both distributions installed. But
since the AVBP branch is named exactly like the official one, Homebrew cannot
tell them apart. They must be linked 'one at a time'. An easy way to switch
from one to the other is to use Homebrew to unlink one and link the other:

    brew unlink cantera; brew link cantera_avbp

## Updating with brew
The Cantera version distributed by cerfacs is a flavor of Cantera V 2.1.1. This
never changes, so Homebrew cannot know that it is supposed to update its
version. If you wish to update your version, you must *reinstall* Cantera. _But
that *still* isn't enough!_ Because Homebrew caches its downloads, it will
simply untar the last tarball you downloaded and not update it. You must
manually delete it, than you can reinstall:

    rm /Library/Caches/Homebrew/cantera-avbp-211.tar.gz
    brew reinstall cantera-avbp

## How was this formula made?
For more info in this subject, go to [Cantera Mac details](cantera_details).
