---
title: "Patching GNU Screen with vertical split support in OS X"
description: "The built-in `screen` only support horizontal split, in order by make it support vertical split, we need a patch."
layout: post
tags: osx, screen
category: tech
comments: yes
---


##Patching GNU Screen with vertical split support in OS X

The built-in `screen` only support horizontal split, in order by make it support vertical split, we need a patch.

Here are the commands:

```
cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/sources/screen co screen
curl http://old.evanmeagher.net/files/gnu-screen-vertsplit.patch > gnu-screen-vertsplit.patch
cd screen/src
patch < ../../gnu-screen-vertsplit.patch
./configure --enable-locale --enable-telnet --enable-colors256 --enable-rxct_osc
make
sudo make install 
```

And also put them into [Gist](https://gist.githubusercontent.com/yang6n/0bad5bfe58854b737abc/raw/9931c08d7fff4d88012a23ff0e5a33f07661a902/screen_vertical_split.sh)

You can simply execute the following command to finish this:

```
curl https://gist.githubusercontent.com/yang6n/0bad5bfe58854b737abc/raw/\
9931c08d7fff4d88012a23ff0e5a33f07661a902/screen_vertical_split.sh | sudo sh
```
