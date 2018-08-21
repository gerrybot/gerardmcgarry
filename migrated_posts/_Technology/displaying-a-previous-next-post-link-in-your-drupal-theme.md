---
title: 'Displaying a previous - next post link in your Drupal theme'
date: Mon, 19 Apr 2010 16:37:07 +0000
draft: false
tags: [CSS, Drupal, Technology, Web Design]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)If you're a convert to Drupal from a blogging platform like WordPress, you might miss the Previous/Next post links that allow visitors to read through the posts on your site in a chronological manner. I've been searching for a solution to this for a while, but nothing I've found on Drupal.org has offered an acceptable solution for me. What I'm going to show you here is some code I've put together that retrieves the next and previous posts from the database and displays them for the user. If you are a Drupal guru and have suggestions for how to refine this, _please share your knowledge in the comments_.

Step 1: Mining The Database!
----------------------------

Before we get to the presentational aspects of the code, we need to find out what "nodes" come immediately before and after our post. Here's the line of SQL code I'm using to extract the information: `SELECT nid, title FROM {node} WHERE nid < %d AND type = '%s' AND status = 1 ORDER BY nid DESC LIMIT 1` **Explanation:** This line retrieves the node _before_ the current one. The "type = '%s'" allows this to _only_ select from the same node type. This is useful if you have several different content types on your site, and you only want the script to select from the same _type_ of content. The "status" portion ensures only published nodes are shown, and the "limit" ensures that only one record is selected.

Step 2: Editing template.php
----------------------------

Jumping swiftly along, here's the code I added to my template.php file. `function yourtheme_prevnext($nid,$ntype) { //This selects the previous record and builds it into an HTML string using the Drupal "l" function to build the link $result = db_query("SELECT nid, title FROM {node} WHERE nid < %d AND type = '%s' AND status = 1 ORDER BY nid DESC LIMIT 1",$nid,$ntype); while ($row = db_fetch_array($result)) { $outputstring .= "`

« " . l(t($row\[title\]),"node/".$row\[nid\], array(attributes => array('title'=> t($row\[title\])))) . "

"; } //This selects the next record and builds it into an HTML string as in the previous example $result = db\_query("SELECT nid, title FROM {node} WHERE nid > %d AND type = '%s' AND status = 1 ORDER BY nid ASC LIMIT 1",$nid,$ntype); while ($row = db\_fetch_array($result)) { //Finally, we wrap the output in a containing DIV element for themeing purposes $outputstring .= "

" . l(t($row\[title\]),"node/".$row\[nid\], array(attributes => array('title'=> t($row\[title\])))) . " »

"; } $outputstring = "

" . $outputstring . "

"; print $outputstring; } This selects the previous and next records from the database and wraps them up in HTML. We use the Drupal `l()` function to create the links in the correct way.

Step 3: Call the function from node.tpl.php
-------------------------------------------

OK, in order to get the HTML to display, you have to edit your `node.tpl.php` file. In the code snippet below, I'm going to call the code directly, but in reality, I only display this code when you're looking at the full node, not the teaser view you might see in a category list. `nid,$node->type); ?>` The code to only display prevnext on full nodes is below `nid,$node->type);} ?>`

Step 4: Add some styling to your CSS file
-----------------------------------------

Now, in order to make it look good, add some code to your stylesheet. I'll give you an example of what I used in my sandbox, but you may need to tweak it for your theme. `/* Post Navigation */ .post-navigation {font-size:12.5px;} .prevpost {float:left;width:48%;text-align:left;} .nextpost {float:right;width:48%; text-align:right;}`

### Your feedback

OK, I've shown you my code. I don't know if anybody else has attempted this, but I'm happy to see other solutions or suggestions for how the code may be improved for this theme. Please share!