---
title: 'iOS tip: Prevent font size scaling when device orientation changes'
date: Mon, 25 Nov 2013 09:57:21 +0000
draft: false
tags: [iOS, Mobile, Aside, Responsive Design, Web Design]
---

I've been messing around with mobile design this weekend. And among some of the mind-bending media queries and  cross device checking, I noticed that when I changed from portrait to landscape orientation on my iPhone, the font size seemed to scale up, upsetting the design. After Googling around, as you do, I discovered a quick fix for this. It's probably something that most mobile/responsive designers include as a matter of course these days, but simply adding this Webkit-specific line to your stylesheet fixes the awkward scaling issue when you rotate your phone screen:

    body {
    	-webkit-text-size-adjust: none;
    }

Add the above to your existing body rules, and it'll clear up orientation change weirdness. Any other mobile design tips and tricks you want to share? Leave me a comment.