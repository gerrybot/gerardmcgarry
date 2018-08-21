---
title: 'Configuring GRUB for the dual-boot Ubuntu/Windows XP environment'
date: Fri, 27 Feb 2009 22:28:50 +0000
draft: false
tags: [Linux, Technology, Ubuntu, Windows]
---

I briefly had a dual boot setup a few years ago. Booting between Linux (I can't remember which distro) and Windows XP was always clunky. Two problems normally come up:

*   With each subsequent kernel upgrade in Ubuntu, you get an extra two lines of boot options. Eventually, it becomes hard to find the Windows option, which is inevitably at the bottom of this endless list of kernel options.
*   When you're using Windows XP as the primary OS, you want _it_ to be the default Operating System rather than Ubuntu. Another possible option is having the computer automatically boot into the last used OS.

**A bit of history.** Back in the day, you had to manually edit the /boot/grub/menu.lst file. This was - as much old-school Linux was - archaic, confusing and _dangerous_. Who knows what you'd mess up by deleting an option or screwing something up. These days, configuring your GRUB is infinitely easier. Why? Well, like the **rdesktop** tool we talked about yesterday, there's a GUI interface to help you tweak GRUB to perfection.

Startup Manager
---------------

The utility is startup-manager. Of course, it's not installed by default, but with the swoosh of an apt-get, you can install it. Run this command: sudo apt-get install startupmanager And in a few moments, you'll be able to open Startup Manager from the **System** \> **Administration** menu. Let's take a look at the **Boot Options** tab: [![Ubuntu Startup Manager](http://gerard.interwebworld.co.uk/files/2009/02/startup-manager.jpg)](http://gerard.interwebworld.co.uk/files/2009/02/startup-manager.jpg) You can use this tab to enable or disable the bootloader timeout. Because I'm dual booting, I don't want to do this, but I _may_ decrease the amount of time to choose from 10 seconds to 5 seconds. The next option for **Default Operating System** is pretty cool. Not only can you choose your Windows partition as default in here, but you _can_ configure GRUB to start the last-used OS, which is convenient. The other options don't bother me that much. The **Security** tab allows you to password protect the bootloader. If you really want to. Now, let's flip to the **Advanced** tab: [![Advanced Startup Settings](http://gerard.interwebworld.co.uk/files/2009/02/advanced-startup.jpg)](http://gerard.interwebworld.co.uk/files/2009/02/advanced-startup.jpg) The **number of kernels** option keeps your startup list tidy, removing all the outdated kernels and just displaying the most recent one. Tick the box, and set the **number of kernels to keep** to your desired amount. The miscellaneous options give you the ability to create a rescue floppy (useful if you manage to wipe your master boot record), or you can restore the original GRUB settings. Now, that was _much easier_ than messing with the menu.lst file, wasn't it? **Stumblers!** If you're a [**StumbleUpon**](http://www.stumbleupon.com) user, and you found this post useful, please give it a thumbs up and some kind words! I'm an active SU user, so please do check out [my profile](http://gerardmcgarry.stumbleupon.com/) and stumbles! Cheers :)