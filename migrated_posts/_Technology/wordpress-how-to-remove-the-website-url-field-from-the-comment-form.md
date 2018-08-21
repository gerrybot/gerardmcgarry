---
title: 'WordPress: How to remove the Website URL field from the comment form'
date: Fri, 19 Aug 2011 16:41:22 +0000
draft: false
tags: [Technology, Themes, Web Design, WordPress]
---

[![WordPress logo](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)As a blogger, the URL field in the WordPress comments form is a constant pain - either spammers are using it to drop shady links, or readers feel compelled to fill it with garbage just to fill in the field. Either way, it's a nuisance. But how do you get rid of it? Well, I spent a long time searching for the solution to this problem last night, and I've written up a solution for removing the URL field that takes into account a number of different scenarios you might encounter! Obligatory warning! Never apply these types of changes to a production site - I keep a copy of my [website themes on a testing server](http://gerardmcgarry.com/2008/xampp-for-windows-lamp-development/) and make changes there. I suggest you do the same! 

Before we begin
---------------

Most of the changes we'll be making will be in your WordPress theme. In my experience, there are a few different scenarios that we need to be aware of:

### 1\. Your WordPress theme doesn't have a comments.php file

If your WordPress theme is missing the comments.php file, WordPress will use the default template, located in /wp-includes/theme-compat/comments.php. This is all well and fine, but the fix detailed below requires the comments.php file to exist in the theme directory. To overcome this, copy the comments.php file from the folder above into your theme folder. Once you've done this, follow the next step:

### 2\. Your WordPress theme has the comment fields inserted manually

Most modern themes will use the <?php comment_form(); ?> code snippet at the bottom of the comments.php file. If this isn't present in your comments.php file, then you should look for a line of HTML/PHP code that refers to a 'URL' field. Simply delete that line and your WordPress comments form should now be missing the website field! In this scenario, you don't need to progress to the more advanced solution detailed below - you're all done!

### 3\. Your theme's comments.php calls comment_form()

OK - so your comments.php file contains: <?php comment_form(); ?> And comments.php is located inside your theme directory? You've come to the right place! Step this way...

Remove the Website URL field
----------------------------

OK, open up your theme's functions.php file and add the following code to the end of the file:

    
    add_filter('comment_form_default_fields', 'url_filtered');
    function url_filtered($fields)
    {
      if(isset($fields['url']))
       unset($fields['url']);
      return $fields;
    }

This code snippet is from TechHacking (link now dead). However, they talk about implementing it as a plugin. It's easier if you just add the code to functions.php in your theme. Now, refresh your blog pages and the URL field should be missing from the comment form. (**Aside**: if the changes don't appear right away, make sure you're not running a caching plugin, and if you are, be sure to flush the cache!)