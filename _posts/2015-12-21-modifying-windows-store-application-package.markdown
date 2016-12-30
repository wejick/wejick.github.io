---
author: wejick
comments: true
date: 2015-12-21 11:43:28+00:00
layout: post
link: http://blog.ggiovani.com/modifying-windows-store-application-package/
slug: modifying-windows-store-application-package
title: 'Windows Store Application : Modifying Package'
wordpress_id: 9
categories:
- Programming
tags:
- package
- programming
- windows
- WUP
---

Sometimes we need to modify our Windows Store application package without taking a long time rebuilding the project, I hope this note helps you to do it.

Let’s say we have application named SmartPak and we forgot to include configuration file when building the app. What we will do is extracting the SmartPak.appx, copy the configuration file into it then package it again.



# Repackaging Windows Store Application Package



However we couldn’t do it using traditional archive manager like 7zip or winzip, Microsoft provides tool to handle this case and it already included in Windows SDK since 8.1.

So currently we have this directory structure :

[![file list ggiovani.com](https://wejick.files.wordpress.com/2015/10/gbr1.jpg?w=630)](https://wejick.files.wordpress.com/2015/10/gbr1.jpg)

Now open your visual studio tools command prompt, you could find it here (the path may different):
`_C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\Tools\Shortcuts\_`
Pick any command prompt you want since packaging is noarch operation, this time I use “_Developer Command Prompt for VS2013_“.

[![windows store application developer tool ggiovani.com](https://wejick.files.wordpress.com/2015/10/gbr2.jpg?w=300&h=114)](https://wejick.files.wordpress.com/2015/10/gbr2.jpg)

Let’s extract the appx, run this command :

`MakeAppx unpack /p SmartPak.appx /d output_directory`

If we don’t manage localization very well, this command may end up with error; At that case use /l switch to ignore localization checking.

Now we have new directory named output_directory, do any modification we need to that directory.

After making modification now we want to repack it again, run this command :

`MakeAppx pack /d output_directory /p SmartPak.appx`

Then we have new SmartPak.appx which includes our modification

However at this step we couldn’t use this package, we have to sign it again since the file is modified. To do it we need to copy our certificate to working directory (to make the process easier). If you’re not sure which one is certificate key, find file with .pfx extension.

At this step we have SmartPack.pfx copied to working directory. Now run this command to sign our new appx :

`SignTool sign /a /v /fd SHA256 /f SmartPak.pfx SmartPak.appx`


Now your package is ready to use !!!

That one is not for bundle package, which has appxupload extension. To handle this we could also use MakeAppx with bundle and unbundle option.

I hope this will help you

Cheers
