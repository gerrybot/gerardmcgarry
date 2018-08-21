---
title: 'Configuring MP3 Support in Kubuntu Linux'
date: Tue, 13 May 2008 22:50:10 +0000
draft: false
tags: [At Work, Technology]
---

Just upgraded to the latest and greatest version of [Kubuntu Linux](http://www.kubuntu.org) yesterday, the Dapper Drake edition. Such a smooth upgrade path - just modify your `/etc/apt/sources.list` file, replacing every instance of `breezy` with `dapper` (back the file up first, of course), then you simply run the following commands:

    sudo aptitude update
    sudo aptitude dist-upgrade

I left mine to download and upgrade overnight and the next morning I had a fresh install of Kubuntu Dapper! Easy. And everything was intact from before - NTFS partitions mounted, FireFox on latest version, etc. Only one problem - my mp3s wouldn’t play in [amaroK](http://amarok.kde.org/). Since I spent a long time trawling the web for the solution, I’m going to make life easier for you and show you how to set up mp3 support in Kubuntu:

1.  You need to add the Multiverse repository to `/etc/apt/sources.list`. Add the line `deb http://nl.archive.ubuntu.com/ubuntu/ dapper multiverse`. Apparently you modify the `nl` part to the country you’re in, so mine was `gb`
2.  I think you have to do a quick update here, so from a console window run `sudo aptitude update`.
3.  When that’s done, run the command `sudo aptitude install libxine-extracodecs`. This will install your mp3 support.
4.  Run amaroK. You should probably restart the sound server with `killall artsd`, or reboot, but I found the mp3 support took effect straight away.

Anyway, I think that’s about right. Give it a go and see what happens, but remember to back stuff up, bless yourself (twice), and don’t blame me if it all goes wrong. I’m finding my way with this stuff too!