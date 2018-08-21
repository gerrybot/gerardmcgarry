---
title: 'Ubuntu 12.10: How to remove the Amazon shopping lens from Unity'
date: Mon, 22 Oct 2012 10:24:17 +0000
draft: false
tags: [Amazon, Linux, Tutorials, Ubuntu, Unity]
---

![Ubuntu Logo](http://gerard.files.wordpress.com/2012/10/ubuntu-logo.png "Ubuntu Logo")Canonical's decision to add an Amazon shopping lens to the latest version of **Ubuntu** 12.10, Quantal Quetzal has been hugely controversial. On one hand it brings an additional (and possibly very lucrative) revenue stream to the maker of the largest Linux distribution (which I support), but on the other, users are concerned for their privacy. Me, I just find the Amazon Shopping Lens a massive pain in the rear end. Luckily, there are a couple of ways you can disable the intrusive Amazon search results. The usability-destroying juggernaut approach is to _switch off all web search results_ in your privacy settings. Unfortunately, this has the unwanted side-effect of stopping useful web searches like YouTube videos, etc, from showing up. But still, if you want an all or nothing solution, this is the one for you.

Removing the Amazon lense from Unity
------------------------------------

The daintier alternative is to uninstall the Amazon shopping lens itself. What? You didn't know that was possible? Well it is. And it's as simple as an _apt-get_ command. Here's the code to run: `sudo apt-get remove unity-shopping-lens` To complete this, you need to log out of your user session and back in again, and Unity searches should show the contents of your computer and not the world's largest online retailer.

The clumsier alternative...
---------------------------

I mentioned above that you could also kill off Amazon results by hosing online searches in your Privacy settings. Simply call up the **Privacy** app (you can get there through your **System Settings** panel). In the Search Results tab, you should see a line that reads "When searching in the Dash: Include online search results". There's a little slider to switch that option off. Warning: The downside is that this will kill off all web content - Wikipedia searches, YouTube results, whatever other online results you are used to seeing in the dash. However, you can as always use a web browser to search for this content if you like. It's entirely up to you.

Is anyone a fan of the shopping lens
------------------------------------

I've got to ask this - does anyone out there need or want the shopping lens in Ubuntu? I'm not a regular shopper, and I use my machine more for research and writing than pricing goods and making online purchases, so having a series of Amazon results is actually genuinely annoying for me. But have any of you found it useful so far?