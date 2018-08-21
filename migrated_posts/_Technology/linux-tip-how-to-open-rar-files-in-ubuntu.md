---
title: 'Linux tip: How to open RAR files in Ubuntu'
date: Fri, 04 Feb 2011 21:49:55 +0000
draft: false
tags: [How-To, Linux, Technology, Tips, Ubuntu]
---

[![Ubuntu logo](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg) It doesn't happen often, but once in a while you'll need to open a RAR file in Ubuntu. **What's a RAR file, you ask?** Well, essentially it's a slightly more obscure zip file format. Windows handles ZIP file formats nicely, Linux is comfortable with TAR.GZ archives. Neither operating system loves RAR files. **Solution - install unrar!** It really is that simple. Fire up a terminal session and type `sudo apt-get install unrar`. Now you've got the tools for the job, let's crack open that RAR file. Sticking with the terminal session, navigate to where your RAR file is stored (let's imagine it's called myrararchive.rar) and then type the following command:

    unrar x myrararchive.rar

...and your archive will be automagically extracted for you. You'll notice we used an "x" switch there - that's just to tell the programme to extract files. For more info on what unrar can do for you, simply type `man unrar` into a terminal window, or browse this guide to become a RAR ninja. You'd have to be a total masochist, of course, but hey-ho.