---
title: 'Creating A Google Sitemap For An ASP.NET Website'
date: Tue, 13 May 2008 23:02:55 +0000
draft: false
tags: [On Web Design, Web Design]
---

Any SEO worth his (or her) salt, knows that [Google Sitemaps](https://www.google.com/webmasters/sitemaps) are a great way to tell Google about the pages that are available on your site. Using a sitemap, you can basically pass Google an inventory of your content and let wee Googlebot crawl your pages without having to rely on your shaky navigational system!

What Is A Google Sitemap?
-------------------------

A Sitemap is a very simple XML file that you use to list the URL of each page in your site. We’ll get to the syntax and structure of the Sitemap XML in a minute, but first let’s look at the data you can record for each URL:

*   **URL**: You’ll need the URL for each page you list. This is represented by the **loc** element.
*   **Last modified**: Not required, but if your ASP.NET application records the date each page was updated, you could include it here. I’m assuming that Google will check this against the last crawl date and crawl the page if it’s been updated recently.
*   **Change Frequency**: Not required, but allows you to specify how often the page is likely to change. For example, content on your homepage is more likely to be updated than an archived article from 2005. [Google say](http://www.google.com/webmasters/sitemaps/docs/en/protocol.html) that this tag is considered a hint and not a command and that pages may be crawled more or less frequently than spidered.
*   **Priority**: You can use this tag to assign a weighting to each page, indicating it’s importance _on your site_. The valid values are from 0.0 to 1.0. Could be useful if you could find a way to assign priority to your pages.

Sample Sitemap
--------------

Here’s a sample sitemap. Notice that it starts with the XML declaration at the top. The first (root) element is `urlset` and within it, each url is defined by an `<url>` element. Note that for the moment, I’m just using the URL (**loc**) and the priority value

<?xml version="1.0" encoding="utf-8" ?>
<urlset xmlns="http://www.google.com/schemas/sitemap/0.84">
	<url>
		<loc>http://www.yoursite.com/Pages.aspx?pageid=21</loc>
		<priority>0.5</priority>

	</url>
	<url>
		<loc>http://www.yoursite.com/Pages.aspx?pageid=22</loc>
		<priority>0.5</priority>
	</url>

</urlset>

Creating Our Sitemap File
-------------------------

For this example, I’m going to assume you’ve got a fairly basic [content management system](http://en.wikipedia.org/wiki/Web_content_management_system), running on ASP.NET. Let’s say each page is stored as an entry in a database table called `pages`. You have fields for `page_id`, `date_created` and `date_updated` among others. Our sitemap is going to focus on displaying each page’s URI and last updated information. In [Visual Web Developer Express](http://msdn.microsoft.com/vstudio/express/vwd/), create a new .aspx page in your website (I called mine Sitemap.aspx for the sake of originality). When the page appears in the editor, strip out all the HTML, except the ASP.NET declaration on the very first line. The page should look something like this: <%@ Page Language=”VB” AutoEventWireup=”false” CodeFile=”Sitemap.aspx.vb” Inherits=”Sitemap” %> Now, press F7 to open up the codebehind file, and let’s get to work. Firstly, add the namespaces you’ll need to access the database, retrieve the data and write an XML file: At the very least, you’ll need System.Data and System.Xml. Second, create a `Page_Load` event. We want the sitemap to be generated dynamically each time the page is accessed. Within the Page_Load, we begin by writing the headers of the XML document:

Response.Clear()
Response.ContentType = "application/rss+xml"
Dim objX As New XmlTextWriter(Response.OutputStream, Encoding.UTF8)
objX.WriteStartDocument()

Next, we write the root element, `urlset` and set the `xmlns` attribute to import the Google Sitemap schema:

objX.WriteStartElement("urlset")
objX.WriteAttributeString("xmlns", "http://www.google.com/schemas/sitemap/0.84")

At this point, we’ll access the pages table in the database. The script below creates a SqlDataRead which iterates through the available pages and lists them by the date they were updated. As it iterates through the results, it creates a start element (url) using `WriteStartElement`, within which two other elements are nested using `WriteElementString`. The `url` element is finally closed using `WriteEndString`

Dim oCmd As New SqlClient.SqlCommand("SELECT * FROM pages ORDER BY date_updated DESC", sqlConn)
Dim oRdr As SqlClient.SqlDataReader = oCmd.ExecuteReader
If oRdr.HasRows Then
    While oRdr.Read
        objX.WriteStartElement("url")
        objX.WriteElementString("loc", "http://www.yoursite.com/Pages.aspx?pageid=" & oRdr("page_id"))
        objX.WriteElementString("priority", "0.7")
        objX.WriteEndElement() 'URL
    End While
End If

Finally we close our database objects and publish the XML document using `objX.Flush`:

oRdr.Close()
oCmd.Dispose()
objX.WriteEndElement() 'URLset
objX.WriteEndDocument()
objX.Flush()
objX.Close()
Response.End()

Now you’re done, you should be able to call up the Sitemap.aspx file in your web browser. Type in the URL (I found Internet Explorer best for this - FireFox tried to download the file for some reason), and the XML document should appear. Now, to finish the job off, create an account for [Google Sitemaps](https://www.google.com/webmasters/sitemaps), and follow the instructions there to set up a profile for your site and add your sitemap. After a few hours, Google should start to tell you if it parsed the sitemap correctly.