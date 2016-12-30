---
author: wejick
comments: true
date: 2016-02-14 02:24:39+00:00
layout: post
link: http://blog.ggiovani.com/setup-vagrant-python-mongodb-dev-environment-frugal-way/
slug: setup-vagrant-python-mongodb-dev-environment-frugal-way
title: Setup vagrant python mongodb dev environment [Frugal way]
wordpress_id: 61
categories:
- Linux
tags:
- mongodb
- python
- uwsgi
---

Recently I was in need of having python development environment for simple http API. Honestly this area is something I don't have good understanding, so this article may contains many impractical way to do or to look things.

## Setup vagrant :

My machine is basically Ubuntu 15:10 and you can threat it just like normal Debian box.

  1. Install vagrant and virtualbox
   ```sh
$sudo apt-get install vagrant virtualbox
   ```

  2. Create directory for the box
   ```sh
$mkdir vgbox
$cd vgbox
   ```

  3. Create new virtual machine box based on ubuntu 14.04
   ```sh
$vagrant init hashicorp/trusty64
$vagrant up --provider virtualbox
   ```
   It will download the box about 450Mbs

  4. At this part basically we have ubuntu 14.04 runs and ready for anything we want
   ```sh 
$vagrant ssh
   ```

## Setup python mongodb :

Unfortunately there would be no running example in this article, since I have no good understanding yet in how everything working together (will find a way to write in other post).

  1. Install pip, mongodb and python header
   ```sh
$sudo apt-get install build-essential python-pip python-dev mongodb
   ```

  2. Setup some dependencies
   ```sh
$sudo pip install virtualenv cython
   ```

  3. Create virtual environtment
   ```sh
$virtualenv firstApp
$cd firstApp
$source bin/activate
   ```

  4. Install python modules
   ```sh  
$pip install mongoengine six python-mimeparse uwsgi
   ```

Now we have everything setup in our box
