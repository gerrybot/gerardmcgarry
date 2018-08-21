---
title: 'WordPress Tip: How to reduce the size of your wp-shortstat database'
date: Thu, 06 Nov 2008 14:38:57 +0000
draft: false
tags: [Technology, Web Design, WordPress]
---

[![WordPress logo](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)I use the [wp-shortstat plugin](http://blog.happyarts.de/wp-shortstat/) across all my WordPress blogs to track visitors and show me where my visitors are coming from. However, Shortstat has its problems – it logs everything, resulting in a massive database size on your server. The more popular your site, the more this lumbering beast of a database slows things down. In fact, in one instance, the database grew so large that Shortstat couldn’t display the stats anymore. So, I came across this post today showing you [how to remove old entries](http://perishablepress.com/press/2008/01/01/reduce-the-size-of-the-wp-shortstat-database-table/) from the Shortstat database. It involves going into your phpMyAdmin and running the following SQL query:

    DELETE FROM `wp_ss_stats` ORDER BY `id` ASC LIMIT n

Now, the above query implements a limit on the number of records that will be deleted. You replace the ‘n’ with the number of records you want to remove, and it’ll remove them from the start of the table, keeping the most recent entries. I’m going to suggest a slight improvement to this idea though. What if you only wanted to keep the last two months worth of records? Well, we can modify the query to achieve that goal. Let’s say we want to delete everything logged before 1 October 2008.

1.  The first thing you need to do is establish the PHP timestamp for the date in question. Can’t calculate this in your head? Try [this nifty converter](http://www.4webhelp.net/us/timestamp.php), and you’ll discover that midnight on 1 October 2008 equates to ‘1222819200’.
2.  Next, fire up your phpMyAdmin and get ready. Have you taken a backup of your database? If not, you might want to break now to back your database up in case you screw this up!
3.  OK, browse to your database, and you should see a table named “wp\_ss\_stats”. This holds all your stats data. I normally browse to this table and hit the SQL tab along the top to get the query editor up.
4.  Now, type in your query, which is
    
        DELETE FROM `wp_ss_stats` WHERE dt < 1222819200
    
5.  Execute the query. If your table is particularly large, you might want to consider deleting in smaller chunks by adding “LIMIT 5000” to the end of your statement and executing this several times. I’ve crashed my DB server running this on a large number of records in the past.

Purging your Shortstat tables in this way every month or so helps keep the database bloat down and at least wp-shortstat will perform a little bit better. One of our database tables was 690MB in size and contained over 4 million records. After running this script, we removed over 2 million records and brought the table size down to 319MB. Still large, but a bit more manageable.