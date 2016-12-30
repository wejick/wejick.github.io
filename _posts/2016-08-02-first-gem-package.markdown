---
author: wejick
comments: true
date: 2016-08-02 11:37:08+00:00
layout: post
link: http://blog.ggiovani.com/first-gem-package/
slug: first-gem-package
title: Fluentd plugin is my first GEM package
wordpress_id: 111
categories:
- Programming
tags:
- fluentd
- gem
- log
- ruby
---

## Fluentd is interesting



![fluentd log wejick](http://logz.io/wp-content/uploads/2015/08/fluentd.png)

I am in the middle of a feature which need realtime monitoring and processing of log from http server. My fellow in Tokopedia suggested me to use fluend, actually this whole thing is his idea. So I started building the feature and then finding out that I need to write custom plugin for fluentd.

Actually this is not completely from scratch, but I just customized from existing plugin which is quite popular. So here it is my first published gem package.

[https://rubygems.org/gems/fluent-plugin-redis-store-wejick](https://rubygems.org/gems/fluent-plugin-redis-store-wejick)
