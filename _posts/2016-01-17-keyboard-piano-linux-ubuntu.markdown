---
author: wejick
comments: true
date: 2016-01-17 09:53:52+00:00
layout: post
link: http://blog.ggiovani.com/keyboard-piano-linux-ubuntu/
slug: keyboard-piano-linux-ubuntu
title: Keyboard piano with linux Ubuntu
wordpress_id: 42
categories:
- Linux
tags:
- linux
- midi
- music
- piano
---

Playing piano on linux ubuntu is not trivial way to do, until now I couldn't find the easiest way to do it. Although the normal way is not difficult to use, it's not that easy and simple. With this guide I hope everybody can use linux for day to day need without so much hassle.

Basically to play piano or other instrument we need to things : Midi interface and synthesizer.

For Midi interface we will use vkeybd which will emulate hardware midi keyboard via normal keyboard or GUI mouse click. The other one is synthesizer, we will use timidity for MIDI to WAV conversion, it's not actual synthesizer like I said before but it will do.

## Installing Keyboard piano on linux Ubuntu

```sh
$sudo apt-get install vkeybd timidity
```

## Playing Time

  1. Run timidity daemon :

```sh
$timidity -iA -B2,8 -Os1l -s 44100
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 2048, period size 680 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3
This command will create interface to ALSA then create 2 1024 buffer on 16 bit 44100 hz
TImidity will print available active port to use, at our case is 129:0-3
```

  2. Run vkeybd :

```sh
$vkeybd --device alsa --addr 129:0
```

Have fun, now we can use normal keyboard as Midi keyboard interface.

I'm not really into music and actually I'm blind about note. I just in the middle on boredom and trying to learn how to read music sheet, this software help me to practice.
