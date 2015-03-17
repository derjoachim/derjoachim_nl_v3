---
title: Grokking Vim Buffers
author: Joachim van de Haterd
layout: post
category: "Technical Thoughts"
tags: Vim
description: Grokking 
---
After many years of vim use, I finally grok buffers, or rather, I get why they
are still as widely used as they are. 

## Multiple Files

Anybody who is working any sizable projects, probably has several open files at
once. Within vim (and probably other editors as well, nothing new here), one
can achieve this in one or more of the ways described below.

1. Open several editor *windows*. Each file is opened in its own window. That's
convenient for the Alt+Tab users among us as long as the numbers of open files
is not too large. 
2. Open files in *tabs*. Each open file is opened within a tab and one can switch
files by selecting its tab. Again, with too many open files, it gets messy.
3. Use *buffers*. Each file is opened in the background, along with some metadata.
In command mode, one can switch files.

Please note that it makes sense to combine the strategies described above. For
instance, one can be working in several contexts or even projects
simultaneously. By opening files for a new context in a new window or tab, one
can group open files easily.

## Windows

The enumeration order above was conscious; I ordered them by level of perceived
difficulty. I have seen novice users who started by opening each file in its
own window. Back when there were no vim tabs, that's basically what I did. With
tabs coming along (or rather: me discovering them), I started grouping open
files in tabs. 

## Tabs

If you work with a manageable number of open files, tabs may be convenient. For
me, they have two disadvantages though: I often work on a small screen, so I
need all the pixels I can get, and I usually work with too many files for tabs
to be convenient. Apparently, the maximum number of open tabs is capped as well.

## Buffers

Buffers are the age-old alternative. Only barred by your computer's memory, you
can have as many buffers as you like. Navigation is quick and easy. The
shortcuts are quick and easy to remember. Even better: you can switch directly
to the proper buffer by entering a partial name. Tab-completion works fine and
if you get lost, you can easily list your open buffers.

For me, this proved to be a godsend. I have everything open in the background,
without losing any screen real estate. 


## Splits

A side note: it is worth exploring the option for splitting and assigning
buffers to these splits. If you are used to screen or tmux, this may look
familiar. I think that this may be worthy an entire new blog post.

## The Best?

As with everything else that is slightly rooted in reality, there is no
'best' way to deal with multiple files. I would urge vim users to explore the
possibilities of buffers though. They are way more powerful than they look and
solve problems you did not know you had.
