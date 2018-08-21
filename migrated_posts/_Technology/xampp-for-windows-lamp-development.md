---
title: 'XAMPP For Windows: LAMP Development'
date: Tue, 13 May 2008 22:35:39 +0000
draft: false
tags: [LAMP, Web Design, Windows, XAMPP]
---

Because I develop sites using both ASP.NET and PHP, I’m tied to a Windows setup for the foreseeable future. However, I’ve been doing more and more work recently with LAMP-type applications which normally require a working Linux server installation.

Although I currently dual-boot with Kubuntu (because KDE’s pretty), I don’t have the Linux know-how to set up and run Apache/MySQL/PHP. [XAMPP is a fantastic alternative](http://www.apachefriends.org/en/xampp-windows.html), because it runs a fully configured LAMP setup on a Windows machine.

I installed it today for the first time, and one warning is to switch off or disable your IIS installation, because Apache will conflict with IIS for use of Port 80, and FileZilla will also clash with IIS for access to FTP on Port 21.

Anyway, I was able to install WordPress into a local folder in a matter of minutes and set up a new database in MySQL just as quickly using the bundled phpMyAdmin.

Also, I was able to enable mod_rewrite for my WordPress blog by modifying httpd.conf (in XAMPP/apache/conf/) - look for the line that identifies the rewrite module and remove the # from the start of the line. Restart your apache server and you’re all set.

This looks like it could be a lot of fun! The biggest advantage is being able to test and develop sites on my own test server, rather than constantly FTPing to a remote site.