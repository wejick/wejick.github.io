---
author: wejick
comments: true
date: 2015-12-23 11:45:48+00:00
layout: post
link: http://blog.ggiovani.com/premake-4-short-introduction/
slug: premake-4-short-introduction
title: Premake 4 short introduction
wordpress_id: 13
categories:
- Programming
tags:
- gnu
- linux
- premake
- visual studio
- windows
---

## Having trouble maintaining cross platform project ? Premake is the answer



Having different build tools to maintain many platforms is troublesome, because naturally we need to sync manually. It can be even worse when we need to configuration of one platforms, sometimes it means we need to add new build configuration. With Premake that issue can be handled much easier, premake could generate project for almost all major available build tools :
    
  * Microsoft Visual Studio 2002-2010, including the [Express editions](http://www.microsoft.com/express)
  * GNU Make, including [Cygwin](http://www.cygwin.com/) and [MinGW](http://www.mingw.org/)
  * [Apple Xcode](http://developer.apple.com/tools/xcode/)
  * [Code::Blocks](http://www.codeblocks.org/)
  * [CodeLite](http://codelite.org/)
  * IC#Code [SharpDevelop](http://www.icsharpcode.net/OpenSource/SD/)
  * [MonoDevelop](http://www.monodevelop.com/Main_Page)

It even has cross compiling support, but it’s still experimental.

`With single project configuration, Premake will generate project for any platform you want`

## So how to use premake ?

I’m not good with premake, actually I never compose my own project using it. Premake is not much different from other meta build tools like cmake and [qmake](https://wejick.wordpress.com/2015/04/22/qmake-dont-forget-to-run-qmake-after-editing-qmake-file/), except it uses Lua as configuration language. This is not introduction to lua, check this [page](http://www.tutorialspoint.com/lua/index.htm) to learn more about lua.

In this article we will create simple solution, it's like creating project via wizard with normal IDE.

First create _premake4.lua,_ premake will use it as default configuration. Then create our solution by invoking solution function, anything after this function goes to solution scope.

```lua    
solution "myFirstSolution"
    configurations { "Debug", "Release" }
```

Look, I create _myFirstSolution_ with two configuration. A solution is nothing without project, right? Then we should create it.

```lua    
project "mainProject"
    language "C++"
    files { "**.h", "**.cpp" }
```
Above is our first project which include all .h and .cpp files from working directory. Then lets advance a little bit by specifying configuration for this project, we will add macro definition for each configuration.

```lua 
configuration "Debug"
    defines { "DEBUG" }

configuration "Release"
    defines { "NDEBUG" }
```

Ok this much is alright, now generate your project using premake [command](http://premake.sourceforge.net/what_is_premake).

```sh
$premake4 --target vs2013
```

This command will generate visual studio 2013 vsproj file.

## Ok, what was that?

In this state you may wonder what was that? Is _configuration_ a premake keyword, and what about _defines_?

If you familiar with lua, you may know that it allows calling function with one argument without parentheses. Before I mentioned that _configuration_ is just [normal lua function](https://github.com/premake/premake-4.x/wiki/configuration); but lua makes it looks like normal file configuration rather than mini programs.

Let’s meet again on part two :D
