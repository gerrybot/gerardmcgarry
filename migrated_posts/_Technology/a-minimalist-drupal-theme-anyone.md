---
title: 'A minimalist Drupal theme, anyone?'
date: Sun, 29 Mar 2009 22:17:43 +0000
draft: false
tags: [Drupal, Technology, Web Design]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)If you were reading a couple of weeks back, I was musing about the effectiveness of [minimalist blog designs](http://gerardmcgarry.com/blog/minimalist-blog-designs-seo) and their impact on search engine optimisation. The basic notion was that by eradicating all the extra stuff on the page and just displaying the page and the bare minimum of navigational links, you could improve search engine relevance and as a result, rank higher for any given search term. Why? Because, providing that the content is well written and follows the principles of good titling and semantic markup, there will be less irrelevant garbage on the page to confuse a search engine. This follows on from the current discussion surrounding Twitter's value in terms of SEO - literally just the title and the content are displayed, along with a handful of navigational links back to the member profile.

My Experiment
-------------

I've decided to create a standard, one-column Drupal theme that only displays the content and not much else. I've left interlinking to the standard Drupal categories, but removed sidebars, Twitter statuses and anything else not relevant to the content. The design (I like to think) is quite elegant: I've put this together using the [960 Grid framework](http://960.gs/), which helped get the layout together quite quickly. There are a few finishing touches I want to do to the design - tweaks to the CSS and removing bits of the default after-content links I'm not fond of. The comments need a tidy-up as well. The idea is to use this theme for a while and monitor the difference in search engine ranking of several pages.

Other SEO modules for Drupal
----------------------------

It's worth mentioning that I use a couple of extra modules to optimise my pages. The first is the [nodewords module](http://drupal.org/project/nodewords), which autogenerates META description tags for each page. I'm also using [Pathauto](http://drupal.org/project/pathauto) to generate clean URLs that include the keywords from the title in the URL. Third - and I shouldn't be using this, because it's not ready for live use - the [XML Sitemap](http://drupal.org/project/xmlsitemap) that generates a sitemap and auto-submits it to the 4 major search engines. Despite the natural interlinking that Drupal does, I prefer to have this for a little extra piece of mind to let the search engines have a full inventory of content on the site. For monitoring of visitor stats, I'm using the Google Analytics module to capture that data.

Releasing this as a theme
-------------------------

When I helped out with the [Freelinking module recently](http://gerard.interwebworld.co.uk/2009/contributing-to-drupal-the-freelinking-module/ "Contributing to Drupal: The Freelinking Module"), I mentioned that I wanted to try and contribute more to Drupal. It's my intention to refine this theme and release it as a free download as soon as I've got a version I'm happy with. Of course, I've got my reservations about the usability of the site due to the lack of links. I'm betting the bounce rate will go through the roof because people won't stick around once they've read the page they landed on. Still, it's a chance I'm willing to take for the sake of this experiment. **Update:** This is now available as the [GerryBot theme for Drupal](http://gerard.interwebworld.co.uk/2010/gerrybot-a-free-minimalist-theme-for-drupal/ "GerryBot: A free minimalist theme for Drupal"), which you can download for free.