---
title: 'How to install Apache, MySQL and PHP on Ubuntu'
date: Thu, 23 Sep 2010 20:59:19 +0000
draft: false
tags: [Linux, Technology, Ubuntu, Web Design]
---

If you're working on developing websites, it's handy to have a development server to test your designs and code against. If you're running Ubuntu, it's fairly easy to install a LAMP stack - I use mine for running test versions of WordPress and Drupal for themeing, but you can use this setup for all kinds of web development. In this post, I'm going to show you how to quickly install Apache, MySQL and PHP to give yourself a fully-functioning development server. By the way, I'm using Ubuntu 10.04 to carry out this tutorial. We'll do the installation in three stages: Apache first as the web server, then PHP5 and finally the MySQL database server. And we're going to do this through the command line, although I'll give you tips on GUI installation at the end.

Installing Apache
-----------------

This bit's a doddle. Type the following command and press enter. You'll be prompted for your password and you might have to confirm a request during the procedure:

    sudo apt-get install apache2

**Confirm it works!** Once you're done, fire up a web browser and visit http://localhost into the browser. You should see a web page confirming that the server is up and running. **Where do I put my website files?** By default, Apache creates a folder at /var/www. That's your root directory, so put your files there.

Installing PHP5
---------------

Time to install PHP - this is the processor that does all the heavy lifting and makes running PHP-based content management systems like WordPress and Drupal possible.

    sudo apt-get install php5 libapache2-mod-php5

Next, you need to restart Apache to activate PHP and get started:

    sudo /etc/init.d/apache2 restart

If you want to test whether PHP is working or not, create a simple PHP file in /var/www. If you include the line in your file, it should print out a list of PHP config information when you load the file in your browser.

Installing MySQL
----------------

Right, now we need to install the MySQL database server...

    sudo apt-get install mysql-server

During the installation routine, you'll be prompted to set a password for the root user. Give it a good secure password (obviously) and the installation will continue. Before we go any further, it's a good idea to install phpMyAdmin to make administering your databases more easy. Type this command:

sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

During the installation you'll be prompted for which webserver type you want to configure phpMyAdmin for - choose **apache2** and hit return. Now, to get MySQL working with PHP, we need to make a quick config tweak. We need to edit the PHP.INI file to uncomment the line that reads ";extension=mysql.so" - to uncomment, you simply remove the semicolon at the start of the line and save the file. The file is protected, so you must do this using sudo. Restart the apache2 service using the same command we typed above. You should find that phpMyAdmin is now available at http://localhost/phpmyadmin. **That's it!** Now that your web server is up and running, you can install whatever PHP-based content management systems you want - or begin developing your own!