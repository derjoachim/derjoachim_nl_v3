---
layout: post
title: How to ruin a Friday afternoon lunch break
joomla_id: 26
joomla_url: how-to-ruin-a-friday-afternoon-lunch-break
date: 2011-07-01 19:38:11.000000000 +02:00
author: Joachim van de Haterd
category: Technical thoughts
tags: [Linux]
---
The combination of an old Plesk version with piss-poor support, a non-backwards compatible database daemon and a bad default option coupled with a poorly executed package update ruined my Friday afternoon. Watch out, kids! Here's another horror story from the ugly world of system administration. For a change, I will dive into something from the *nix world that tries to make my life miserable.

A little background story: I am trying to set up a Magento web shop for a client of mine. Her hosting provider claims to support Magento, albeit with a few hacks. They made us a nice VPS with CentOS and Plesk. Although I am way too familiar with Plesk, this made me a happy camper. For a change, a server migration would be in an environment I happen to be familiar with.

My colleague who is still young and eager to learn, agreed to help me set up Magento within the plesk environment. Since I had duties at another customer, I was happy to give him the reins.

The Plesk version supplied to us, was 9.X, which is old. Therefore, it only ran PHP 5.1 . Magento needs 5.2+, but the help desk of the hosting provider already had that taken care of. In their wiki, they had a guide on how to upgrade PHP.

After some time, my intrepid young colleague sent me a message which ran something like 'uh oh, this is going wrong'. His powers of observation were at their best. The Plesk admin prompt would not show up. Instead, there was this dreaded little message that said: database connection failed. Ouch!

I opened an SSH session, and saw that Apache was running happily. Good. Of course we already knew. After all, it was Apache that told us that MySQL was not running properly. I found the mysql log and it had a cryptic message about not recognizing the usebdb option.

In my lunch break I opened up a Google screen, and entered 'plesk' and the exact error message into the search box. The first three hits were from the plesk forums. They were the exact same problem, mostly after a routine update. These questions were never answered by any Plesk representatives.  Well here's why I love Plesk. Thanks guys for your good support for which we pay dearly. I owe you one. Probably with a crowbar. Gordon Freeman style.

Anyhoo, the `--usebdb` option was still my only clue. Maybe it wasn't Plesk after all. The first hit was the bull's eye. At the time that Plesk 9 was the current version, mysql was updated from 5.0 to 5.1 . The `--usebdb` option was obsoleted. No biggie. However, the my.cnf config file was not updated by the CentOS guys accordingly, and the mysql daemon would not start. This was quickly fixed. Just comment out the `--usebdb` in `my.cnf` and start the daemon.

Well, this was a waste of time that either me and my colleague could have spent better. For instance, I could have taken the time to eat lunch. I wish that (A) this question would have been answered in the Plesk forums, (B) mysql would have given a warning, but happily ignore obsolete options and (C) CentOS would al least have supplied a working `my.cnf` .
