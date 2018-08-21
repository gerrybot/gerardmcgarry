---
title: 'What version of Ubuntu am I using?'
date: Sat, 25 Apr 2009 23:04:51 +0000
draft: false
tags: [Linux, Technology, Tutorials, Ubuntu]
---

Because Ubuntu is a free operating system, they don't feel the need to shove the version in your face in quite the same way their commercial counterparts do. So, when you're on the threshold of doing an upgrade, it's nice to know what version you're upgrading from.

There's a quick, command based way to discover what version of Ubuntu you're using:

    cat /etc/issue

Alternatively, for a more detailed output, try this command:

    cat /etc/lsb-release

This will return the version of Ubuntu that you're currently using. I used it prior to upgrading, and also after the upgrade to verify that everything had been successful.