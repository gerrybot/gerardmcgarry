---
title: 'How to remotely connect from Ubuntu to a Windows machine'
date: Thu, 26 Feb 2009 20:39:53 +0000
draft: false
tags: [Linux, Technology, Ubuntu]
---

In deciding to run Ubuntu in a Windows environment (I run a Windows server as well as a couple of Windows XP machines), one of my key concerns was being able to connect to those Windows machines. Now, looking around Ubuntu, you might come across an application called **Remote Desktop Viewer**. This will happily connect between Ubuntu machines and computers running VNC servers. But it doesn't do RDP (Remote desltop protocol) which you need to connect to Windows. What you need is the **rdesktop** command line utility _or_ the **Terminal Server Client**, which is a GUI front-end to rdesktop. The client is quite useful if you're not especially fond of command line working. If you've used the Remote Desktop tool in Windows before, the interface is quite similar. From what I can see, in my version of Ubuntu (8.10 - Intrepid Ibex), both rdesktop and Terminal Server Client are installed by default. Unfortunately...neither are integrated into the program menus, so you've got to run them from a command.

Starting rdesktop and tsclient
------------------------------

A good keyboard combination to know is ALT+F2 - this brings up a run window. Type in **rdesktop _servername_** and a Windows logon prompt will automagically appear. It might be a little bit small, so you can tweak the command next time. Try **rdesktop -u _username_ -g 1024x768 _servername_** and this will set the window size to 1024 x 768 and prepopulate the usename field. If you want more options you can use, bring up a terminal window and type **man rdesktop** to get a full description of all your available command options.

tsclient - Terminal Server Client
---------------------------------

OK, fire up that ALT+F2 command, and type in **tsclient**. You'll see the following settings screen: [![Terminal Services Client](http://gerard.interwebworld.co.uk/files/2009/02/tsclient.jpg)](http://gerard.interwebworld.co.uk/files/2009/02/tsclient.jpg) You can get away with the basics of typing in the computer name in the first box, but there are dozens of options. The **display** tab allows you to set the window size or choose full screen mode. Have a browse among the options and see what suits you. Anyway, as usual, I hope this helps anybody who's trying out Ubuntu. The **rdesktop** tools have helped me a lot in getting into Ubuntu, but having a lifeline to my Windows environment. If you've played with other remote desktop tools in Ubuntu, feel free to give your thoughts and tips in the comments.