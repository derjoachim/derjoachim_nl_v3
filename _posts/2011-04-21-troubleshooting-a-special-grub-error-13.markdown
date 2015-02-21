---
layout: post
title: Troubleshooting a special GRUB Error 13
joomla_id: 19
joomla_url: troubleshooting-a-special-grub-error-13
date: 2011-04-21 15:33:25.000000000 +02:00
author: Joachim van de Haterd
category: Technical thoughts
tags: [Linux]
---
A few days ago I got my first kernel update for my netbook in 7 months. However, it did not boot anymore. Here's what I did to fix it.

I own an EEEPC, one of the earliest generations. A few months ago, I converted from Ext2 to Ext4 file partitions. This was probably the underlying problem, so I am explicitly mentioning it here.

When I installed Arch Linux, I was advised to install a special kernel maintained by somebody who called himself Toofishes. Kudos to the man. However, he quit somewhere in August. I was just considering switching back to the vanilla kernel (or making my own), but yesterday, i suddenly saw that a new kernel had been built! Yay!

After updating, I rebooted and got the dreaded GRUB error 13.

```
	root hd0,0
	File system type is ext2fs, partition type 0x83
	Error 13:  Invalid or unsupported executable format
```

My fallback kernels (which I never use), gave me the same error.

Before panicking, I googled the dreaded error 13 and I was not too suprised to find many results. All I needed, was a boot disk, and a healthy dose of command line magic. After booting the boot disk, I needed to use the following:

First I needed to mount the partitions on the HDD.

```
	# mkdir /mnt/arch
	# mount -t ext4 /dev/sda1 /mnt/arch
	# mount -t proc proc /mnt/arch/proc
	# mount -t sysfs sys /mnt/arch/sys
	# mount -o bind /dev /mnt/arch/dev
```

The second step was a chroot. After all, we want grub to choose the right file system.

```
	# chroot /mnt/arch /bin/bash
```

The (theoretically) final step is to rerun grub-install. The --recheck option makes sure that the disks are properly probed.

```
	# grub-install --recheck /dev/sda
```

In my case, I got a nasty error:

```
	/dev/root not found or not a block device
```

This one did not pop up in the standard documentation. So either the documentation is lacking, or my case was a special one. I am going for the second option. Let's take a look at the line before the error 13 line:

```
	File system type is ext2fs, partition type 0x83
```

Since my partitions have long been moved to Ext4, I suspected that this should be the culprit. So, back to the search engine again.

A quick search yielded the following command:

```
	# grep -v rootfs /proc/mounts &gt; /etc/mtab
```

Either, I had to edit mtab when converting my Ext2 partitions to Ext4 and forgot, or my mtab was broken in some other way. However, the grub-install worked this time and my laptop boots fine now.

## Acknowledgment

For troubleshooting this issue, I used the following two pages.

 * [https://wiki.archlinux.org/index.php/Create_an_Ext4_Partition#GRUB_Error_13](https://wiki.archlinux.org/index.php/Create_an_Ext4_Partition#GRUB_Error_13)
 * [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)
