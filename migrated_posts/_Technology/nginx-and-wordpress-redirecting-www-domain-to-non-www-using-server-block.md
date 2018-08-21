---
title: 'Nginx and WordPress: Redirecting www domain to non-www using server block'
date: Sat, 08 Jan 2011 19:21:49 +0000
draft: false
tags: [Nginx, SEO, Web Design, WordPress]
---

[![Nginx logo](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)](http://gerard.interwebworld.co.uk/files/2011/01/nginx-logo.png)This is a quick tip post to show you how to redirect the www version of a domain to it's non-www equivalent using [Nginx](http://nginx.org/). The reasons for doing this are quite technically dense, so a knowledge of web hosting and SEO might be useful. Basically, having the same site available at both www.yoursite.com and yoursite.com means that there are two identical copies of your site on the web. This is what's called 'duplicate content', and can [lead to your site being penalised by search engines](http://www.ragepank.com/articles/3/preventing-duplicate-content/). It's a quick thing to remedy if you're hosting your site with Nginx. You simply add a server block for the www.yoursite.com domain.

Setting up the redirect
-----------------------

When we did our [original tutorial on setting up Nginx](http://gerardmcgarry.com/blog/setting-a-virtual-host-nginx "Setting up a virtual host in Nginx"), I recommended setting up the config files using the name of the domain. So, your domain config should be in **/etc/nginx/sites-available** and the file should be named **yourdomain.com**. So, open up the yourdomain.com config file in a text editor

    sudo nano yourdomain.com

Next, add a new server block

    server {
            listen 80;
            server_name www.yourdomain.com;
            rewrite ^ http://yourdomain.com$uri permanent;
    
    }

The rewrite line redirects the request to the non-www version of the site. It also works for long requests like www.yourdomain.com/2011/01/yourpost/. The www part of the domain name will be stripped. Be careful not to add a trailing slash after the domain name - the $uri operator will do that for you! And obviously you want to use a permanent redirect, which translates as a 301 redirect for SEO purposes. In order to activate the new config, you have to reload the Nginx service.

    sudo service nginx reload

You should now test this config in your web browser. I've just run this code on a test site, and it works perfectly for requests to the domain itself _and_ to pages within the site. I've mentioned WordPress in the title of this post because that's the CMS that I've used in testing this out. It works extremely well for our requirements. I haven't tested any of this with Drupal or any other content management systems. Neither have I tried using a wildcard subdomain instead of the www.yourdomain.com entry in the server block.