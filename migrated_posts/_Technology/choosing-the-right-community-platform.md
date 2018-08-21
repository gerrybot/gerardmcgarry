---
title: 'Choosing the right community platform'
date: Thu, 04 Sep 2008 14:58:58 +0000
draft: false
tags: [Communities, Drupal, Technology, Web Design, WordPress]
---

I've been weighing up two blogging/CMS platforms recently with a view to launching a new community site. Those platforms are [Drupal](http://drupal.org) and [WordPress MU](http://mu.wordpress.org). **Drupal** is a leading open source content management system. With the aid of some nifty add-on modules, Drupal is capable of becoming just about anything your imagination wants. Blogs, wikis, forums, event calendars and much more. **WordPress MU** is the multi-user implementation of WordPress. It powers the hugely popular WordPress.com blogging community and is mostly limited to just blogging. That said, it's a familiar platform for many and otoriously easy to use.

Considering Drupal
------------------

One install and common functionality for everyone delivered via add-ons. Site architecture can be determined and configured centrally. One common theme by default, with the opportunity to add other themes so that users can customise their experience. Doesn't allow for personalisation of their specific blog though. Spam management can be centrally controlled via [Mollom](http://mollom.com), a content monitoring service developed by the same brains behind Drupal. Just recently noticed that the Mollom service has now restricted free usage and has a paid-for option for larger blogs. Spam management can optionally be controlled by restricting comments to logged-in users, but there's an obvious trade-off in usability here! I've had some trouble with Drupal version upgrades in the past. Minor version upgrades aren't too bad, but major versions 5.x to 6.x have caused me some pain. Always keep a development mirror of your site to test upgrades on before you go live!

Considering WordPress MU
------------------------

WordPress is probably the best known blogging software there is. However, WordPress MU is a different beast entirely. I did a test install of it this week and it scared the hell out of me. In terms of spam management, you can install Akismet as a plugin, but you can't hard-code your Akismet key for each blog created. So, you can either send all your users over to WordPress.com to get a key of their own, or you can think of something else. There's a Mollom plugin for WordPress incidentally, but it's unclear as to whether this can be used in a multi-user environment. One the plus side, you can have themes assigned on a per-blog basis, which gives your users the ability to personalise to a degree. However, you've got to presumably design or install those extra themes... The subdomain setup which is what you want for this kind of blog architecture is also a difficult setup. I got it working, then installed a domain redirect plugin to see if it would be possible for users to redirect a domain to their blog. Didn't work. And unlike WordPress regular, the multiuser implementation doesn't have such reliable documentation or how-to posts helping with implementations. Finally, because I read so much around the time of the WordPress.com launch, I'm aware that there's little guidance surrounding WPMU and server architecture. Now, obviously running on a shared-hosting account is a big no-no. But the question remains, what's appropriate for a WPMU implementation and will it scale to other architectures?

Drupal FTW?
-----------

For the moment, I'm gravitating toward Drupal as the content management system for my new community. I've been using it fairly successfully elsewhere, and I think it has some nicely joined-up multi-user features. Yes, it'll need a bit of work to get it set up to my satisfaction, but it may be the best option in the long run. Among the challenges with Drupal are optimising the WYSIWYG editor (TinyMCE or FCKEditor?) and making file/image uploads intuitive, as well as allowing easy embedding of YouTube and other media. Profile configuration is another area I want to look at in better detail down the line, so that people can share information about themselves, pictures, etc. And one final notion - what type of hosting is most appropriate? I imagine migrating a Drupal installation across hosting platforms will be a tad easier than moving a WPMU site - hopefully!

Your Input...
-------------

Have you got any experience with either Drupal or WPMU? Am I barking up the wrong tree in choosing Drupal? Any advice or input from either Drupal or WordPress afficionados is gratefully received!