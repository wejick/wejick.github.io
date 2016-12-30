---
author: wejick
comments: true
date: 2016-04-07 05:00:36+00:00
layout: post
link: http://blog.ggiovani.com/actually-extern-c/
slug: actually-extern-c
title: What actually extern "C" does?
wordpress_id: 78
categories:
- Programming
tags:
- c++
- name mangling
---

Most C++ programmers know that they need to use extern "C" when declaring function, so it can be accessible from C. However this becomes a magic mantra for many developers, what does this thing do actually?

Short answer :
It tells C++ compiler "No name mangling for this function", so C linker could understand.

A little bit longer answer
C++ use name mangling to enable function overloading, but C doesn't have function overloading so no need for name mangling.

So what is name mangling ?

We have this function :

```c
int plus(int,int);
```

C++ compiler may produce this in object file :

```c  
aabbcc(int,int);
```

C compiler would produce this in object file :

```c   
plus(int,int);
```

Imagine we provide that function via header file to C code, when linking the linker will find for plus(int,int) from C++ object code. However plus(int,int) isn't there, because it becomes aabbcc(int,int).

Declaring it as extern "C" will suppress name mangling for this function, so it will produce C style naming.

```c    
extern "C"
{
    int plus(int,int);
}
```

I hope it's easy to understand
