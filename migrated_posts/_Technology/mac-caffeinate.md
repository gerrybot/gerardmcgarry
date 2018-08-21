---
title: 'Stop your MacBook from sleeping with the Caffeinate command'
date: Thu, 13 Feb 2014 13:09:31 +0000
draft: false
tags: [Apple, Microsoft, Technology]
---

A frequent bugbear with OS X on my MacBook Pro is that the screen will dim and then sleep if I leave it unattended for any length of time. That's a nuisance because I can be running FTP operations or SSH sessions that I need to keep active and OS X will just go to sleep in the middle of them.

Enter caffeinate...
-------------------

Caffeinate is a command line tool that allows you to prevent your Mac from going to sleep when it's 'idle'. You can run the command in its purest form (without parameters) and it'll keep your computer awake until you get back. Alternatively, you can specify a time limit in seconds to caffeinate for. Try this: caffeinate -t 600 That command will keep your idle MacBook awake for 10 minutes. You can experiment with other timeout values to find whatever suits.

Advanced options
----------------

Caffeinate has other cool options. For instance, if you have a batch operation to process, you can run caffeinate along with your command - and this will keep your computer awake until the task completes. For example: caffeinate ./batch-script-to-process.sh You can add other options to the command:

*   `-d` — Prevent the display from sleeping.
*   `-i` — Prevent the system from idle sleeping.
*   `-s` — Prevent the system from sleeping. This is valid only when system is running on AC power.
*   `-u` — Declare that a user is active. If the display is off, this option turns the display on and prevents the display from going into idle sleep.