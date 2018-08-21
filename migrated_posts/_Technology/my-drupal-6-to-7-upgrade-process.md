---
title: 'My Drupal 6 to 7 Upgrade Process'
date: Wed, 07 Dec 2011 12:06:46 +0000
draft: false
tags: [Drupal, Web Design]
---

[![Drupal 7 image](http://gerard.interwebworld.co.uk/files/2011/12/drupal7.jpg)](http://gerard.interwebworld.co.uk/files/2011/12/drupal7.jpg) Oh, hello! If you're reading this, it's the first entry I've posted to my blog since upgrading the site to Drupal 7! A major version upgrade like this isn't something to be taken lightly. I've had to drop certain modules along the way and make a full backup of my site's database and files. There's a certain kind of anxiety one experiences when doing a major version Drupal upgrade, so I thought I would share my upgrade process with others. Other Drupal users are invited to share their experience and tips on upgrading at the end of the post! So you want to upgrade to Drupal 7? Well, here's how _I_ went about it:

1\. Inventory your third party modules
--------------------------------------

Take stock of third party modules in use on your site. In its Drupal 6 incarnation, I was using CCK, Administration Menu, Boost, Date/Time (Date popup), Geshi Filter, ImageFieldl Assist, ImageAPI/ImageCache, Backup/Migrate, Feedburner, Global Redirect, IMCE, Integrated Metatags, Mollom, Pathauto, Read More Link, Scheduler, Site Verification, Token, Anti Spam, Google Analytics, Views, jQuery UI, WYSIWYG, XML Sitemaps. A bit of preparation work will save you time in the long run: CCK is largely integrated into Drupal core now, so there's no need to install it for Drupal 7. The Feedburner module seems to be dead in the water. Integrated Metatags has been replaced with the Drupal Metatag module. The list goes on. You need to check this sort of thing out in advance, because if there's a critical module on your site that hasn't been ported to Drupal 7 yet, it's a bit of a deal breaker. **Lesson? Do your prep work!**

2\. Backup your database
------------------------

I used the Backup/Migrate Module to backup my site's database and downloaded it to my hard drive. Worth mentioning that at this point you should consider the site frozen and **not** be adding any new content or files to it.

3\. Backup your CMS files
-------------------------

I also take a full backup of the entire Drupal installation at this point. You can either FTP your files locally, sync them over SSH with the rsync command or just zip up the entire Drupal installation and download the tar.gz file. I literally tarred up my entire Drupal root and downloaded the tarball, which left me with a reliable database and directory structure in case the upgrade was a disaster and I had to roll back.

4\. Maintenance mode
--------------------

Right, it's time to start making changes, so pop your site into maintenance mode so that visitors know the site is temporarily unavailable.

5\. Disable third party modules and themes
------------------------------------------

At this point, you want to disable all third party themes and set your theme to one of the Drupal defaults like Garland. This reduces the risk of upgrade problems associated with third party code and brings your site back to a basic Drupal install.

6\. Remove the old Drupal installation
--------------------------------------

Next, I create a subfolder under my 'sites' directory and move all the Drupal 6 themes and third party modules from sites/*/modules in there. The D6 versions will be incompatible with Drupal 7 anyway, but these serve as a reminder of which modules need to be reinstalled at the end of the upgrade process. Once I've done this, I create a folder in the site root and move the old Drupal installation in there. This is pretty much everything except the 'site' and 'files' folders, which contain the bulk of the user-generated content. Again, this is mostly a convenient failsafe in case we need to roll back, and it also ensures a clean Drupal 7 installation. It would be incredibly messy to just overwrite the old Drupal 6 with the new files.

7\. Download and unpack Drupal 7 files
--------------------------------------

Download and unpackage the Drupal 7 files. Whatever your preferred method - FTP the files up to your host, which. An be slow, or my favourite technique: using SSH and downloading and extracting the tarball. wget http://ftp.drupal.org/files/projects/drupal-7.10.tar.gz tar xfz drupal-7.10.tar.gz cd drupal-7.10/ cp --rpf * ../ rm -rf ./drupal-7.10/ rm -f drupal-7.10.tar.gz The above procedure downloads the latest version of Drupal (7.10 at the time of writing this), extracts it to a subfolder in my web root. I then jump into the Drupal-7.10 directory and copy all the files to the web root. The last two commands are simply cleanup to remove the archive and extracted files.

8\. Begin the upgrade process
-----------------------------

With all your Drupal 7 files in place, it's time to visit your site and begin the upgrade process. I found by hitting the homepage, it automatically threw an alert about the 'existing Drupal site' and gave a link to run the upgrade script. However, if there are any lingering issues that need addressed before you can upgrade, you'll see a diagnostic page detailing what needs fixed before you can continue. Once the upgrade is finished you should be able to see your site content. Breathe a sigh of relief that you've got this far and haven't lost your content!

9\. Reinstall and update modules
--------------------------------

Now begins the laborious process of downloading, enabling and upgrading the third party modules. I found drush to be essential here. I'd download one or two modules at a time, enable them and then run any attendant database updates. It's as easy as this (probably easier if you're a Drush ninja!): drush dl token pathauto drush en token pathauto drush updatedb I worked through my list of D6 modules and installed the Drupal 7 equivalents. I found that installing the Drupal 7 version of a module meant running database updates, which is why the updatedb command is included here. It's probably a good idea to check the functionality of each module as you go along to ensure it's working as expected and that there aren't any new settings that require your attention. Also worth checking your Drupal error log and status reports in case you need to address any compatibility issues.

10\. Install a Drupal 7 compatible theme
----------------------------------------

Before I began the upgrade process, I gave [my Gerrybot theme](http://gerard.interwebworld.co.uk/2010/gerrybot-a-free-minimalist-theme-for-drupal/ "GerryBot: A free minimalist theme for Drupal") a complete overhaul to work with Drupal 7. It's not quite ready for public use yet - there are a few things I need to tidy up - but I'm hoping to release a version of the theme for other Drupal users shortly. **Hint:** If there are any Drupal theming folks who would like to help tidy up the code for public use, please get in touch with me!

Over to you...
--------------

So, that's my Drupal 7 upgrade process. Hopefully others will find it helpful, and hopefully other Drupal experts will take advantage of the comments area to talk about their own process for upgrading from Drupal 6 to 7. If there's a more streamlined method, I'd certainly love to hear it!