---
title: 'Linux tip: How to delete files older than x number of days'
date: Fri, 27 Apr 2012 12:11:29 +0000
draft: false
tags: [Linux, Tutorials, Ubuntu, WordPress]
---

Looking for a quick way to delete old files in Linux? For example, log files can build up over a long period of time. **Usage case**: The default WordPress backup tool doesn't delete old backup files. So, over time, these files can accumulate and take up valuable disk space. If you run a large and busy site, this can become a problem. So, in order to maintain a healthy file system, we'll want to keep say the last 30 days' worth of backups and discard anything older than that. Of course, this technique will work equally well in any directory that contains log files. Here's the code - I'll explain what we're doing below: `find /path/to/folder -name '*.sql' -mtime +30 -delete`

1.  Okay, the `find` command is built right in to Linux. We're using it to locate - then delete - files that match the date criteria.
2.  /path/to/folder - Make this to the path to the log file directory you want to delete files from. We restrict this to a particular folder so that we're not running the command right across the file system - that would be _bad_!
3.  We're using the `-name '*.sql'` to restrict the command to _only_ the backup files that end with .sql. As with the previous point, this is a precautionary measure so that we don't delete _all_ files.
4.  The `-mtime` switch allows us to specify files older than a certain date. In this instance, we want everything older than 30 days.
5.  Finally, the `-delete` switch tells the command to delete all the files that meet the criteria we specified. If you want to see what files _will_ be deleted, run this command without `-delete` and you'll be given a list of files.

**Note:** This command works perfectly on Ubuntu. I can't vouch for other Linux distributions as all distros vary slightly. As always, try this out on a sample set of data before doing it on something critical - and use restrictions intelligently to avoid deleting more data than you intended to!