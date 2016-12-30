---
author: wejick
comments: true
date: 2016-08-02 16:43:36+00:00
layout: post
link: http://blog.ggiovani.com/simple-perl-profiler/
slug: simple-perl-profiler
title: Simple perl profiler
wordpress_id: 114
categories:
- Programming
tags:
- perfiler
- perl
- profile
- profiling
---

In my two months working with perl there is one particular problem I face everyday, that is about measuring my code performance easily.



## I call it Perfiler

Last Friday I took a day off and worked on interesting tool to do simple profiling in perl. It is very simple, it is not collecting callstack information to measure how much time a scope take to be finished. I have to specify which scope to measure, but it is pretty fast because it doesn't collect any runtime information except scope timing, this way I can minimize profiling bias. However I don't think this is thread safe.

Without further a do, you can check this Github repository :

[github.com/wejick/perfiler](https://github.com/wejick/perfiler)

What makes it pretty cool is it's able to produce simple json and svg timeline. The svg output is based on systemd analize plot.

![perfiler wejick](https://raw.githubusercontent.com/wejick/perfiler/master/svgoutput.png)
