---
title: 'Drupal Howto: Use Modr8 and Modr8 Bypass to protect your site from spam'
date: Mon, 24 Jan 2011 19:33:25 +0000
draft: false
tags: [Content Moderation, Drupal, How-To, Spam, Web Design]
---

The 5 or 6 regular readers of this blog may remember that a while back our Unreality Shout site [was attacked by spammers and pretty heavily vandalised](http://gerardmcgarry.com/2010/drupal-question-moderating-content-from-new-users-on-a-site/). I asked for suggestions for workflow solutions that would prevent a repeat of this, but without making it harder for established members to post content. [![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)Some of you Drupallers kindly sparked off some great ideas, and after flirting with the [Workflow](http://drupal.org/project/workflow) module, I decided to go with [Modr8](https://drupal.org/project/modr8) and [Modr8 Bypass](http://drupal.org/project/modr8_bypass). Modr8 provides the basic functionality to hold back content from being published. Modr8 Bypass then gives you the ability to choose users (based on role) who should be allowed to bypass those rules and go straight to publishing their content. I wanted to share a tutorial for configuring Modr8 with you guys, because it took a little bit of fiddling just to get it working properly. Let's roll up our sleeves and dive in...

1\. Create a new user role and assign it to trusted members
-----------------------------------------------------------

For this to work, we need to distinguish between ordinary authenticated users and people that we trust to publish content unmoderated. I created a role called **Established Member** and assigned it to people on the site who were regulars and who published clean, well-written posts in the past.

2\. Install the modules
-----------------------

I'm assuming you guys know what you're doing - install the Modr8 and Modr8 Bypass modules in whatever manner you're used to and then activate them.

3\. Configure Content Type Workflows
------------------------------------

OK, we've got a bit of tweaking to do to Content Types. What you want to do here is to remove the **Published** checkbox for content types you want to protect. On [Shout](http://unrealityshout.com), we protected our Blog, Wiki page and Group creation pages. New members could post unrestricted in the Forum and upload photos, but we wanted the content on those other types to be of a higher calibre. To remove the **Published** checkbox, simply go to **Content Types** in your Drupal backend, edit the types you want. The checkbox you're looking for can be found under **Workflow Settings**. You should also tick the **In Moderation Queue** checkbox, which tells Modr8 to list the content for review. This is also in the workflow settings for each content type.

4\. Configure Modr8 Settings
----------------------------

Next up, we configure the Modr8 module - go to the Modr8 page under Site Configuration. If you've installed both modules (basic Modr8 _and_ Bypass), you'll have two tabs. The first tab deals with default moderation actions, and you can configure standard emails that'll be sent to your users whenever you approve or reject some content. Because I'm dealing with spammers here, I opted not to send emails on deletion of content, but this whole page should be configured to your own requirements. **Modr8 Bypass** has two checkboxes. Make sure they're both ticked. They're fairly self-explanatory - they undo the custom workflow settings we set up in step 3. This means that content is published automatically for your chosen user roles. Or so you might think - there's one more step to take...

5\. Configure Modr8 User Permissions
------------------------------------

This is a big gotcha - you've got to configure the user permissions not only to identify the roles who can bypass moderation, but also for the content types. It's actually quite a nice, granular setting if you've got a bigger site with lots of content types and roles.

1.  Go to **User Permissions** in your Drupal admin area, and scroll to the Modr8 section.
2.  Under the Modr8 Module settings, tick "Bypass moderation queue" for your chosen roles.
3.  There's a Modr8 Bypass section under this - check the "bypass \[name of content type\] moderation" under the desired roles.
4.  Save your Permissions settings.

6\. Test, Test, Test!
---------------------

Yes, once you're done, fire up a couple of test users, one in your Established Members role and one regular authenticated user and try to post content. The Established Member should be published right away, while the regular user should see a content moderation warning. To moderate content, Modr8 installs a page in the **Content management** area of your Drupal admin section. Look for **Moderated Content**. Managing approval from this page is pretty straightforward. You can sent little messages to your users with approval or rejection of their posts.

One last thing...
-----------------

As far as I can tell, Modr8 _doesn't_ issue an email to the admin to alert them to new content in the queue. That's a bit of an oversight. However, by happy coincidence, I use the Antispam module with Akismet on my site. Because the new posts are set to unpublished by default, Antispam sends me an email whenever something new is in the queue. Finally, a big thank you to Michelle Cox for her advice to look at these two modules!