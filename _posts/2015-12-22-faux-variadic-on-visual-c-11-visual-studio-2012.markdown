---
author: wejick
comments: true
date: 2015-12-22 11:44:51+00:00
layout: post
link: http://blog.ggiovani.com/faux-variadic-on-visual-c-11-visual-studio-2012/
slug: faux-variadic-on-visual-c-11-visual-studio-2012
title: Visual Studio 2012's Faux Variadic
wordpress_id: 11
categories:
- Programming
tags:
- c++
- microsoft
- visual studio
- windows phone
---

Yes yes yes. That’s the answer if you ask me whether I have personal problem with VC 11 (Visual Studio 2012).



## Why visual studio did it ?

Another problem which I found interesting is how variadic list was implemented in VC11, they called in [Faux Variadic](http://blogs.msdn.com/b/vcblog/archive/2011/09/12/10209291.aspx). In short this feature is not yet fully supported, or you could say it works via workaround. However this workaround have some side effects, the one most affects me is the number of maximum argument was reduced. They did it to reduce compiler memory consumption.

Normally we would have function with variadic list  handles 6 even 10 argument, but you couldn’t do it on VC 11 by default. In order to allow this scenario you have to define _VARIADIC_MAX, the default value is 5. This comes with side effects, compiler would eat more memory than before.
