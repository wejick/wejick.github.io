---
author: wejick
comments: true
date: 2015-12-21 09:46:39+00:00
layout: post
link: http://blog.ggiovani.com/compiling-cocos2dx-in-ubuntu-linux/
slug: compiling-cocos2dx-in-ubuntu-linux
title: Cocos2DX Compiling in Ubuntu Linux
wordpress_id: 4
categories:
- Programming
tags:
- cocos2d
- cocos2dx
- cpp
- linux
- programming
---


Cocos2DX is one of most popular game engine in the world and it supports almost all popular platform available. I have plan to build a game based on this engine, just for have fun and fill my empty days. Here is how we can compile cocos on Ubuntu Linux.
    
# Compiling Cocos2DX in ubuntu linux
Download cocos from [http://cocos2d-x.org](http://cocos2d-x.org)

    
# Prepare dependencies :
```
_libx11-dev_
_libxmu-dev_
_libglu1-mesa-dev_
_libgl2ps-dev_
_libxi-dev_
_g++-4.9_
_libzip-dev_
_libpng12-dev_
_libcurl4-gnutls-dev_
_libfontconfig1-dev_
_libsqlite3-dev_
_libglew-dev_
_libssl-dev_
_glfw3 _
```
# Go to /build directory inside cocos package
run :

```sh
$sudo ./install-deps-linux.sh
```

# Create makefile

```sh
$mkdir lxbuild
$cd lxbuild
$cmake ../
```

# compile
```sh
$make
```

Now you can check lxbuild directory for some compiled library.
