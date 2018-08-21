---
title: 'WordPress tip: Split up long posts into multiple pages'
date: Sat, 30 Nov 2013 16:12:56 +0000
draft: false
tags: [Web Design, WordPress]
---

![WordPress logo](http://interwebworld.co.uk/wp-content/uploads/2013/09/wordpress-300x214.png)Many professional web publishers will opt to split up long posts into multiple pages: it breaks the article down into digestible chunks and also has the added benefit of reducing your site's bounce rate and keeping readers on your site for longer. (Reducing the bounce rate of your website sends positive signals back to Google about the usefulness of your content.) [WordPress](http://wordpress.org/) has a neat, in-built method of splitting up your posts. You won't need a separate plugin for this, but you _will _need to make sure your theme has the [wp\_link\_pages()](http://codex.wordpress.org/Template_Tags/wp_link_pages) function in the single post template. Most good-quality modern themes will have this in place, but you may have to add it for others.

Splitting up your posts
-----------------------

This bit's done quite simply. In the post editor window, you simply insert the code comment `<!--nextpage-->`. You can do this as many times as you like. Some websites split their posts up for each point on a "Top 10" style list. Others will maybe break posts directly in half. Basically use it to suit your requirements. But be warned: overuse can turn some readers off, because it requires them to have successive pageloads, so it can get annoying. Now that you've done this, publish or preview your post. When you view the post, you should see a series of links at the bottom of your post, allowing you to browse between the different pages of your article. If you can't see this in your theme, you need to read on to the next section...

Implementing wp\_link\_pages
----------------------------

If you can't see the pagination links at the bottom of your post, then your theme probably is missing the [wp\_link\_pages() function](http://codex.wordpress.org/Template_Tags/wp_link_pages) from the single.php template. There are many different ways to style the output from this function, but the default settings are usually just fine. To quickly get this working, open up your WordPress website's single.php theme file and add the wp\_link\_pages() function directly after the wp_content() one. The end result should look like this:

    <?php the_content(); ?>
    <?php wp_link_pages(); ?>

Save your page's code and upload to the website, and your multi-page posts should now have the proper links underneath them to allow you to browse between sections. A really useful feature, especially if you publish lots of long-form content.