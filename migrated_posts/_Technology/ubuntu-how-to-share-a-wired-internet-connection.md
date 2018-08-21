---
title: 'Ubuntu: How to share a wired internet connection'
date: Fri, 23 Jul 2010 15:59:43 +0000
draft: false
tags: [How-To, Linux, Networking, Technology, Tutorials, Ubuntu]
---

[![Ubuntu logo](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/02/ubuntu-logo.jpg)Ever been stuck with a single, wired internet connection, but needing to connect more than one computer to the internet? You'll be glad to know that with Ubuntu, it's easy to share an internet connection by creating an ad-hoc wireless network. It happened us recently on holiday - we had a single wired network connection, but two laptops. Both machines were wireless enabled. Here's how to set up the connection: 1) Connect the ethernet cable to the laptop that will be hosting the wireless network. Do a quick check to ensure that you can access the internet from that computer! 2) Click the networking icon at the top right of your screen, and select the **Create new wireless network** option at the bottom of the menu. You'll be presented with the following dialog: [![Wireless sharing setup in Ubuntu](http://gerard.interwebworld.co.uk/files/2010/07/wireless-ubuntu.jpg)](http://gerard.interwebworld.co.uk/files/2010/07/wireless-ubuntu.jpg) I've filled in some sample details here to help you out. Using the passphrase is a lot more straightforward than a complicated HEX code - you can literally type in a memorable passphrase that you can share with your friends or colleagues. Once you click the **Create** button on this dialog, the new network (in this case, 'Interweb') will be available to other wireless computers in the vicinity. They can connect by selecting the **Interweb** network (if you used my example) from their computers and typing in the passphrase you set up.

Deleting the network
--------------------

If you decide you want to stop hosting your wireless network, simply right click on the networking icon and select **Edit Connections**. Go to the Wireless tab, find the connection you created and delete it. Easy!

Video tutorial
--------------

Here's a quick video I created showing how to set up a wireless network on your Ubuntu machine. http://www.youtube.com/watch?v=W\_xH\_QLeYlI