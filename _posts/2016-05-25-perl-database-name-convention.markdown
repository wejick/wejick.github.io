---
author: wejick
comments: true
date: 2016-05-25 00:41:16+00:00
layout: post
link: http://blog.ggiovani.com/perl-database-name-convention/
slug: perl-database-name-convention
title: Perl database terms name convention
wordpress_id: 96
categories:
- Programming
tags:
- database
- perl
---

## Perl database terms convention



For my own reference

```perl  
$dsn    Database source name
$dbh    Database handle object
$sth    Statement handle object
$hAny   of the handle types above ($dbh, $sth, or $drh)
$rc     General Return Code  (boolean: true=ok, false=error)
$rv     General Return Value (typically an integer)
@ary    List of values returned from the database.
$rows   Number of rows processed (if available, else -1)
$fh     A filehandle
undef   NULL values are represented by undefined values in Perl
\%attr  Reference to a hash of attribute values passed to methods
```