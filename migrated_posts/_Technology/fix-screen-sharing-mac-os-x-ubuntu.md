---
title: 'Fix Screen Sharing between Mac OS X and Ubuntu'
date: Sun, 23 Nov 2014 21:39:34 +0000
draft: false
tags: [Linux, MacBook Pro, Remote Desktop, Ubuntu]
---

A little while back, Ubuntu made a subtle change that broke Desktop Sharing to Mac computers. I keep a headless server upstairs to serve media files across my network, so screen sharing is essential to manage the server. However, when Ubuntu made their change - requiring encryption on the VNC connection - Macs lost the ability to connect. When attempting to connect to the Ubuntu server, your Mac will fail with the following error message:

> Connection failed to “\[User's\] remote desktop on \[Hostname\]”. The software on the remote computer appears to be incompatible with this version of Screen Sharing.

Fortunately, there's a quick fix for this on the Ubuntu side (also works on alternative Ubuntu-based distros like Mint). Follow the steps below to disable encryption on your Remote Desktop connections. First up though, here's my Mint Desktop Sharing config screen - it's set up to allow connections on the local network with a password required for access. [![Desktop Sharing prefs](http://gerard.files.wordpress.com/2014/11/desktop-sharing-prefs.jpg)](http://gerard.files.wordpress.com/2014/11/desktop-sharing-prefs.jpg)

1.  Install the dconf-tools by opening the Terminal and typing 'sudo apt-get install dconf-tools'
2.  When that's complete, open the newly installed dconf Editor
3.  Expand 'org'
4.  Expand 'gnome'
5.  Expand 'Desktop'
6.  Select 'Remote Access'
7.  Uncheck 'Require Encrption'(don't click on Set to Default as it rechecks it)
8.  Exit dconf-Editor

Here's a quick screenshot showing how your dconf screen should look: [![Dconf Settings](http://gerard.files.wordpress.com/2014/11/dconf-settings.jpg)](http://gerard.files.wordpress.com/2014/11/dconf-settings.jpg) I was able to immediately connect to the server from my MacBook after making this tweak. However, if this doesn't resolve the problem for you, try a reboot of your Ubuntu/Linux Mint machine.