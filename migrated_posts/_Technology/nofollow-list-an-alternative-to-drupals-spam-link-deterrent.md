---
title: 'Nofollow List - An alternative to Drupal''s spam link deterrent'
date: Fri, 04 Dec 2009 19:36:32 +0000
draft: false
tags: [Drupal, SEO, Spam, Technology, Web Design]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)Something I've _hated_ about running community sites on [Drupal](http://drupal.org) is the cursed Spam Link Deterrent filter. The idea behind this filter is that it applies rel="nofollow" to any links in user-generated content. And the reason this is necessary is that when you have a membership site and you allow users to create content on it, you inadvertently attract spammers who want to drop links back to their own site. By applying the _nofollow_ attribute, you are telling search engines not to count that link as 'editorially approved' - therefore, the spammer doesn't derive any value from the link. The problem with the Spam Link Deterrent is that it's an all or nothing solution - even internal links to other content on the site get this added to them. This means that your site loses a lot of value from natural internal links.

Enter Nofollow List
-------------------

[Nofollow List](http://drupal.org/project/nofollowlist) is a Drupal module that was developed for another reason entirely - to attempt to curb the monopoly of links toward massive sites like Wikipedia. Originally, it was intended to be a blacklist tool, applying _nofollow_ to reduce the amount of link value those sites were gaining. I thoroughly approve of this usage, by the way - I believe that the strength of links to sites like Wikipedia is actually detrimental to the 'level playing field' of the web. But that's a debate for another day... Anyway, there's another usage of Nofollow List that I've been using on [Unreality Shout](http://unrealityshout.com) recently - using it as a whitelist to allow unrestricted links within my network of sites, but applying _nofollow_ to other sites that I can't vouch for. This means that any spam content or links to giant authority sites get nofollow applied to them while links within the Unreality network of sites work perfectly.

Configuring Nofollow List
-------------------------

It's pretty straighforward to set this module up -

1.  Upload the module and enable it in Drupal.
2.  Go to **Site Configuration** -\> **Nofollow List** and switch it to **Whitelist** mode. Next, add the names of the domains you want to whitelist (without the http://) - one entry per line.
3.  Save this configuration, of course!
4.  Go to your **Input Filters** configuration and enable the **Nofollow List filter** on every Input Type your users use. You might want to disable the **Spam Link Deterrent** to prevent conflicts.
5.  That's it - I recommend you test this configuration first. I created a post that linked to a range of site, some on the whitelist, some not. I was then able to analyse the source code of the published post to see that it was working.

I hope this helps some other Drupal users who've been struggling with how to protect against spam content but want to mximise the SEO possibilities for their site. I just wonder why this module hasn't replaced the Spam Link Deterrent in Drupal core yet. It's simple enough to configure, and could be set up to automatically include the domain of the site it's running on.