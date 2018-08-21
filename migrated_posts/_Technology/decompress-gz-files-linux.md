---
title: 'How to decompress .gz files in Linux'
date: Sun, 08 Jun 2014 13:53:39 +0000
draft: false
tags: [Linux, Ubuntu]
---

[![Ubuntu Logo](http://interwebworld.co.uk/wp-content/uploads/2012/10/ubuntu-logo-150x150.png)](http://gerard.files.wordpress.com/2012/10/ubuntu-logo.png)I've been struggling this morning with a compressed SQL file - it had been given a .gz file extension, and I was trying to use the `tar` command to decompress it. Apparently this is stupid - there's a dedicated utility to decompress a .gz file - `gunzip`. It's as simple as this: `$ gunzip big-database-dump.sql.gz $ ls big-database-dump.sql ` (The `ls` command simply lists the extracted file, by the way) If you're using Ubuntu, there's a very easy way to extract the file using the GUI - simply browse to the .gz file you want, right click on it and choose the **Extract here** command. However, the time to use the `tar` command is when you're opening up a file like drupal-6.15.tar.gz `tar -zxvf Drupal-6.15.tar.gz` Hope this helps out other Ubuntu/Linux newbies who've struggled with file decompression!