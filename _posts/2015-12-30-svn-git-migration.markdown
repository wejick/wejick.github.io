---
author: wejick
comments: true
date: 2015-12-30 10:42:40+00:00
layout: post
link: http://blog.ggiovani.com/svn-git-migration/
slug: svn-git-migration
title: SVN Git Migration
wordpress_id: 27
categories:
- Programming
tags:
- git
- programming
- svn
---

SVN Git migration is always interesting topic to talk about, and there are a lot of article discuss it. SVN is old hero which finds its dawn, since git offers more flexible and preferable development flow. Many entities are actively using SVN with no plan to migrate, and many others are evaluating.

# SVN GIT Migration : don't worry it's easy

Migrating the source code itself is a piece of cake, however migrating the history and the workflow are another matter. I summed up there are 3 big step to migrate SVN to GIT :
    
  1. Preparing the environment
  2. Converting
  3. Sharing

To help migrating we will use [https://github.com/nirvdrum/svn2git](https://github.com/nirvdrum/svn2git) and while trying to stick with git standard tools.

## Preparing Environment

What need to do before converting the repository is getting list of the users, later we will need it to adding user information to git. Git has different user information than svn, beside username git also has user email. Other thing to note is do it on case-sensitive environment, like using linux.

After installing svn2git, run this :

```sh    
$svn2git http://svn.example.com/path/to/repo --authors ~/authors.txt`
```

keep authors.txt for next step

### Converting

Now let's clone your svn repository to git, it takes time so do it overnight :

```sh
$git svn clone --stdlayout --authors-file=authors.txt http://url/to/svn/repository dest_dir-tmp
```

Now you have git local repository, with the same branches as your svn including 'trunk' branch.

To keep your git repository synchronized before it active, we could use this command.

```sh    
$git svn fetch
```

Lets cleaning up our new git local repository, first step - delete trunk branch since we have master on git :

```sh    
$git branch -d -r trunk
```

### Sharing

Now we are ready to create git server, refer to [this article](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server) to setup your server.

Source :

http://www.karpach.com/subversion-to-git-migration.htm

https://www.atlassian.com/git/tutorials/migrating-overview/
