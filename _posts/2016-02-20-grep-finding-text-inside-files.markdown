---
author: wejick
comments: true
date: 2016-02-20 01:27:17+00:00
layout: post
link: http://blog.ggiovani.com/grep-finding-text-inside-files/
slug: grep-finding-text-inside-files
title: Grep finding text inside files
wordpress_id: 68
categories:
- Linux
tags:
- file
- grep
- oneliner
---

Need to find text inside files in your directory? This grep trick would be useful.

Basic :

```sh
$grep -rnw [directory here] -e [pattern here]
```

Example :

```sh   
$grep -rnw ./Documents -e coolThings
```

Filtering based on filename extension :

```sh
$grep --include=*.[extension] -rnw [directory here] -e [pattern here]
```

excluding :

```sh 
$grep --exclude=*.[extension] -rnw [directory here] -e [pattern here]
```

Those scripts will run recursively through entire directories inside specified directory, use --exclude-dir to exclude some of them
