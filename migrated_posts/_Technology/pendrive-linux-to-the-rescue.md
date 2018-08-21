---
title: 'Pendrive Linux to the rescue!'
date: Sat, 27 Feb 2010 12:44:50 +0000
draft: false
tags: [Linux, Open Source, Technology, Troubleshooting]
---

Since most laptop and desktop computers these days can boot from a USB drive, one of the handiest utilities in my toolbox is an installation of [Pendrive Linux](http://www.pendrivelinux.com/). Pendrive Linux gives you a bootable, fully-working linux system on a USB stick. I use a 2GB ByteStor flash drive personally, with the default install of the Pendrive Linux system. From what I've read, you can go as far as to install larger systems like [Ubuntu](http://www.ubuntu.com/) on a flash drive, but I've stuck to this slightly more compact system (more out of laziness, to be honest).

Portable Operating System
-------------------------

One of the supposed uses of this type of system is portability - you can use it on virtually any hardware, bringing your full linux system and favourite settings with you anywhere. It's an alluring notion - as someone who jumps between several different systems on a daily basis, having all your settings ready to go is a massive timesaver. However, I've used thumb drive Linux for other purposes...

Data recovery and hardware testing
----------------------------------

I can't count the number of times someone's come to me with a faulty Windows box, either with a failing hard drive or crippled with other problems - viruses, messed up operating system, etc. If you can boot a machine to a version of Linux (OK, you _could_ use a live CD installation, but you can't save settings to a CD!), you can mount Windows hard drives and copy data elsewhere. OK, for large data, you'll also need to hook up a larger USB hard drive to copy the data to.

1.  Boot to USB Linux system and connect a secondary USB drive to store the data on
2.  Mount the Windows hard disks
3.  Locate the data you need to recover and copy it to the larger hard USB hard drive
4.  You may get the odd error, but this mostly works for me.

### Hardware troubleshooting

I had a machine in for repair this week - Windows Vista, but wouldn't connect to the internet through wired or wireless interfaces, even though the computer could 'see' the available wireless networks. The error log in Vista was no use - it claimed that it "couldn't contact the DHCP server". So, I ran the machine with the Pendrive Linux operating system instead, and it connected to the internet instantly. OK, that proved that the networking hardware was actually fine - pointing me to a software issue instead. (For the sake of completeness, it was an expired and possibly corrupted version of Norton 360 blocking the network interfaces!) Remember though, NTFS access is pretty important if you're planning to restore data from more modern Windows XP and Vista systems.

Inventive Uses
--------------

Now, I can't personally vouch for these usages of thumb drive Linux installs, but they're possible and also pretty cool. If you use virtualisation solutions like [VirtualBox](http://www.virtualbox.org/), you can boot a virtual machine to a USB Linux install, meaning you can take that portability and troubleshooting toolkit to an entirely new level.

Thumb Drive Feature Comparison
------------------------------

The ever-wonderful LifeHacker website has a great - if slightly old - [run-down of Thumb Drive systems](http://lifehacker.com/5069054/battle-of-the-thumb-drive-linux-systems) that you can download and run for free. Did I mention that they're free? That's pretty important - the only thing you need to spend cash on is a USB thumb drive, and you probably have a handful of them lying around the house already! Now, considering that my own install is a couple of years old, I'm going to experiment and see if I can upgrade my USB stick to a more modern version of Linux, preferably Ubuntu. One thing to bear in mind is that if you're planning to use this on older hardware, a lighter operating system like [Damn Small Linux](http://www.damnsmalllinux.org/) might be better, especially if the machine doesn't have much RAM to work with. That's one last idea for you - if you have an old computer lying around that you want to breathe new life into, test it against a light version of Linux. You might find that a machine that was increasingly slow under Windows is actually pretty fast under Linux - and _voila_, you've [extended the life of your PC](http://gerard.interwebworld.co.uk/2009/the-onward-march-of-technology-and-open-source-software/ "The Onward March Of Technology (and Open Source software)")!