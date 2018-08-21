---
title: 'Drupal: How to increase the default font size in TinyMCE'
date: Fri, 05 Dec 2008 14:34:13 +0000
draft: false
tags: [Drupal, Technology, TinyMCE, Tutorials, Web Design]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)If you've ever installed the [TinyMCE module](http://drupal.org/project/tinymce) for [Drupal](http://drupal.org) (or indeed the [WYSIWYG module](http://drupal.org/project/tinymce) which seems to be the preferred way forward), you'll have noticed that the default font size is miniscule. My first concern as a web designer is usability. How hard is it to read and edit?

How to make the default font bigger:
------------------------------------

Right, I'm going to do this using WYSIWYG module, but it's _almost exactly the same_ using the TinyMCE module.

1.  Create a CSS file in your theme's folder. I called mine tinymce.css for obvious reasons.
2.  Go to yoursite.com/admin/settings/wysiwyg and edit the profile for the input type of your choice.
3.  Go to the CSS section of the TinyMCE profile and expand it. Switch the **Editor CSS** dropdown to **Define CSS** and then fill in **CSS Path** with the path to where you saved your CSS file. You can enter this manually, or you can use shorthand to point to your theme folder - like this: %b%t/tinymce.css
4.  Save your settings

What you've achieved up to this point is you've linked a new, blank CSS file to the TinyMCE editor. What you need to do now is add some CSS to alter the appearance.

A quick warning about file caching!
-----------------------------------

Whatever way the editor works, it doesn't refresh the CSS on a page refresh. I found the easiet way to force a refresh was to type the URL to the stylesheet directly into another browser window and refresh it manually before refreshing the page. It's crude, but it works.

Editing the CSS file
--------------------

Right, so open up the tinymce.css file in your favourite editor (Dreamweaver/Notepad/Aptana/whatever...) I didn't make any radical edits - just the following resulted in a decent, readable font in the editor:

body.mceContentBody {
    font-size:0.8em;
    background-color:#fff;
    padding:5px;
    line-height:135%;
    }

The class "mceContentBody" is what each instance of TinyMCE uses to identify itself, so theming based on that is a good starting point. You can do other things too - if your theme has custom classes, you can mirror the behaviour of them in TinyMCE so they give an approximation of how they'll display. The most obvious thing I'm thinking of is image alignment classes like img.left and img.right. I've checked this in IE7 and FireFox 3 and it seems to work just fine. I'd imagine that it'll be good for most modern browsers. Hopefully this'll help a few other people out there who've been having the same problem with Drupal and TinyMCE.