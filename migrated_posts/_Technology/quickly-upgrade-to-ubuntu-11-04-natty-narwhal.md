---
title: 'Quickly upgrade to Ubuntu 11.04 Natty Narwhal'
date: Sat, 30 Apr 2011 22:31:35 +0000
draft: false
tags: [How-To, Linux, Technology, Tips, Ubuntu]
---

[![Ubuntu logo](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg)In case you missed it, the latest edition of Ubuntu was released this week, Natty Narwhal (or 11.04 if you prefer). It seems to have been one of the most popular releases ever, because _I can't connect to the Ubuntu website to upgrade!!!_ What's happening is that because Canonical's servers are so busy, the upgrade assistant can't download the release notes for the new version. And so the upgrade fails.

Enter Bittorrent
----------------

Because Canonical make their [ISO files available as torrents](http://www.ubuntu.com/download/ubuntu/alternative-download#bt), you can download the latest version of Ubuntu without relying on their creaking servers! Good old Bittorrent! **A word of caution**: download the _alternate_ version of the ISO, not the standard desktop edition. That's the file named _ubuntu-11.04-alternate-i386.iso.torrent_ for people like me on an Intel architecture.

Upgrade Ubuntu directly from ISO
--------------------------------

Why bother burning a CD-ROM when you can [upgrade Ubuntu directly](https://help.ubuntu.com/community/NattyUpgrades) from the ISO image?

    sudo mkdir -p /media/cdrom
    sudo mount -o loop ~/Desktop/ubuntu-11.04-alternate-i386.iso /media/cdrom

And from there, you simply run the following command to get the upgrade process running:

    gksu "sh /media/cdrom/cdromupgrade"

Another word of caution: the installer will prompt you to download newer versions of files from the Internet. Well, if you want to do this upgrade quickly, you don't want to add the lag time from downloading all those files. Say no, and deal with updating later.

Et voila!
---------

That's your lot - a quick and easy way to upgrade your Ubuntu to Natty Narwhal without relying on Canonical servers. Judging by how hard they've been hit this time round, I'm guessing I'm not the only one busting to try out the new Unity interface - hopefully this'll be a sexy new feature that'll attract some curious new users to try Linux!