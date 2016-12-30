---
author: wejick
comments: true
date: 2016-07-18 06:56:29+00:00
layout: post
link: http://blog.ggiovani.com/size-referenced-array-perl/
slug: size-referenced-array-perl
title: Size of referenced array in perl
wordpress_id: 107
categories:
- Programming
tags:
- array
- context
- perl
- reference
- scalar
---

I have $this refer to an array, so how I can know the size of the referenced array?

```perl
scalar @{$this}
```

it will dereference the reference to then use scalar context, so we can get the size of the referenced array
