---
title: 'How to enable a theme for a single site in WordPress Multisite'
date: Sun, 29 Sep 2013 21:41:30 +0000
draft: false
tags: [Web Servers, WordPress]
---

[![WordPress logo](http://interwebworld.co.uk/wp-content/uploads/2013/09/wordpress.png)](http://interwebworld.co.uk/wp-content/uploads/2013/09/wordpress.png) **WordPress MU** (or Multisite) is a fantastic way of managing multiple WordPress sites without the hassle of handling separate updates for each site. Because an MU installation shares resources, plugins and core files only need to be updated once and _every_ site is updated. Handy, right? With WPMU, you can install a range of plugins and themes, and with network-wide activation, all your WordPress subsites have access to those resources. The thing is, sometimes you want to restrict a theme to one particular site. It took me a while to work out how to do it, but it's actually quite simple. Here's a quick step-by-step of how to do it:

*   Start by going to the **Themes** section in **Network Admin**. Make sure your theme is installed (obviously) and that it is **not** network enabled. (Network enabled means it's available to all sites, and you don't want that in this case!)
*   Staying in **Network Admin**, go to **Sites**->**All Sites**. From this list, click on the name of the site you want to edit.
*   Click on the **Themes** tab. You should see a list of themes installed on the site. Find the theme you want and click the **Enable** link beside it.
*   Next, browse back to the WordPress **Dashboard** of the site you're working with. Go to the **Appearance** section and you should now see your theme is available. Activate the theme from there, customise it to your requirements and then check the live site to see how your theme looks.

Key screens:
------------

[![WordPress network disabled theme](http://gerard.files.wordpress.com/2013/09/network-disable.jpg)](http://gerard.files.wordpress.com/2013/09/network-disable.jpg) In the **Network** -> **Themes** section, it's important to make sure the theme _isn't_ network enabled - otherwise, it will be available to all sites in your network. Obviously, if you discover your theme is network enabled, make sure to disable it here. [![Single site theme enable screen](http://gerard.files.wordpress.com/2013/09/theme-enable.jpg)](http://gerard.files.wordpress.com/2013/09/theme-enable.jpg) Staying in the Network Admin area, go to the configuration for the individual site you want. Click on the themes tab and from here you can selectively enable new themes. Save your changes and make any widget/menu edits your site requires and your new theme should be live on the site. Hope this helps a few other WordPress network admins out there :-)