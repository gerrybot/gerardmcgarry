---
title: 'Installing MySQL for Nginx'
date: Sat, 06 Nov 2010 01:49:00 +0000
draft: false
tags: [MySQL, Nginx, Technology]
---

[![MySQL logo](http://gerard.interwebworld.co.uk/files/2010/11/mysql-logo.png)](http://gerard.interwebworld.co.uk/files/2010/11/mysql-logo.png)Following on from our last step in [setting up an Nginx server](http://gerardmcgarry.com/2010/installing-nginx-on-a-media-temple-ve-server/), we need a database to store our CMS data in. What's a good database to install on an Ubuntu server? Oh yeah, MySQL! MySQL is a doddle to install - you simply connect via your SSH client and run the following command:

    sudo apt-get install mysql-server php5-mysql mysql-client

While it's installing, you'll be prompted for a root password for the MySQL server. Give it a good, secure password and you'll have to confirm the password before the installation continues. And you'll need this later on for connecting your web app to the database, so write it down!

Setting up a database
---------------------

Next, we'll connect to the MySQL server through the command line and create a database container for our site. If you remember from our last article, we'll be setting up a database for the spare domain, [www.interwebworld.co.uk](http://www.interwebworld.co.uk). I'm going to call this database _interweb_. Connect to MySQL with the following command:

    mysql -u root -p

You'll be prompted for the root user password. Enter that and you should get a welcome screen. Now, type the following command to set up your database:

    create database interweb;

As with the SSH account on your website, you don't want to use the root account for normal operations. Therefore, you should run this command in MySQL to set up a database user with rights on the database we just created:

    grant all on interweb.* to 'youruser' identified by 'yourpassword';

If you're not comfortable working with your databases via the command line, you should also consider installing [phpmyadmin](http://www.phpmyadmin.net/) \- it's easy to install through the usual repositories. There's a little bit of setup to do to make this work, and we'll cover that in the next exciting installment! Well, not quite. Before phpmyadmin will run, we need to install a PHP processor. We'll also need this for our Drupals or our Wordpress CMS. So, next up we install PHP-FPM - which, like Nginx, is gaining approval in webmaster circles where they gather to talk about these types of things...