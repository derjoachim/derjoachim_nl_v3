---
layout: post
title: Another reason to hate Exchange server
joomla_id: 22
joomla_url: exchange-just-refuses-
date: 2011-05-17 12:57:50.000000000 +02:00
author: Joachim van de Haterd
category: Technical thoughts
tags: [Microsoft]
---
Here's one from the trenches of IT support. Today's source of frustration is Microsoft Exchange 2003.

Yesterday I received a call from a customer. Because a number of outlets were to be replaced, two servers would have to be shut down and powered on again. No problem. This office has two servers: a domain controller and a mail server. Both run Windows 2003. The mail server runs Exchange.

When the electricians were done, I reconnected the servers and booted them. After some time, both servers were happily up and running. Or were they? The employees complained that they could not contact the mail server. Strange. It appeared to be working normally. A quick look to the logs revealed that it could find no domain controller. Restarting exchange solved the problem.

d'Oh! The office is too small for a backup domain controller, and for some reason, Exchange needs one. However, how difficult is it to connect to the DC when it finally gets up? This is one of the many many things that make me hate Microsoft environments.

Lesson learned: when rebooting all servers simultaneously, make sure that the domain controller is the first to be back up. Either that, or just don't use Exchange. I'd settle for the second option.
