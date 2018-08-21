---
title: 'Give your Drupal site an SEO makeover'
date: Mon, 22 Mar 2010 21:48:18 +0000
draft: false
tags: [Drupal, SEO, Technology, Tutorials, Web Design]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)Drupal's currently my content management system of choice. But like virtually any CMS, Drupal needs some SEO tuning to make it more attractive to search engines. I've set up a number of websites using Drupal, and this post will gather together some of my standard actions for optimizing. I'll try to be as exhaustive as possible on this post, starting with the basics and moving toward more complex optimization techniques. This post, for the most part, looks at [Drupal](http://drupal.org/) modules that can automate the SEO process for you. None of this negates the need to have an accessible theme design and to do the usual SEO activities such as building backlinks to your site. Let's get started...

1) Enable clean URLs
--------------------

First stop in any new Drupal site is to enable clean URLs. This gets rid of the querystring-based yoursite.com?q=/node/121 URLs and replaces them with something like yoursite.com/node/121 - Not only is it much nicer to look at, but it paves the way for the next step:

2) Install and Configure the Pathauto module
--------------------------------------------

[Pathauto](http://drupal.org/project/pathauto) automatically creates text-based URLs for your site, so instead of this being gerardmcgarry.com/node/121, it'll actually be gerardmcgarry.com/blog/giving-drupal-site-seo-makeover. The logic behind this is that it will be more easily readable to the human eye, and it'll also carry all the salient keywords from your page title, which makes it more attractive to search engines. **In-depth config**: In its default state, Pathauto creates paths as content/title-of-your-post. However, with a bit of extra configuration, you can configure paths according to content type, so you have photo/statue-of-liberty and blog/state-of-the-economy. Go to **Site Building -> URL Aliases -> Automated Alias Settings** to fine tune how your URL Aliases are generated.

3) Install and Configure the Global Redirect module
---------------------------------------------------

While we're working with path aliases, it's a smart idea to install the [Global Redirect module](http://drupal.org/project/globalredirect). Where Drupal is a little lackadaisical about URLs and duplicate content, Global Redirect works as an enforcer to ensure that all variants of an URL redirect to a single, authoritative URL. Without it, you'll be able to access the same content at node/121 _and_ blog/state-of-the-economy, which looks bad to search engines. It's a simple function, but it can make a huge difference.

4) Install Nodewords module
---------------------------

They say meta data is dead, but even Google will use your Meta Description tag as a snippet in its search results. Installing the [Nodewords module](http://drupal.org/project/nodewords) will automatically generate those meta tags directly from your content, saving you from having to create them manually with each page. You can also configure Nodewords to create a keywords meta tag from the taxonomy tags used in the post. It's quite a powerful module than can be extended beyond what I've covered here, so take some time to delve into its possibilities. **Also try**: [Integrated metatags module](http://drupal.org/project/int_meta) \- which has a very similar set of capabilities, but is slightly less intuitive to set up.

5) XML Sitemaps
---------------

Providing an XML Sitemap for your site is essential for content discovery. The [XML Sitemap](http://drupal.org/project/xmlsitemap) module will automatically generate a sitemap for you and ping the major search engines to notify them of new content. Install the module, configure it. No site, Drupal or otherwise should be without a sitemap these days. **Go further**: Configure [sitemap autodiscovery](http://www.scribbledesigns.co.uk/2007/04/12/how-to-configure-sitemap-autodiscovery-for-your-website/) for your site by adding "SITEMAP: http://yoursite.com/sitemap.xml" to the end of your robots.txt file. **Even further:** I sometimes configure the tracker in Drupal, and add the /tracker link as a "Latest posts" menu item. This creates a well-linked directory of virtually every node on your site, which means no files end up orphaned or overlooked, especially on more complex sites where not everything (Image nodes, Organic Groups, Wiki pages) are published on the front page.

6) Site verification
--------------------

This works hand-in-hand with the XML Sitemaps module - if you're a member of Google, Yahoo! or Bing's various webmaster sites, you need to validate your site before they'll give you stats and information about your site. The [site verification module](http://drupal.org/project/site_verify) can handle both file and meta tag based methods of verifying your site with each search engine.

7) Google Analytics
-------------------

Continuing our theme of interfacing with the search engines, you need to install some kind of visitor tracking to track where your visitors are coming from, what pages they're viewing and the various other types of metrics that are important for monitoring your site's growth. I suggest Google Analytics because it's easily become the industry standard. The [Google Analytics module](http://drupal.org/project/google_analytics) for Drupal inserts the tracking code without you needing to edit your theme, and gives you some nice configurable extras. Of course, you need a Google Analytics account in the first place, but those are free and easy to set up.

8) Nofollow for user-generated content
--------------------------------------

Any community site that allows the public to sign up and create content will undoubtedly be targetted by spammers to drop links. If your moderation skills are poor, and you allow unfiltered links to bad websites, Google in particular takes a dim view of your site and will demote you in search listings. You'll lose traffic. You _can_ sculpt this by using nofollow on user-generated links. You can set this up in **Site Configuration -> Input Formats** \- enable the HTML Filter for your default input type and then enable the **Spam Link Deterrent** in there. This applies nofollow to all user-generated posts, including your own. **More sophisticated method!** Instead of using the Spam Link Deterrent, install and configure the [Nofollow List module](http://drupal.org/project/nofollowlist). This allows you to block certain sites so that they have nofollow automatically applied. My preferred approach is to apply nofollow to all domains, and keep a whitelist of sites that are exampt from this. [Instructions on configuring Nofollow List](http://gerardmcgarry.com/2009/nofollow-list-an-alternative-to-drupals-spam-link-deterrent/). Either method will give you the added peace of mind of knowing that _even if_ spammers are dropping links on your site, they're not getting any search engine benefit from their nefarious activities.

9) Speed it up for better crawling
----------------------------------

Yes, there's a current school of thought that suggests Google now [favours sites that load quickly](http://mashable.com/2009/11/15/google-ranking-speed/). Even if Google's plans to factor in page load times aren't there yet, faster page loads are good for your users anyway. So, install the Boost module for static page caching, and enable features in Drupal like CSS aggregation to ensure your site serves pages as fast as possible.

What others say:
----------------

The are different schools of thought as to what works for a Drupal site and what doesn't. Some people suggest using the Page Title module, others recommend the Search 404 module as part of an SEO strategy. There are recommendations for tools like Alinks or Glossify to create automatic backlinks within your site.

.htaccess tweaks
----------------

One technique which I think you _should_ try is making sure your site is only available at either yoursite.com or www.yoursite.com. It kind of ties int o the techniques for canonical URLs we talked about in the Global Redirect section. If your site is available with _and_ without the "www" prefix, you have potential duplicate content issues _and_ you could be diluting the value of your inbound links. Some people may link to the www version and some to the version _without_ it. First, check if your site is available at both addresses. If it is, find the .htaccess file at the root of your Drupal site and edit it. Scroll to the section that contains the rewrite rules and you'll find sample code to redirect to the URL of your choosing. Read the instructions and uncomment the code of your choice, replacing the domain details with the domain of your site. One word of warning - if you make changes to your .htaccess and/or robots.txt files, you have to be careful not to overwrite them when you upgrade your Drupal installation. When I download a Drupal upgrade, I tend to remove these files from the package so that they don't overwrite the custom versions I've created.