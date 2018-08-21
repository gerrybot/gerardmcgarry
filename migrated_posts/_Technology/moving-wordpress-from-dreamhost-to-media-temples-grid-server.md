---
title: 'Moving WordPress From Dreamhost To Media Temple’s Grid Server'
date: Tue, 13 May 2008 23:08:04 +0000
draft: false
tags: [On Web Design, Web Design]
---

[![WordPress logo](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)](http://gerard.interwebworld.co.uk/files/2011/08/wordpress-logo.jpg)I’m throwing in the towel with Dreamhost. The downtime problems that started in the summer and seem to be intermittently reappearing have caused me to completely lose hope in DreamHost. I signed up for a [Media Temple Grid Server](http://www.mediatemple.net/go/order/?refdom=familyoffive.co.uk) (affiliate link) account a few weeks back and have been gradually porting my blogs across one-by-one. With other people following suit, I thought I’d share my notes for moving a WordPress install over to Media Temple.  Naturally, this guide assumes that you have existing blogs on Dreamhost and a Grid Server account with Media Temple!

My Setup
--------

I’m running a WordPress 2.0.x install with a handful of plugins and a theme I designed myself. I’ll be backing up the WordPress database and files in advance of the move and shifting them to the new server. I also have a series of email addresses configured at Dreamhost, so I’ll want to have the equivalent addresses set up at Media Temple, ready for when the domain changes over. I sensibly registered my domains away from 1&1 Internet, which means I don’t have the hassle of registration transfers or transfer fees! Hooray for me! When I’ve got my data migrated, I’ll simply redirect the DNS to Media Temple et voila - minimal interruption!

Step 1: Backing Up
------------------

The first step is to make sure we’ve got all our data ready to move. **WordPress Files**: Fire up your FTP program of choice and download your entire WordPress `wp-content` directory. This is where all of your custom themes, image uploads and plugins reside, so take no chances. Download it separately. Once I downloaded the `wp-content` folder, I created a backup folder on my hard disk and downloaded the entire WordPress installation to it. I was glad I did, because there were some miscellaneous directories that I might have otherwise missed! **WordPress Database**: Since I run the 2.0.x version of WordPress, I have the luxury of Scott Merrill’s Database Backup plugin. Simply browse to your site’s `wp-admin` folder and select **Manage**, then **Backup**. The standard WordPress database tables will be backed up by default, but you should check the additional tables for backup, as these are usually related to some of your plugins. Set the backup plugin to download the file and then click Backup. Wait a few minutes and you’ll be prompted to save the file. Save it somewhere safe: you’ll need it later! A word of warning: tables for stats packages can get pretty big and cause the backup to fail. If you find this happening, consider leaving out those tables and reinstalling that plugin from scratch after you’ve moved. It means starting your stats again, but might be easier for the job in hand. Part of my migration plan is to install Google Analytics anyway, so it wasn’t a tough choice.

Step 2.1: Pre-Configuring Media Temple
--------------------------------------

OK, so we’re all backed up. Don’t close your Dreamhost account just yet! If all else goes wrong, you might need to reactivate it! Let’s get things over on Media Temple ready for the move:

1.  Log on to your Media Temple account.
2.  Click on **Domains**, then **Add New**. I selected **Add an Alternate Domain** and **Add DNS Zone**, but you may want to register or transfer a domain name. It’s important to create a DNS zone for the domain, so that Media Temple is ready to handle the service once the domain is transferred or registered.
3.  On the next page, select your Grid Service and the IP address to link it to (there’s usually only one). Click next to complete the process.

Step 2.2: Importing Your Database
---------------------------------

Now, lets set up the database:

1.  Go to the (mt) Domain List and select the primary domain (the first one you set the account up with). Click on the **Manage Databases** link.
2.  Click on the **Add New Database** link and give your database a name. (mt) will prefix it with your account code. Make sure that MySQL is selected as the database type.
3.  When you return to the database list, find the one you just created and click the **Admin** link to start phpMyAdmin.
4.  In phpMyAdmin, select your database from the drop-down and it will load. In the main window, click the **Import** button at the top of the page. Click **OK** to begin importing your WordPress database.
5.  That’s it! Your database is now ready - though it might be nice to let your commenters know that some comments might be lost in the transfer.

Step 2.3: Upload your WordPress Files
-------------------------------------

Now to upload our WordPress installation. Having the files in place means the blog will be ready to rock once you transfer the domain across. Remember to modify the `wp-config.php` file in your WordPress root folder to the settings of the **new** database!

1.  In fact, let’s do that now. Go to the **Manage Databases** page in Media Temple and take a note of the username, password, internal server address and database name, and change `wp-config.php` accordingly.
2.  Now, upload the entire WordPress installation you backed up earlier. Your account email from Media Temple has a youraccount.gridserver.com address that allows you to upload files before the domain has transferred. Simply log on to that, browse to `/domains/yourdomain/html` and upload everything. Take the time to ensure everything transferred successfully!

Step 3: Transfer Those Email Addresses
--------------------------------------

Now, let’s not forget those email addresses! We need to set those accounts up in advance to allow email to be delivered to them when the transfer takes place. Luckily, my I forward all my email to my Gmail account, so this should be easy!

1.  Go to the Media Temple Account Center, select your primary domain and then the **Email Aliases** link. Click **Add New Email Alias**.
2.  There’s a really neat trick that Media Temple does in enabling you to forward an address for all domains in your package. So, say you have an info@ address, if someone sends mail to info@ any of your domains, it’ll be forwarded. Makes it easy to standardise addresses across sites.
3.  Create the alias address, and select the domain you want it to apply to (or leave it set to all domains).
4.  Then you can choose up to three email addresses to forward the messages to. Set this whatever way you require.
5.  Set an optional autoresponder and save the record.
6.  Rinse and repeat for all addresses you need to transfer!

Now, because I set up forwarding, this worked very well for me. If you need a dedicated mailbox, use the **Email Users** facility instead of aliases.

Step 4: Showtime!
-----------------

Alright. Take a deep breath. Here we go. We’re going to modify the DNS of the domain to point to Media Temple. First, I’ll show you how to do this under 1&1 (my method) and then under Dreamhost. Here’s 1&1:

1.  Log on to the [1&1 Admin](http://admin.1and1.co.uk) panel. Click **Domains**.
2.  Select the domain you want to change and then **DNS**, **Edit DNS Settings**. Set the primary and secondary name servers to `ns1.mediatemple.net` and `ns2.mediatemple.net` respectively and save your changes.
3.  Wait patiently for DNS to propagate.

And under Dreamhost:

1.  Go to Dreamhost’s control panel and select **Manage Domains**. Find the domain you’re transferring and click **DNS**. The domain must be registered with Dreamhost though. In the nameservers area, enter `ns1.mediatemple.net` and `ns1.mediatemple.net` in the first two boxes and ensure the other nameserver entries are blank.
2.  Click the **Set these nameservers…** button and then wait patiently - you guessed it - for DNS to propagate…

Step 5: Test It!
----------------

There are a couple of things to test when you’re porting WordPress to a new server. Here are a few:

1.  URL Rewriting doesn’t seem to work out of the box. Go to `wp-admin` and then **Options**, **Permalinks**. Your permalink choice should be intact from before, so just click the **Update Permalink Structure** button and things should get sorted. The reason for this is probably because my FTP program didn’t backup the .htaccess file. Following the procedure above should recreate the .htaccess file as before.
2.  Send yourself an email (or get a friend to send one). Verify if it got redirected.
3.  Post a comment discreetly on your site and then check your new database in phpAdmin to see if it’s there. If it isn’t, chances are, DNS hasn’t transferred yet and your comment went to the old database.

**Final thought:** After doing another server move this weekend, I’d advise setting up the DNS zone on Media Temple at least a day in advance for it to be ready. So, it might be better to do that part of the job before you start taking your backups and everything else.