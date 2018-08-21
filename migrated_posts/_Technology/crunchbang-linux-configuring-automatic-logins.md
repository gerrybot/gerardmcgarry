---
title: 'Crunchbang Linux: Configuring automatic logins'
date: Sat, 22 Oct 2011 12:33:17 +0000
draft: false
tags: [Crunchbang, Linux, Tutorials]
---

[![Tux, the Linux mascot](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot-300x222.jpg "Tux, the Linux mascot")](http://interwebworld.co.uk/wp-content/uploads/2011/10/tux-linux-mascot.jpg)If you read my previous post about [building a headless Crunchbang Linux](http://interwebworld.co.uk/2011/10/21/how-to-install-and-configure-remote-desktop-in-crunchbang-linux/ "How to install and configure remote desktop in Crunchbang Linux") machine, you'll understand that one of the next steps for us is to have the machine log in automatically. Without an automatic login, the Vino server won't have the chance to start and therefore you won't be able to control the machine remotely. The good news is that configuring automatic logins in [Crunchbang](http://crunchbanglinux.org) is remarkably easy.

Step by step: Configuring automatic logins
------------------------------------------

1.  Right-click anywhere on your Crunchbang desktop and browse to the **System** menu. Click on **GDM Login Set-up**. You'll be prompted for your administration password to make these changes.
2.  Now, when the **Login Window Preferences** window appears, click on the **Security** tab and select **Enable automatic login**. You need to use the drop-down box to select the user account to log in when the computer starts.
3.  Save your settings and reboot the computer. It should log in automatically first time.

And that's it. In our next tutorial, we'll be looking at making applications start automatically when the Crunchbang computer starts up.