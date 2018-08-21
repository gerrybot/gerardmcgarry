---
title: 'How to install PHP-FPM for Nginx on an Ubuntu 10.04 server'
date: Sat, 06 Nov 2010 18:42:28 +0000
draft: false
tags: [Nginx, PHP, Technology, Ubuntu, Web Design]
---

[![Nginx logo](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)This is the third part in my series of articles looking at [building an Nginx server on the Media Temple VE service](http://gerardmcgarry.com/2010/installing-nginx-on-a-media-temple-ve-server/). We currently have a working Nginx installation and a domain name pointed at the server, and in the last step, we [installed MySQL and created a first database](http://gerard.interwebworld.co.uk/2010/installing-mysql-for-nginx/ "Installing MySQL for Nginx") to store our CMS data. In this phase of the installation, we'll be installing [PHP-FPM](http://php-fpm.org/) to handle the PHP from WordPress or Drupal. We'll be working mostly from [the guide](http://wiki.mediatemple.net/w/Install_PHP-FPM_on_Ubuntu_10.04) on Media Temple's knowledge base, coupled with some tuning parameters from EndOfWeb (broken link removed). Installing PHP-FPM is quite a straightforward process - just a matter of following some simple aptitude requests, then making some small edits to the configuration file to fit our server. Let's get started:

Add the right repositories!
---------------------------

    sudo aptitude install python-software-properties
    sudo add-apt-repository ppa:brianmercer/php

Next, run this command to update your repositories list:

    sudo aptitude -y update

Install the required software
-----------------------------

Now that we've got our additional repository ready, time to install the necessary components. Run the following commands - the first two download and install the software, the last one starts the php5-fpm service:

    sudo aptitude -y install php5-cli php5-common php5-mysql php5-suhosin php5-gd
    sudo aptitude -y install php5-fpm php5-cgi php-pear php5-memcache php-apc
    sudo service php5-fpm start

Tuning the PHP-FPM service
--------------------------

Jump to the fpm directory and edit the php5-fpm.conf file to tune the service. Luckily, the tutorial at EndOfWeb is based on a 512 (ve) server, which is what I'm running, so let's just apply those settings. Open the config file -

    cd /etc/php5/fpm
    sudo nano php5-fpm.conf

Edit the following settings. I found that in my default configuration, the pm value was set to static, therefore all the other settings were commented out. So, don't forget to uncomment the settings before changing them!

    pm = dynamic
    pm.max_children = 8
    pm.start_servers = 2
    pm.min_spare_servers = 2
    pm.max_spare_servers = 3
    pm.max_requests = 500

And naturally, restart the php5-fpm service when you're done. At this point, we've got all the necessary components to run a PHP-based application from our [Nginx](http://nginx.org/) server - Nginx, MySQL and PHP. They call this an LNMP stack (as opposed to LAMP). Of course, that would be a tiny bit _too_ simplistic, so in my next article I'm going to be looking at how Nginx handles virtual servers so that we can serve more than one site from our (ve) server.