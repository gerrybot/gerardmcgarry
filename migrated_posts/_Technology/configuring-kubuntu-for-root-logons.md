---
title: 'Configuring Kubuntu For Root Logons'
date: Tue, 13 May 2008 22:31:41 +0000
draft: false
tags: [Kubuntu, Linux, Technology, Tips]
---

[Kubuntu Linux](http://www.kubuntu.org) has the `root` account disabled by default for security purposes. Users are encouraged to use the `sudo` command as an alternative whenever root-level priviledges are needed.

Now, maybe I’m too old-skool, but that’s just plain irritating. Here's how to enable root logons in Kubuntu.

Edit the kdmrc file
-------------------

The first thing you need to do to enable root logons in Kubuntu is to modify the `/etc/kde3/kdm/kdmrc` file. However, to change this file - guess what? - you need root access! Here’s how to do it:

1.  Press **alt+F2** to call up the Run Command. Type in `/etc/kde3/kdm` to call up the `kdm` folder in Konqueror.
2.  When the folder opens, you should see a file called `kdmrc`. Right-click it and select **Actions**, **Edit As Root**. You’ll be prompted for the root password (which should be your own password)
3.  The file should open up in a text editor (**KWrite** on my installation). Broswe for the line `AllowRootLogin=false` and change false to true. Save the file and close it.

Enabling Root Logins (Modifying the Root User Account)
------------------------------------------------------

The second step here is to actually enable the root account for login, because it is disabled by default. There may be a quicker, more _linux_ way to do this, but this is my method:

1.  Press **alt+F2** to call up the Run Command. Type in `kuser` to start up the KDE User Manager.
2.  Double-click on the `root` entry to bring up the account properties and _uncheck_ the **Account Disabled** checkbox. Click **OK** to save the changes.
3.  Exit the KDE User Manager.

And that’s it! If you log off, you should now be able to login to Kubuntu as root.

Why Enable Root Logins?
-----------------------

Yes, I know that in an ideal world I would use `sudo`. Why did I absolutely require root access? Well…

1.  I don’t know Linux very well. I can hold my own, but I don’t speak the command-line-lingo like the pros.
2.  Elements of the GUI in Kubuntu don’t work so well. In particular, the [network configuration utility ‘forgets’ the default gateway](http://ubuntuforums.org/showpost.php?s=daa225f2f0f013f25d3ed5a3d9fe9dfc&p=669072&postcount=3) entry.
3.  Some graphical tools also have an **Administrator Mode** button. I found in some instances that this didn’t work. You would type in credentials and it would return you to the same greyed-out screen, indicating that authentication had been rejected. Very frustrating.
4.  Being fairly unfamiliar with Linux, I didn’t know the command equivalent for these graphical functions, so I couldn’t very well `sudo` them, could I?

If anybody reading this has any links to good newbie linux resources, let me know!!!