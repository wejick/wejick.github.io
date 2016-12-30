---
author: wejick
comments: true
date: 2016-03-04 15:30:02+00:00
layout: post
link: http://blog.ggiovani.com/faux-variadic-on-visual-c-11-visual-studio-2012-2/
slug: faux-variadic-on-visual-c-11-visual-studio-2012-2
title: Faux Variadic On Visual C 11 (Visual Studio 2012)
wordpress_id: 71
categories:
- Programming
tags:
- c++
- visual studio
- visual studio 2012
---

Yes yes yes

That’s the answer if you ask me whether I have personal problem with VC 11 (Visual Studio 2012).

Another problem which I found interesting is how variadic list was implemented in VC11, they called in [Faux Variadic](http://blogs.msdn.com/b/vcblog/archive/2011/09/12/10209291.aspx). In short this feature is not yet fully supported, or you could say it works via workaround. However this workaround have some side effects, the one most affects me is the number of maximum argument was reduced to reduce compiler memory consumption.

Normally we would have function with variadic list  handles 6 even 10 argument, however you couldn’t do it on VC 11 by default. In order to allow this scenario you have to define _VARIADIC_MAX, the default number is 5. This surely comes with side effects, compiler would eat more memory than before.
