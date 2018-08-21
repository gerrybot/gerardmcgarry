---
title: 'Drupal Theming Tip: Show messages depending on whether the user is logged in or not.'
date: Sun, 08 Mar 2009 14:36:58 +0000
draft: false
tags: [Drupal, Technology, Web Design]
---

[![Drupal logo](http://gerard.interwebworld.co.uk/files/2009/05/drupal.jpg)](http://gerard.interwebworld.co.uk/files/2009/05/drupal.jpg)I'm working on a Drupal theme at the minute where I need to work out whether a user is is logged in (or not) and show them a message accordingly. One such scenario is user invitations:

1.  I want to build in an invitation to become a member. If someone is already logged in, they don't ned to see this message. If they're not a user (or not logged in), I want them to see a message saying "Join our community" and providing a sign-up link.
2.  Certain pages have a wiki functionality. I want non-users to see an invitation to join up and edit, while existing members will see a message encouraging them to get involved. Slightly different messages, but both hopefully effective.

So, how does one do this in a Drupal theme? _It's actually quite easy._ For older versions of Drupal, they used to recommend the following code:

    <?php
      global $user;
      if ($user->uid) {
        // User is logged in.
      }
    ?>

But in Drupal 6 there's a tidy little function you can use: [`user_is_logged_in()`](http://api.drupal.org/api/function/user_is_logged_in/6) So, using that as the basis for a quick bit of code, you'll have something like this:

    <?php if (user_is_logged_in()) {
    	//message to logged-in user
    } else {
    	//message to anonymous user
    }
    ?>

Naturally, if you know a bit about PHP, you'll be able to customise this to a number of different requirements. Hope this helps a few people out there in Drupal-land.