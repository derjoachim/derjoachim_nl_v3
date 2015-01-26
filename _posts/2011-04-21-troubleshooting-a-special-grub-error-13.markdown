---
layout: post
title: Troubleshooting a special GRUB Error 13
joomla_id: 19
joomla_url: troubleshooting-a-special-grub-error-13
date: 2011-04-21 15:33:25.000000000 +02:00
author: Joachim van de Haterd
excerpt: "<p>A few days ago I got my first kernel update for my netbook in 7 months.
  However, it did not boot anymore. Here's what I did to fix it.</p>"
category: Technical thoughts
---
<p>A few days ago I got my first kernel update for my netbook in 7 months. However, it did not boot anymore. Here's what I did to fix it.</p>

<p> </p>
<p>I own an &nbsp;EEEPC, one of the earliest generations. A few months ago, I converted from Ext2 to Ex4 file partitions. This was probably the underlying problem, so I am explicitly mentioning it here.</p>
<p>When I installed Arch Linux, I was advised to install a special kernel maintained by somebody who called himself Toofishes. Kudos to the man. However, he quit somewhere in August. I was just considering switching back to the vanilla kernel (or making my own), but yesterday, i suddenly saw that a new kernel had been built! Yay!</p>
<p>After updating, I rebooted and got the dreaded GRUB error 13.</p>
<pre><samp><code>root hd0,0</code></samp><samp><code><br />File system type is ext2fs, partition type 0x83</code></samp><samp><code><br />Error 13:  Invalid or unsupported executable format</code> </samp>
</pre>
&nbsp;
<p>My fallback kernels (which I never use), gave me the same error.</p>
<p>Before panicking, I googled the dreaded error 13 and I was not too suprised to find many results. All I needed, was a boot disk, and a healthy dose of command line magic. After booting the boot disk, I needed to use the following :</p>
<p>First I needed to mount the partitions on the HDD.</p>
<pre># mkdir /mnt/arch<br /># mount -t ext4 /dev/sda1 /mnt/arch<br /># mount -t proc proc /mnt/arch/proc<br /># mount -t sysfs sys /mnt/arch/sys<br /># mount -o bind /dev /mnt/arch/dev</pre>
<p>The second step was a chroot. After all, we want grub to choose the right file system.</p>
<pre># chroot /mnt/arch /bin/bash</pre>
<p>The (theoretically) final step is to rerun grub-install. The --recheck option makes sure that the disks are properly probed.</p>
<pre># grub-install --recheck /dev/sda</pre>
<p>In my case, I got a nasty error:</p>
<pre>/dev/root not found or not a block device</pre>
<p>This one did not pop up in the standard documentation. So either the documentation is lacking, or my case was a special one. I am going for the second option. Let's take a look at the line before the error 13 line:</p>
<pre>&nbsp;File system type is ext2fs, partition type 0x83</pre>
<p>Since my partitions have long been moved to Ext4, I suspected that this should be the culprit. So, back to the search engine again.</p>
<p>A quick search yielded the following command:</p>
<pre># grep -v rootfs /proc/mounts &gt; /etc/mtab</pre>
<p>Either, I had to edit mtab when converting my Ext2 partitions to Ext4 and forgot, or my mtab was broken in some other way. However, the grub-install worked this time and my laptop boots fine now.</p>
<h2>Acknowledgement</h2>
<p>For troubleshooting this issue, I used the following two pages.</p>
<ul>
<li><a href="https://wiki.archlinux.org/index.php/Create_an_Ext4_Partition#GRUB_Error_13" target="_blank">https://wiki.archlinux.org/index.php/Create_an_Ext4_Partition#GRUB_Error_13</a></li>
<li><a href="http://www.gentoo.org/doc/en/grub-error-guide.xml" target="_blank">http://www.gentoo.org/doc/en/grub-error-guide.xml</a></li>
</ul>
