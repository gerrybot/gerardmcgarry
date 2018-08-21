---
title: 'How to launch programs automatically at startup in Crunchbang Linux'
date: Sun, 23 Oct 2011 16:28:17 +0000
draft: false
tags: [Crunchbang, Linux, Tutorials]
---

[![Tux, the Linux mascot](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot-300x222.jpg "Tux, the Linux mascot")](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot.jpg)Remember when we configured our [headless Crunchbang computer the other day](http://interwebworld.co.uk/2011/10/21/how-to-install-and-configure-remote-desktop-in-crunchbang-linux/)? Now that we've got the machine up and running [and logging in automatically](http://interwebworld.co.uk/2011/10/22/crunchbang-linux-configuring-automatic-logins/), we want to start some programs running when the machine boots up. Well, the good news is that Crunchbang makes this process embarrassingly easy: the distribution has an autostart script that you can edit to run the programs of your choice. You can even specify a sleep delay so that programs load in a specific order and don't overload the machine. This is some heavenly scripting!

Finding and editing autostart.sh
--------------------------------

The autostart.sh script is the file you need to edit to customize your startup experience. Let's fire up the terminal and do some editing - we're going to fix a problem in my earlier post!

1.  Browse to the OpenBox config folder: cd ~/.config/openbox/
2.  Edit the autostart.sh file: nano autostart.sh
3.  Navigate to the bottom of the file - it's the smartest place to add your own custom entries. Along the way note that a double hash (##) denotes a comment - always advisable to explain the commands you've added to your script!
4.  We're going to configure the vino server service to start automatically, so add a comment like "## Start Vino server" and take a new line. In the new line, type `/usr/lib/vino/vino-server &` (the ampersand character at the end allows the script to continue processing any additional commands you might add). Add any other commands you'd like to run at startup.
5.  Save the autostart.sh file and then restart your computer to test.

The Sleep Command
-----------------

A useful variant is to add the "sleep" command to your script. This delays execution of your program by a specified number of seconds, allowing the computer to launch programs sequentially, preserving system resources or allowing other tasks to complete first. A modification of the command above would be: `(sleep 60s && /usr/lib/vino/vino-server) &` This would delay startup of the Vino server until 60 seconds after OpenBox loads. Feel free to play as creative as you like with this command - you could execute a system backup script, run an application or whatever else strikes your fancy.

Shutting down unwanted services
-------------------------------

You can also comment out software in the script that you _don't_ want to run - for example the novelty Statler app that says a random phrase every now and again. Simply find that line in the autostart.sh script and comment it out with "##". Likewise you could disable the Conky service or the screensaver - both of which are activated via this script. Find the lines you want and comment them out.

What else?
----------

So that's it for this little tutorial - I'd be interested to see what other things people use the autostart script for in Crunchbang. Also, is it available in other Linux distributions?