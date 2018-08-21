---
title: 'WordPress: How to use MySQL to replace the URL in your posts'
date: Sun, 08 Aug 2010 19:21:19 +0000
draft: false
tags: [Databases, MySQL, Technology, Tutorials, WordPress]
---

[![WordPress logo](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)If you've ever moved your WordPress site to another location, you'll find that all your images end up broken because they all point to the old domain. The problem is, all the image paths stored in the database are static, so you've got to update them to the new location. **Usage case**: My usage case is that I'm moving an old WordPress site to my local computer to use as a sandbox for theme design. So all the references to myolddomain.com need to be changed to localhost/sandbox (the directory on the server that my WordPress installation is on). **Caveats**: What I'm about to show you will not only update the image paths, but it'll also update the internal links on the site. As long as your permalinks setup is the same as before, everything should be fine! **Tools**: This procedure can be easily carried out using either PHPMyAdmin if you've got it installed. You can also use a simple MySQL command line prompt if you're familiar with that.

Find and replace text using MySQL
---------------------------------

OK. The WordPress posts table is called **wp_posts**. So, make sure you're operating on the correct WordPress database, etc, etc, and let's get started. We do this using a simple SQL UPDATE statement and the **replace()** function, which will do all the heavy lifting. And we simply replace the domain information rather than the entire URL string. Here's the syntax: `replace(POST_CONTENT,'myolddomain.com','localhost/sandbox')` POST_CONTENT is the field we want to operate on. 'myolddomain.com' is the text we want to look for, and 'localhost/sandbox' is what we want to replace it with. Change these values to suit your own case.

### The SQL statement in full

`UPDATE wp_posts SET POST_CONTENT = replace(POST_CONTENT, 'myolddomain.com', 'localhost/sandbox');` Once you execute the statement above, fire up your site in a browser, and you should find that where images were broken before, they're all fixed now. Oh, and naturally, you should have your database all backed up before you do anything like this at all.