---
title: 'Creating a custom Firefox search that Googles all subdomains in a site'
date: Tue, 03 Mar 2009 19:19:20 +0000
draft: false
tags: [Firefox, Technology, Web Design]
---

[![Firefox Logo](http://gerard.interwebworld.co.uk/files/2009/08/firefox-e1379623063857.jpg)](http://gerard.interwebworld.co.uk/files/2009/08/firefox-e1379623063857.jpg)Here's a quickie Firefox hack - there may be quicker ways of doing this, but this is pretty nifty all the same. Let me explain why I needed to search across all subdomains: on [Unreality TV](http://www.unrealitytv.co.uk "Unreality TV: The Reality TV blog"), we have a handful of subdomains, each containing its own installation of WordPress. Now, when I'm writing about a topic for the music blog, I might want to see what else we've written with regard to that person or band or celebrity. Now, I could simply do a Google search and include "Unreality" as a keyword, which works fairly well. Lately though, I've taken to using an advanced search feature - the **site:** operator. Typing **"search query" site:*.unrealitytv.co.uk** quickly retrieves posts from across the site that meet my query.

Adding the search to Firefox
----------------------------

So where does Firefox come in? Well, Firefox is my primary browser, and I use the search box extensively, I decided to see how easy it would be to add the domain search to the list of search engines. Here's what I did:

1.  Browse to **C:Program FilesMozilla Firefoxsearchplugins** and copy the **google.xml** file.
2.  Go to the start menu and bring up the **Run** dialog. Type in **%appdata%MozillaFirefoxProfilesdefault.somethingsearchplugins**. The default.something folder will have a random string of 3 letters instead of the word 'something'.
3.  Paste the **google.xml** file into this folder and rename it to something unique. The name of the site might be smart.
4.  Now, open the newly pasted file in your favourite text or web editor ([I use Aptana](/blog/my-mostly-free-web-design-toolkit)). We need to make some changes.
5.  First things first: change the values for **ShortName** and **Description** in the file to suit your search. They'll read Google and Google Search by default.
6.  Second, browse down to the line which reads **<Param name="q" value="{searchTerms}"/>**. After **{searchTerms}** add the following: "+site%3A*.yourdomain.com". The modified line should read: **<Param name="q" value="{searchTerms}+site%3A*.yourdomain.com****"/>**. If you didn't replace the word _yourdomain.com_ with your actual domain name, then this isn't going to work: go back and change that to the appropriate domain name.
7.  Save your changes, restart your browser, and you should have the new entry in your drop down menu (as seen below!).

[![FireFox custom domain search](http://gerard.interwebworld.co.uk/files/2009/03/domain-custom-search.jpg)](http://gerard.interwebworld.co.uk/files/2009/03/domain-custom-search.jpg)

Can you do it better?
---------------------

Well, that's how I accomplished the custom search in Firefox. As I said at the top, I'm sure there are many ways to do this. If you know of something more efficient, please drop me a line in the comments. **Update:** I've included an unreality.xml file in a zip file below. Download this, extract it and put the file in **%appdata%MozillaFirefoxProfilesdefault.somethingsearchplugins**. Restart your browser and it should just work. Hack it to suit your own site!