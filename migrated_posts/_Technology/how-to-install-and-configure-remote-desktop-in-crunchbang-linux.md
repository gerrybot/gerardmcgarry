---
title: 'How to install and configure remote desktop in Crunchbang Linux'
date: Fri, 21 Oct 2011 11:23:08 +0000
draft: false
tags: [Crunchbang, Linux, Remote Desktop, Vino]
---

[![Tux, the Linux mascot](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot-300x222.jpg "Tux, the Linux mascot")](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot.jpg)I've been playing around with [Crunchbang Linux](http://crunchbanglinux.org/) for the last few days. I had a low spec old server lying around the house and wanted to see if it would perform better with a lightweight Linux distribution. The machine had been struggling under the latest Ubuntu 11.10, so I scrubbed it and installed Crunchbang. The problem being that the machine runs in the attic office and doesn't have a screen or keyboard, so remote access is essential. But Crunchbang doesn't seem to come with a default remote desktop server, so we have to install one for ourselves.

Vino to the rescue
------------------

Vino is [the default VNC server](https://help.ubuntu.com/community/VNC/Servers) that ships with Ubuntu and has done for a long time now. And because Crunchbang is a distant cousin of Ubuntu, I figured this would be a good place to start! Installing Vino, of course, is a complete breeze - let me walk you through the steps...

1.  Fire up the terminal! Type in `sudo apt-get install vino` and follow the instructions on screen.
2.  Once Vino's been installed, you need to configure it. To do this, open up a terminal window (Super-key + t) and type vino-preferences. Press return, and a familiar configuration screen should appear.
3.  You want to configure Vino to allow other users to view _and_ control the desktop.
4.  Under security, _untick_ the "You must confirm each access to this machine". You want the machine to automatically accept your incoming connections - otherwise, you'd have to manually approve each connection!
5.  We set a password to secure access to the machine, and allow the network to automatically accept incoming connections. Once you've set the options (I've included a handy screenshot below to guide you), your VNC server should be up and running.
6.  The last step is to go to another machine on the network and try to connect. You can use the built-in remote desktop utility in most Ubuntu distributions, or alternatively install TightVNC for Windows.

Vino recommended configuration screenshot
-----------------------------------------

\[caption id="attachment_121" align="alignnone" width="300" caption="Click on the image for full size version"\][![Vino preferences in Crunchbang](http://interwebworld.co.uk/wp-content/uploads/2011/10/crunchbang-vino-300x224.jpg "Vino preferences in Crunchbang")](http://interwebworld.co.uk/wp-content/uploads/2011/10/crunchbang-vino.jpg)\[/caption\] _Et voila_! Remote access to your screenless, keyboardless server!