---
title: 'Drupal question: Moderating content from new users on a site'
date: Wed, 17 Nov 2010 18:01:10 +0000
draft: false
tags: [Communities, Drupal, Spam, Technology]
---

[![Drupal Logo](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/01/drupal-logo.jpg)A question for Drupallers who manage community sites where members can post content: **Is there a way to hold the first few posts from a new member for moderation until they've earned trust in the community?**

Why I'm Asking
--------------

We had a massive spam attack on [Unreality Shout](http://unrealityshout.com) this past weekend. A handful of malicious users generated hundreds of nodes of spam in a very short space of time. Shout is an entertainment community where members can come along and blog news and reviews, participate in forum discussions, etc. But we get an awful lot of spam, which is incredibly frustrating. Much of it is profile spam, but a fair proportion is people coming onboard to write link-stuffed blog posts. I want to snuff this out because it's damaging to the community and potentially damaging to the site if Google decides we're a spam dump.

What I Want To Do
-----------------

I want to hold content from new members for moderation. And I want it to be a largely automatic process. Let's say you have less than 6 posts on the site. Well, I want to queue your blog posts for approval before I let them through. Once you've got more than six (approved) posts, you've earned our trust and can post freely from that point forward. So, the big question is - **how do I achieve this type of moderation?**

*   **Can it be done natively** through Drupal's roles - ie. moving an author from a regular "authenticated user" role to an "Approved Author" role?
*   **Contributed modules**? Can an approval process be achieved through [Rules](http://drupal.org/project/rules), [Workflow](http://drupal.org/project/workflow), [Userpoints](http://drupal.org/project/userpoints) (as a mark of trust/authority) or something else?
*   Is there a way to **notify the user** that their post is held for moderation and the site admin know that there is content in the queue?
*   **Custom module?** Is it necessary to build a custom module for this kind of functionality?

I'll leave the post with that information. I'd really like to spark a discussion around this topic, because I've tried a number of measures - like activating Mollom to protect blog entry nodes (didn't work). Currently I've set the community to invite-only mode, but I'd like to open it up to the public again. How have others handled this issue - Drupal sites like Examiner.com and NowPublic that encourage submissions from the public? I'd love to hear your suggestions...