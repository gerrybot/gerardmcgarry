---
title: 'Perfecting Your WordPress Title Tags'
date: Tue, 13 May 2008 22:37:40 +0000
draft: false
tags: [On Blogging, Web Design]
---

[](http://www.wordpress.org)[![WordPress logo](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)WordPress‘ default theme (Kubrick) is great, but I’ve always had a problem with the title tags that the Kubrick theme generates. They could be so much more search engine friendly, don’t you think?

<title>
	<?php bloginfo('name'); ?> <?php if ( is\_single() ) { ?> &raquo; Blog Archive <?php } ?> <?php wp\_title(); ?>
</title>

This usually results in the title reading like **Interweb World » Perfecting WordPress Title Tags**, which is fine. But isn’t it better to serve the title tags with the title of the _article_ first? That’s the key information, not what website it came from. And that title tag is what’s going to be used in people’s browser favourites, search engine results and social bookmarking services ([del.icio.us](http://del.icio.us), [Digg](http://www.digg.com), [Stumbleupon](http://www.stumbleupon.com), etc).

Improving your Blog Titles
--------------------------

I’ve opted for a simple bit of code which you can see below. Basically, for the homepage (`is_home()`), we want to display the Blog Name and it’s description or strapline. Then, for every other page (category pages included), we want the **title** to show up first, _then_ the site name.

<title>
	<?php if (is_home()) { ?>

		<?php bloginfo(’name’); ?> &raquo; <?php bloginfo(’description’); ?>
	<?php } else { ?>
		<?php wp_title(”); ?> &raquo; <?php bloginfo(’name’); ?>

	<?php } ?>
</title>

Looking good. Test this out on your own blog and see how you get on.

Modifying Title Tags for UltimateTagWarrior
-------------------------------------------

If like me you use Christine Davis’ Ultimate Tag Warrior plugin for internal tagging, add the code below (just after the `is_home()` condition) and your tag pages will have the same effect.

	<?php } elseif (is_tag()) { ?>
		<?php UTW_ShowCurrentTagSet("", array(’first’=>’%tagdisplay%’, ‘default’=>’, %tagdisplay%’, ‘last’=>’ %operatortext% %tagdisplay%’)); ?> &raquo; <?php bloginfo(’name’); ?>