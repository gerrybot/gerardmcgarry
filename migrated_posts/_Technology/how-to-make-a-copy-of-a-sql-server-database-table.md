---
title: 'How To: Make A Copy Of A SQL Server Database Table'
date: Tue, 13 May 2008 22:41:06 +0000
draft: false
tags: [On Web Design, Web Design]
---

I’ve been working on a couple of projects recently where I’ve had to retain legacy databases and integrate them into new websites. In order to do this without damaging the original tables, I find it useful to make a copy of the original database table and use _that_ for the development work. Since I do all of my bespoke CMS development on hosted Microsoft SQL Server databases, I had to hunt down a quick method to copy an existing database table into a new one. Let’s say we have an old table (`oldnews`) containing news items for a website. The structure is generally sound, but we don’t want to risk any damage to the original table. The following syntax copies the data from `oldnews` to the new table `newnews`:

    INSERT INTO newnews SELECT * FROM oldnews

Apparently, this will also copy data into an existing table, so if `newnews` already exists the data will be placed there. If the table doesn’t already exist, it will be created. At least, that’s how it worked for me! You can even copy table data from a different (local?) database by specifying the full database path:

    INSERT INTO newnews SELECT * FROM olddb.dbo.oldnews

If you’ve got any more insight into table copying techniques, drop your wisdom in the comments!