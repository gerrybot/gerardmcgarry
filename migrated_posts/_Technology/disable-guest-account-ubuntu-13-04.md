---
title: 'Linux: How to disable the guest account on Ubuntu 13.04'
date: Mon, 14 Oct 2013 09:32:50 +0000
draft: false
tags: [Howto, Linux, Ubuntu]
---

[![Ubuntu Logo](http://gerard.files.wordpress.com/2012/10/ubuntu-logo.png)](http://gerard.files.wordpress.com/2012/10/ubuntu-logo.png)By default, **Ubuntu 13.04** has a usable guest account. I discovered this yesterday evening when I noticed my daughter had logged on as a guest. Obviously some of you won't be comfortable having an accessible guest account on your computer. You'll be pleased to know there's an easy way to disable the guest account (and toggle it back on again if you need to).

Instructions
------------

Fire up a terminal session on your Ubuntu machine, then type in the following command and hit **Enter**.

    sudo /usr/lib/lightdm/lightdm-set-defaults -l false

Reversing this process is as simple as changing the `false` `at the end to a` `true`.

    sudo /usr/lib/lightdm/lightdm-set-defaults -l true

What this changes
-----------------

What's happening in the background when you execute this command? Quite simply, it inserts a line in the `/etc/lightdm/lightdm.conf` file that says `allow-guest=false`. So, the alternative way to make this edit - if you like doing things the _long way_ \- is to use gedit or nano to edit the lightdm.conf file and add that line yourself. And obviously switch false to true to re-enable guest access. Now, once you've made the changes, you'll need to reboot your computer for the guest account to be fully disabled.