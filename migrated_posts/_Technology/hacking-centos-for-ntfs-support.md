---
title: 'Hacking CentOS For NTFS Support'
date: Tue, 13 May 2008 22:11:24 +0000
draft: false
tags: [CentOS, Linux, NTFS, Technology]
---

In deciding between various Linux distributions, a friend recently recommended that I look at [CentOS](http://www.centos.org). I duly tested it out for a bit on an old machine then decided to have a play on one of my regular PCs, setting it up to dual-boot with Windows XP. **Update: 19 September 2013**: The Linux NTFS project seems to have been discontinued, so I've removed the broken links that were on this page previously. Strongly recommend you check out [NTFS 3G for mounting partitions](https://wiki.archlinux.org/index.php/NTFS-3G) under Linux. Things were going fine until I needed to access my Windows XP partitions which were formatted with NTFS. Apparently due to concerns over licensing and the legally of tapping into the NTFS format, the CentOS developers (or more likely [Red Hat](http://www.redhat.com)) have decided not to build NTFS support in by default. As with everything Linux, _there is a way_ to work around this. And here it is.

The Linux-NTFS Project
----------------------

A post in the [CentOS Forums](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=2603) pointed me to the [Linux-NTFS project](http://www.linux-ntfs.org/) website. This is a project dedicated to enabling reliable, full-featured access to NTFS filesystems from Linux. Just what we need! First off, I’m using the current release of CentOS Linux, version 4.2. Apparently, this requires the same download as RedHat Enterprise 4. Now, before you start downloading stuff, run this quick test to determine your kernel version:

uname -r

You should get `2.6.9-22.EL` as your result. If so, download the corrseponding NTFS RPM from the download page. There’s a convoluted Linux-y way to install the RPM file from the command line, but I just double-clicked to install. Haven’t noticed any disturbing side-effects so far…. Anyway, just execute the RPM and it’ll trigger the installation routine. Follow the prompts to the end.

Verifying The Install
---------------------

The instructions ask us to verify the install before proceeding, so run the command below:

/sbin/modprobe ntfs

If you get errors, you’re got problems. If it all completes silently, run `cat /proc/filesystems` and check the output for NTFS. If you see NTFS - good - time to mount the drive!

Mounting Your NTFS Volume
-------------------------

Right, before you mount, you have to create a directory in Linux as your **Mount Point**. This will be the entry point to the NTFS volume, which you’d previously accessed through `C:` or `D:`. To create the mount point:

mkdir /mnt/windows

Then you link the NTFS volume to the mount you just created:

mount /dev/hda1 /mnt/windows -t ntfs -r -o umask=0222

The mount command you just executed will give you access to the drive for your current session. If you want your NTFS drives to _always_ be mounted, then you need to add some entries to the fstab in Linux. You can get more instructions on this from the Linux-NTFS website.