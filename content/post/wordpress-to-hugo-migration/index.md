---
title: "Wordpress to Hugo Migration"
date: 2018-08-10T17:18:52+01:00
draft: true
---

Steps to migrating from WordPress to Hugo

1. Use the export tool on WordPress to generate an XML file for the site.
2. Use the [Blog2md tool](https://github.com/palaniraja/blog2md) to convert your export into individual .md files for each post
3. Generate a Hugo site in your dev environment and copy in the exported .md files to your content area. This takes some planning for the type of site you want to create and if you want to replicate the structure of the old site
4. Add a theme to your Hugo site

#todo

1. Move domain to another provider - Google Domains?
2. Set up domain email to go to Gmail/G Suite account
