---
title: 'Drupal 6: Get notification emails when modules are updated'
date: Mon, 30 Mar 2009 20:55:22 +0000
draft: false
tags: [Drupal, Security, Technology, Tutorials]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)Here's another quick Drupal 6 tip: if you have the **Update Status** module enabled, you can get notifications by email when updated modules for your site are available. This is a handy thing to have, particularly for security updates. As I understand it, the Update Status module periodically checks against the Drupal website (on each cron run) and will notify you if updates are available. I think it only checks activated modules though, so if there are updates to inactive modules, it won't notify you. 

Setup for Update Notifications
------------------------------

Here are a few notes on getting update notifications up and running:

1.  Is the Update Status module enabled? If not, browse to **Admin** -\> **Modules** and enable it.
2.  Is there a cron run configured? If not, set up a regular cron run for [your Drupal installation](http://drupal.org/cron). This is just good practice.
3.  Now, browse to your Drupal admin pages, then go to **Reports** -\> **Available Updates** and click on the **Settings** tab.
4.  In here, you can enter a series of email addresses to notify when updates are avalable. Then you can opt for check daily or weekly for updates, and whether you want to receive security updates _only_ or for all updated modules.

In my experience, the more modules you have installed, the more frequently you'll receive these updates. Personally, I prefer to set it just for security updates so that I get the important notices only.