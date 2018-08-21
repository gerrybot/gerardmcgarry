---
title: 'Linux: Using the find utility with -regex to delete files'
date: Mon, 22 Aug 2011 15:23:23 +0000
draft: false
tags: [Linux, Regular expressions, Technology, Tutorials, WordPress]
---

Something I'm going to share with you today is how to delete a batch of files in Linux (a CentOS distribution in this instance) using the built-in **find** utility and some regular expressions. **Use case**: It turns out that the backup utility for WordPress doesn't delete old backups that it stores on your server. As these files build up, they typically consume a lot of space, and eventually fill up your hard disk. I like to keep a few historical backups just in case, so what I wanted to do was delete all the old backups _except_ the 1st and 15th of each month. That gives me a good historical trail of backups at intervals of roughly a fortnight per backup.

The find -regex command
-----------------------

Enter the find utility. It has a built-in regex function which allows you to find patterns within filenames. Here's the command that I use:

    find -regex '.*/filename.*2011(0[1-9]|1[012])(0[2-9]|1[0-4]|1[6-9]|2[0-9]|3[01]).*.sql'

The logic here is that each backup file is named "filename\_yyyymmdd\_xxx.sql" where y, m and d stand for year month and day and the xxx is a timestamp of sorts. What I've done here is to hard code in the year, then enter regular expressions for the month and day. When using the brackets () and pipe | characters, you have to be careful to escape them with a backslash for this to work. Test this command against your WordPress backup directory until the output matches what you expect to delete. When you're ready to delete the old backup files, simply add "-delete" to the end of the command and your files will be deleted. It should look something like this:

    find -regex '.*/filename.*2011(0[1-9]|1[012])(0[2-9]|1[0-4]|1[6-9]|2[0-9]|3[01]).*.sql' -delete

Limitations and Ideas for improving this technique
--------------------------------------------------

1.  This isn't an elegant solution by any stretch of the imagination. Ideally, I'd like to skip the last thirty days' worth of backups and then delete from there. This would give a selection of current backups, plus the fortnightly archive.
2.  The regex code itself could probably do with being cleaned up. It would be cleaner to say "delete every file that _wasn't_ created on the 1st or 15th of the month". Unfortunately, my RegEx skills aren't sharp enough for that!
3.  Bundling the solution into either a script file for use in a cron job or a WordPress plugin for managing rotation of backup files would be especially sexy. Set your backup retention policy and let cron manage the rest.

If you can help with any of those, leave me a comment!