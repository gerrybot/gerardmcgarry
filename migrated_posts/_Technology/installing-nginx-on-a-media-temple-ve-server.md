---
title: 'Installing Nginx on a Media Temple VE Server'
date: Sat, 06 Nov 2010 00:34:46 +0000
draft: false
tags: [Caching, Nginx, Technology, Web Design]
---

[![Nginx logo](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)I've become obsessed in the last few weeks with improving web performance. The more I've looked into optimization techniques, the more Nginx - pronounced "Engine X" - keeps coming up. It's an open source web server that's steadily gaining a name as a companion technology/replacement for Apache. Nginx can be used in two ways

1.  As a **reverse proxy cache** for Apache. In this mode, it'll speed up your PHP applications by caching static versions of files and serving them out far more efficiently than Apache does.
2.  As a **fully functioning server** in its own right. With a Fastcgi or PHP-FQM server, it can process PHP by itself without any need for the hefty Apache service.

After struggling with trying to get Nginx working as a reverse proxy on a Media Temple DV server, I ended up getting nowhere. Whatever the problem, I simply couldn't get this solution to work. So I decided to start with a fresh server - one of the new VE servers with a clean install of Ubuntu. I've installed Nginx on a local web server with WordPress and Drupal running on it, so the logical next step was to try it on a live server...

Point your DNS to Media Temple's servers
----------------------------------------

Pre-emptive move, this one: set the nameservers for your domain to Media Temple's nameservers - ns1.mediatemple.net and ns2.mediatemple.net. I'll be working with an old domain of mine, [www.interwebworld.co.uk](http://www.interwebworld.co.uk) for this experiment to get things up and running.

Installing Nginx
----------------

Before we begin, when you first get your VE server, it's fairly wide open. You need to follow the [instructions for securing your server](http://wiki.mediatemple.net/w/Securing_your_(ve)_Server) and setting up a normal user account with SSH access.

    sudo apt-get update
    sudo apt-get install nginx
    # Start the Nginx service
    service nginx start 

That's it. At this point, you should see the Nginx holding page for your domain. So the server's up and running - what next? Well, my plan is to have my Nginx server host a few virtual sites. They'll be based on content management systems like Drupal and Wordpress. We'll be setting these up manually, looking at how to install and configure MySQL and PHP-FQM. Oh, and we may just need something to allow us to connect by FTP and upload files to the server. Lots of fun ahead, and this is just the first step. Next we'll be installing MySQL on the server and setting up some databases.