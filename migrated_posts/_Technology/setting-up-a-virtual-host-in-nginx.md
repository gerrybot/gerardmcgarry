---
title: 'Setting up a virtual host in Nginx'
date: Sat, 06 Nov 2010 19:47:16 +0000
draft: false
tags: [Nginx, Technology, Web Design]
---

[![Nginx logo](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png) If you've been following this tutorial series for [Nginx on Media Temple's (ve) server](http://gerardmcgarry.com/2010/installing-nginx-on-a-media-temple-ve-server/), you'll know that we've completed three steps - installing [Nginx](http://nginx.org/), MySQL and PHP-FPM for a fully functioning web server. In this fourth part, we're going to look at setting up a virtual host in Nginx. We need this, because the intention is to serve a few different sites from this server and each one will require its own virtual host setup. But first, a quick look at how Nginx does things and where it stores configuration and data. For a start, all the Nginx config files are located at /etc/nginx. The main Nginx configuration file is nginx.conf, but vhosts are declared in /sites-available and they're enabled in /sites-enabled.

    #The directory for Nginx configuration
    /etc/nginx
    
    #The default Nginx server configuration file
    /etc/nginx/nginx.conf
    
    #Vhost configuration files are stored in
    /etc/nginx/sites-available
    
    #Vhost configuration needs to be enabled here
    #use a symlink to the config file in sites-available
    /etc/nginx/sites-enabled

Before we move away from this, I should point out that all the website files are hosted in /var/www. You'll need to create a folder here to store your website files in. Let's try an example configuration. Change directory to sites-available:

    cd /etc/nginx/sites-available

Make a copy of the default config file to get started:

    cp default yourdomain.com

I've created a sample config file that works for the WordPress install on the [Interweb World](http://www.interwebworld.co.uk) domain - [download it from here](http://gerardmcgarry.com/files/config.txt) as a text file. You can edit this file to suit your needs (replace "yourdomain.com" with the domain name _you_ want to use.) From this config file - which I'll talk about in more detail in another post - I was able to install WordPress and configure it to use "pretty permalinks". Here are the contents of the vhost configuration file:

    server {
    	listen   80;
    	server_name  yourdomain.com;
    
    	access_log  /var/log/nginx/yourdomain.com.access.log;
    	root   /var/www/yourdomain.com;
    	index  index.php;
    
    	location / {
    		try_files $uri $uri/ @wordpress;
    	}
    
    	location @wordpress {
    		fastcgi_pass 127.0.0.1:9000;
    		fastcgi_param SCRIPT_FILENAME /var/www/yourdomain.com/index.php;
    		include /etc/nginx/fastcgi_params;
    		fastcgi_param SCRIPT_NAME /index.php;
    	}
    
    	location ~ .php$ {
    		try_files $uri @wordpress;
    		fastcgi_pass	127.0.0.1:9000;
    		fastcgi_index	index.php;
    		fastcgi_param SCRIPT_FILENAME /var/www/yourdomain.com$fastcgi_script_name;
    		include fastcgi_params;
    	}
    }

When your config file is saved, it is only _available_. You need to activate the configuration by creating a link to the config in the sites-enabled folder. Run this command:

    ln -s /etc/nginx/sites-available/yourdomain.com /etc/nginx/sites-enabled/yourdomain.com

As I understand it, the config files could be called whatever you like, but for ease of identification, it's best to use the domain name. Gotta have _some_ standards! Now that the configuration is in place, let's quickly prepare a location to store our webfiles. You can see from the above example that this directory is at `/var/www/yourdomain.com`. It needs to be created, so navigate to `/var/www` and run `mkdir yourdomain.com`. Restart the service - next step is restarting Nginx to make the new settings take effect. But first, run `nginx -t` to test the configuration - it'll tell you if there are any pesky syntax errors with your config, so you can fix them before restarting the Nginx service. If the test completes successfully, then restart the service:

    service nginx restart

Alternatively, you can run `service nginx reload` to load the new configuration into memory without needing to restart the service completely. That's it! You should have a fully working web server listening on your domain. Download and extract the latest version of WordPress to /var/www/yourdomain.com, then load up the domain in your browser and run the install process.

Hijinx with Nginx: Recapping what we've just done!
--------------------------------------------------

OK, to finish off on this post, I thought I'd recap on what we've just done. I'm sure there's a lot that can be done to tune the installation - like browser caching and gzip compression, but we'll look at these later on. For now, let's look over the process of setting up a vhost in Nginx.

1.  Browse to Nginx's sites-available directory, **make a copy of the default configuration file** and give it the same name as your domain.
2.  **Edit the yourdomain.com configuration file** \- use the configuration file above to set up the rules that'll allow WordPress to work on Nginx. Save the file.
3.  **Prepare the directory** that'll host the website's files - since Nginx hosts from /var/www by default, make a subdirectory in here, again using the domain name as the name of your directory - _it must be **exactly as you typed it** in the vhost configuration file!_
4.  Test the configuration with **nginx -t** and resolve any errors that this returns. When it returns successful, proceed to the next step.
5.  **Restart or reload** the Nginx service to allow the new settings to take effect.

I hope these steps help a few people to get started with Nginx. If you're an expert and I've missed something out, please comment or mail me to clarify the instructions. Just remember, I'm a beginner with Nginx myself, and there's lots to learn. I'll be sharing my discoveries here as I tune and refine the configuration, with the ultimate goal of moving one of our high-traffic WordPress sites to an Nginx server. A great starting point for newbies is the [Nginx wiki](http://wiki.nginx.org/Main), which carries [sample configuration files](http://wiki.nginx.org/Configuration) for most of the major content management systems, and some useful advice on best practises for your config.