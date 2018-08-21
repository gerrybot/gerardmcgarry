---
title: 'Where does Microsoft Outlook store signature files?'
date: Wed, 30 Apr 2008 14:23:18 +0000
draft: false
tags: [Microsoft, Technology, Tips]
---

I was asked by someone today how they could get a well-formatted email signature like mine - you know, with the nice fonts, corporate logo and everything.

Well, I remembered going through a lot of pain trying to create my signature at the start. There had to be an easy way to distribute my signature as a template so that other people could customise it with their details.

After a bit of digging around, I discovered that Outlook 2003 stores signatures in `documents and settingsusernameapplication Datamicrosoftsignatures`. In my signatures folder, I found three versions of my standard signature - text-only, RTF and HTML. I was able to take these files and drop them into another user's signatures folder. (If the person doesn't have any previous signatures configured, you may have to create the signatures folder manually)

Now, go into Outlook 2003 and select Tools, Options, then go to the Mail Format tab. Click the **Signatures** button and you should see an entry for the signature you just copied across. You should then also be able to amend the details - change the name, DDI number and email address, etc - to suit the person you're creating the signature for.

From my experiments, any changes you make in the Edit Signature screen are automatically copied to the text, rich text and HTML versions of your signature.