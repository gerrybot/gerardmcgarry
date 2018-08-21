---
title: 'Command line tip: How to restart Mac OS X networking'
date: Mon, 06 Jan 2014 11:19:35 +0000
draft: false
tags: [Apple, OS X, Terminal, Tips]
---

[![Apple Logo](http://interwebworld.co.uk/wp-content/uploads/2014/01/apple-logo-300x224.jpg)](http://gerard.files.wordpress.com/2014/01/apple-logo.jpg)If you're a terminal warrior like me, you'll occasionally need to reboot the OS X network interface. There's a quick way to do this through the command line - but first you need to know the identity of your network interface. Run the ifconfig command in your terminal and find the interface with an IP address attached to it. On my MacBook Pro, the ethernet interface is en0 while the wireless interface is en1.  Yours may be similar.

Shutting down the network interface
-----------------------------------

Now that you've identified the interface, shutting it down and restarting it is a breeze. Run this command: `sudo ifconfig en0 down` And to start things back up again... `sudo ifconfig en0 up` That's it. It's a simple command that's worth remembering - or bookmarking!