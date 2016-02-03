---
layout: post
title: Autofs Weirdness Fixed
date: 2015-10-11
author: Joachim van de Haterd
category: Technical thoughts
tags: [Linux]
---
I just (hopefully) solved an annoying problem with autofs and thought I would share it with the world and save someone a few hours of debugging.

I love autofs. It is an automounter for Linux that can be used for virtually anything that needs mounting (in terms of file systems that is). Currently, it is at version 5.X. However, recently, I was not able no see any of my NFS mounts. Neither my NAS nor my Pi appeared to work. 

A quick `showmount -e <server>` taught me that both my NAS and my Pi were up and running and NFS was working like a charm on both servers. I started double checking any settings. It appears that there were some compatibility problems with earlier autofs versions, but there were no new package maintainer versions to merge with my settings. Even so, my settings were exactly the same as on the [Arch Wiki](http://wiki.archlinux.org/index.php/Autofs) and it had worked very well for a long time.

Next stop: manually run `automount`. No errors. No mounts either. The logs did not show anything either.

Okay, so I probably fucked up some settings. I uninstalled autofs, made sure that the `/etc/autofs` subdirectory was deleted and reinstalled autofs. I checked the wiki again and used the vanilla settings that had always worked. Again, the only result was a huge void where my NFS mounts used to be. For arch linux, this is normally `/net`. 

In the past, I once had to create subdirectories for my servers manually. I tried that as well. No dice. With autofs off, the subdirectories were there (but obviously empty). With the service on, the subdirectories were missing or invisible. Now that was a clue. In earlier versions, there used to be an option called ghosting that would create the subdirectories for you even if the mounts were not available. What if the `/net` subdirectory was the culprit? Again, I stopped the autofs service, I removed the `/net` directory and started the service again. It worked!

TL:DR? If autofs suddenly stops mounting without any hints in the logs, try turning off the service, remove the directories in which your mounts normally reside, and start the service again.
