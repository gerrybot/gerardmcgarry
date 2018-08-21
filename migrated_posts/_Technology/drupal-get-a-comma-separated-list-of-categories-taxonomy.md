---
title: 'Drupal: Get a comma-separated list of categories (taxonomy)'
date: Sat, 02 May 2009 09:56:12 +0000
draft: false
tags: [Drupal, Technology, Tutorials, Web Design]
---

[](http://drupal.org)[![Drupal logo](http://gerard.interwebworld.co.uk/files/2009/05/drupal.jpg)](http://gerard.interwebworld.co.uk/files/2009/05/drupal.jpg)Drupal's default way of displaying categories really bugs me. They compile all the categories into an unordered list, which adds a lot of pointless complexity to the theme. Coming from the WordPress school, I'd much prefer to have a comma-separated list of categories. Well, after an epic battle with my node.tpl.php file and much searching on the Interwebs, I've come up with a solution. It's based heavily on a code snippet used in [this Lullabot article](http://www.lullabot.com/articles/how_to_build_flickr_in_drupal). Essentially, what we need to do is parse through all the terms, [build a link](http://api.drupal.org/api/function/l/6) for each taxonomy term and then use the implode function to build the comma separated list. Here's a sample of the code I'm using:

    
    <?php
    	$term_links = array();
    	// "implode" makes the terms comma-separated
    	foreach ($node->taxonomy as $term) {
    		$term_links[] = l($term->name, 'taxonomy/term/' . $term->tid);
    	}
    	print implode(', ', $term_links);
    ?>
    

I'm currently using this directly in the node.tpl.php, but what I'd _really_ like to do is wrap this in a function and place it in the template.php file so that I can redistribute it with my theme when I make it available. And so that I can carry it across to other themes I might design. Any hints or tips along those lines would be greatly appreciated!