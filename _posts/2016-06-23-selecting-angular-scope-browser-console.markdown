---
author: wejick
comments: true
date: 2016-06-23 10:58:58+00:00
layout: post
link: http://blog.ggiovani.com/selecting-angular-scope-browser-console/
slug: selecting-angular-scope-browser-console
title: Selecting angular scope from browser console
wordpress_id: 102
categories:
- Programming
tags:
- angular
- chrome
- javascript
- web
- webkit
---

In webkit browser $0 is element selected from element inspector in devtools. With this knowledge I can select angular scope easily with this method :

```javascript    
angular.element($0).scope()
```