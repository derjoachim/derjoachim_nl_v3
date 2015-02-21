---
layout: post
title: Starting Nooku programming, some pitfalls
joomla_id: 31
joomla_url: starting-nooku-programming-some-pitfalls
date: 2011-09-02 18:20:58.000000000 +02:00
author: Joachim van de Haterd
category: Technical thoughts
tags: [Programming, Nooku, Web development]
---
I've recently started developing web applications in [Nooku](http://www.nooku.org) framework. It is an awesome new framework, but daunting for newbees like yours truly. For one, development goes so fast, that the Nooku community can't keep up with documentation. Fortunately, the [community](http://groups.google.com/group/nooku-framework?lnk=) is friendly and helpful.

## Framework versus server

Before beginning my ramblings, I'd like to make a distinction between the Nooku Framework and Nooku server. The former is the framework that complements all Joomla versions since 1.5, whereas the latter entirely replaces Joomla. Server and framework are being developed in parallel.

Furthermore, it should be noted that Nooku is a RAD framework. It has a lot of 'magical' components. It does a lot of things automatically. This is both a tremendous advantage and a huge disadvantage. A lot of common tasks work out of the box, but in the beginning, you will not realize that these functions are already there, and finding out will make you feel like an idiot. :-)

## RTFM and contribute

Nooku Framework has its own [wiki](https://nooku.assembla.com/spaces/nooku-framework/wiki) and its own discussion group. The framework, currently bearing version number 0.7, was written by developers and for developers. The community are happy to help, but expect you to read and learn stuff yourself. And they are eager for any contributions. They are more than willing to share the framework, but expect your contributions in return. They may be in the form of code, documentation, or even a beer for the developers. Just don't be a parasite and give back.

One more thing, there is a nice showcase component for Nooku server. Its code is elegant and gives you a good overview of the capabilities of Nooku. Read the code and try to grok it. Furthermore, read the code in the /lib/koowa subdirectory.

## How to start your Nooku experience

There are already [several](https://nooku.assembla.com/spaces/nooku-framework/wiki/Installation) [Nooku](http://blog.bedre.no/nooku/tutorials/installing-nooku-framework-with-the-symlinker/) [Installation](http://israelcanasa.com/post/1119166074/installing-nooku) [Guides](https://nooku.assembla.com/spaces/nooku-framework/wiki/Installation), and I will not dive any further into this subject matter. However, I ran into a few problems that deserve a mention:

 * Make sure that your \*AMP stack is properly configured. Your php.ini file should contain the correct settings to actually display errors. Furthermore, some \*AMP stacks like MAMP use different versions of PHP. Make sure that you are working with the correct version.
 * Make sure that your PEAR version is the correct one. I switched \*AMP stacks and it took me quite some time to get PEAR running in a halfway decent way again. Without PEAR, running the symlinker script (see the wiki) will refuse to run. You can manually link everything, or bluntly copy the files into your project, but keeping up with recent revisions will be difficult.
 * Use a good subversion or git client. I prefer the CLI tools. YMMV.
 * Use a decent text editor. Eclipse and [Aptana](http://aptana.com/) are popular choices. I still prefer gvim for hard core text editing, but that's because I am an old dog. Aptana is an IDE based on Eclipse, specially tailored for web developers.

Good. You are set up and either have Nooku server running or a recent Joomla! version with the Nooku Framework.Now we start entering some code. First I will give you a few tips on configuring a standard Joomla 1.5 installation for Nooku usage:

 * Not Nooku-specific, but equally important: make sure that your debug settings are correct. Otherwise, you will not see any relevant error messages. That will make debugging very hard.
 * Sooner or later, you will have to work with Mootools, a Javascript OO framework, favored by the Nooku community. Make sure that you have enabled the [Mootools Upgrade plugin](http://docs.joomla.org/What_is_the_Mootools_1.2.4_upgrade_plugin). BTW: the Joomla framework appears to prefer JQuery. I am not going to enter into any religious debates. They are both good.


## Random coding tips

 * When creating a dispatcher that extends the standard dispatcher, be sure to call it with an echo. A dispatcher returns a lot of code. You won't see anything when you forget the echo.
 * Frontend development is tricky. Whatever your settings, any mistake will be punished with a white screen. At the time of writing, this is a known issue that needs solving (at least partially), but it has lower priority than other issues. One strategy is to develop in the backend first and migrate to the frontend later. Another one is to skip the frontend altogether.<

## A few general tips

 * Be sure to update frequently. Nooku (both server and framework) are in active development. However, be sure to test well before updating live applications.
 * Join the assembla site for Nooku. It is simply the best way to keep up with developments.
 * If you really like coding in Nooku, be sure to visit a code jam. You'll meet the people behind the community, and you'll learn a trick or two.

Happy coding.

## Disclaimer

I work for Moyo Web Architects, one of the forerunners in Nooku development in the Netherlands. Although I am a relative newbee in the Nooku world, I have been a web programmer for 9 years now.

### Final note

Today, I finished my first module, entirely written in Nooku. Again, I learned a few new tricks, and will be happy to share them on my site (or even the Nooku Framework wiki). Keep an eye on my blog.
