---
title: Choosing a New Blogging Platform
author: Joachim van de Haterd
layout: post
category: "Technical thoughts"
tags: [CMS, Joomla, Jekyll]
description: The road to a new blogging platform.
---
Earlier this week, I wrote a slightly harsh [post](http://derjoachim.nl/blog/2015/02/10/joomla-is-the-emacs-of-cmss/) on why I stopped using Joomla for my personal blog. I still feel bad about it, even as a vim user. Emacs does not deserve that. Whereas the previous post was about my reasons for leaving Joomla, this post is about my choice for a new blogging platform.

### Alternatives

I started looking for alternatives. The most popular choice is a bad one. In terms of maintainability and security, Wordpress is utterly horrible and I would not advise it to anybody. End users love it, which is kinda putting the ‘[Word](https://office.live.com/start/default.aspx)’ in Wordpress. Its code is reminiscent of the PHP4 days and really needs refactoring. I was looking into [Ghost](http://getghost.org/) or [Feathe.rs](http://feathe.rs/), but I did not like the idea of my writings being saved elsewhere and feathe.rs has been in beta for years now. I even could have installed Joomla 3 with the [Moyoweb CCK](http://moyoweb.nl/en/blog/2014-01-17/content-management-on-steroids.html), since I am one of the developers. To be honest, that option was alluring, but I chose differently.

### Static HTML

I recently wrote a [guest blog](http://www.nooku.org/blog/2014/11/on-philosophy-architecture-ants/) on the [Nooku](http://nooku.org/) blog. This is basically a static HTML site. I loved it. All I had to do, is fork their website on Github, put my post in a separate branch and enter a pull request when my post was done. The best thing was: all I needed to do, is write a post in Markdown, so I could use my favorite text editor. In the background, the entire website was 'compiled' into static HTML. What a perfectly elegant solution for a problem I did not know I had. I needed that too! The name of this particular blogging platform is [Jekyll](http://jekyllrb.com), which is based on Ruby, but if you prefer PHP, there are several options too. I like [this one](http://getgrav.org).

### Templating

Initially, making a template looked slightly challenging. The Liquid templating engine is not too well documented. Stackoverflow was a godsend; all the undocumented features I needed, were explained thoroughly. With the right Sass framework, a few hours and a bit of elbow grease, I got further than I ever got with Bootstrap. IMHO, this website never looked better, and its codebase is quite efficient.

### Import

Importing the data was easy, almost ridiculously so. There is a [Jekyll importer](http://import.jekyllrb.com/docs/home/), which is installable as a Ruby gem. Sadly, it did not support Joomla 3. However, a few hours and a crash course in Ruby later, I wrote my own Joomla 3 import script. [It's on Github](https://github.com/derjoachim/jekyll-import/blob/joomla3-import/lib/jekyll-import/importers/joomla3.rb), so feel free to use it. As of this writing, the pull request is still pending, so use it at your own risk.

### Ease

Jekyll is ridiculously easy to use for anyone who is a programmer or hacker worth their salt. Creating a Jekyll site initially takes some effort, but once one gets the hang of it, it is very easy to maintain. The content workflow makes sense for everyone who ever worked with git. It integrates flawlessly with Github pages if you like and if you don't, no worries. Any ftp or ssh client with rsync will do. 
