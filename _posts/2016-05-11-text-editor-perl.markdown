---
author: wejick
comments: true
date: 2016-05-11 13:02:50+00:00
layout: post
link: http://blog.ggiovani.com/text-editor-perl/
slug: text-editor-perl
title: Text editor for perl
wordpress_id: 89
categories:
- Linux
- Windows
tags:
- perl
---

The best thing to do when learning new language is finding the common best practice for everything, this is including text editor to use. There are some popular text editor around Perl community, here is the (not complete) list :

  1. Padre
     It's more like IDE, however seems outdated

  2. VIM
    
     Everybody love vim, but not me

  3. Atom

     Popular, modern, open source and have a lot of plugin

  4. Komodo Edit / IDE
    
     I'm afraid with vendor lock in, so I didn't dare to try it even though it's recommended by many people.

  5. Notepad++
    
     Really familiar with this one, sadly it is only for windows

So at the end of the day I choose to use Atom with these package :
    
  1. terminal-plus : to open console
  2. linter-perl : perl linter based on B::Linter
  3. language-perl-template-toolkit : perl template toolkit support for atom


There are some gotcha when setuping the development environment :
    
  1. I choose to use Activestate Perl (AP) distribution, B::Linter doesn't compile in AP 5.22x . So I use the older one 5.2.0
  2. When you are behind corporate proxy it is better to setup cnltm then set http_proxy value to cntlm
  3. When using AP as much as possible use ppm instead of cpan to add package
