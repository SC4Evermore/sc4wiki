---
title: "Starting a new page"
description: ""
published: false
date: '2019-08-07T23:01:13Z'
tags: []
editor: markdown
dateCreated: '2019-08-07T23:01:13Z'
---

> **Note:** This article needs formatting.

For help creating an article, read [Help:Contributing](/help/contributing). This article provides help on creating pages other than articles, and provides technical details on the several ways to create a page.

One of the [user rights](/user-groups) that can be set for a user group is "createpage", the right to create a new page. A wiki can grant this right for example to all users who are not blocked, or only to those who have logged in.

The edit page has a link for *Editing help*, so you won't be lost. For general editing matters and details on the [markup language](/wikipedia-markup-language) of the [wikitext](/help/filling-the-page), see [Help:Editing](/help/editing). *If you want to experiment, use the [sandbox](/zztoken1zz-sandbox) first.* Note: Sandbox page is currently blank. The purpose of this blank page is to use as a whiteboard to experiment.

Anyone, including you, can write these help documents at [m:Help:Contents](/m-help-contents), and you are most likely allowed to edit the site, <!-- unconverted template: SITENAME --> that you are looking at now! Just type a title in the box at the bottom of the page, click "Create article", and start writing. You should probably create a link to the article in a related page; linking to a page is enough to "create" the page! New pages can also be started by following a link to a non-existent page, which likewise launches the edit page. See [Starting a page through the URL](#starting-a-page-through-the-url) below.

## General principles

- **[Search](/help/searching)** to see **whether** someone has written a similar page before you start one yourself. Choose the title carefully.
- Review conventions of the project you are working in regarding e.g.:
  - naming conventions; see also [Help:Page name](/help/page-name).
  - whether a separate page is justified; perhaps it is better to add the text to a related page (especially if the text is not very long); that page can always be split later, after it has grown.
  - how-to guidance for writing regarding style, content and formatting. E.g. for the Wikipedia project see [How to write a great article](/w-wikipedia-how-to-write-a-great-article).
- While creating the page and **before** saving it, check the <u>*What links here*</u> link on the creation page. Align the new content with existing links, or change the new title, or fix the other links.
- If nothing points here, the page is isolated. Links to it will need to be added on other pages.

## Starting a page from a link, or after a search

To start a new page, you can click a link to the new page. This takes you to [edit](/help/editing) mode of the non-existing blank page, which allows creation. You might not be able to create a new page unless you are logged in. Notably this applies to the English Wikipedia. Another way to start a new page, on the English Wikipedia, which uses the [w:MediaWiki:Nogomatch](/w-mediawiki-nogomatch) option, is to perform a search for the new title with the Go button (as you should have done before). When the search finds nothing, press "create the article".

Links to non-existing pages are common. They are typically created in preparation for creating the page, and/or to encourage other people to do so. Links are not only convenient for navigation, but also make people aware of the new page (those who read a related page and also those who [watch](/help/watching-pages) the related page). New page links are not really broken, as long as the name correctly identifies the intended content. (A new page link with a "wrong" or misspelled name, or that duplicates content found under another name is "broken", but in a different sense.)

New page links typically look different from links to existing pages. Depending on [settings](/help/preferences), a different color or a question mark is used. (Sometimes links to new pages are called "red links", the display option of one of the settings). Links to non-existent pages are created with \[\[New page name\]\] from the wiki editor. (In this case, the empty page "New page name" would be created).

Of course, you can also create the link yourself, in a related page, index page or your user page. However, it may be better to wait with creating links until after creating the new page, especially if the new link replaces one to an existing page. In this case, create the link but press Preview, instead of Save. From preview area, clicking the new link will create the new page (without updating the referring page).

## Starting a page through the URL

Using the browser address bar to enter a URL to a new page is an easy way to start the new page process. Easier still is editing the pagename part of a URL for an existing page. Using the URL for the new page displays the default 'no article' message. The default page has the usual <u>*Edit this page*</u> link, which can be used to begin adding content.

To get access to a MediaWiki project page, with the links at the edges but without the superfluous loading of a page, use a bookmark to a non-existing page. The default 'no article' page will display the edge links.

## Creating an empty page

A **new page** is distinguished from a blank page: the latter has a [page history](/help/page-history). However, creating a new page is just like editing a blank page, except that a new page displays the text from [MediaWiki:Newarticletext](/mediawiki-newarticletext) (which may vary by project).

Occasionally it is useful to create an empty page - For example a template can be made such that, depending on a parameter, it produces either just a standard text or also an additional text. This is done by having it call another template, of which the name is a parameter; one version of the other template contains the additional text, the other version is blank. See [optional text](/help/advanced-templates#optional-text).

To create an empty page, save a page with the wikitext . This code will not be saved, it just prevents refusal by the system to create an empty page. Alternatively, first create a non-empty page, e.g. with just one character, then edit the page to make it empty. A page with one or more blank spaces at the end, including a page only containing one or more blank spaces, is not possible.

## Using text from some other editing environment

Although pasting existing text into the wiki is often the simplest way to start, you may want to [try converting from Word or HTML to wiki markup](/help/wordtowiki).

## Protecting a page from being created

It is not really possible to protect a page from being created, but one can create a page with a standard text such as in [w:en:Template:Deletedpage](/w-en-template-deletedpage) and [protect](/help/editing#page-protection) that page. Note that sometimes a terminology like "This page should not be created." is used even though for the system the page exists. Therefore it is not suitable for demonstrating a link to a non-existing page.

## Non-existing pages showing info

Category and image pages are partly dynamically generated, and partly editable. A category page contains a list of pages in the category, an image page may contain an image and info from Commons. Thus if the page does not "exist" it may still show info.

The edit page of a "non-existing" category page shows the pages it contains. However, the edit page of the local page of an image on Commons neither shows the image, nor the editable content on Commons, not even in preview, it does not even indicate that viewing the page provides an image and other content from Commons.

A link to a "non-existing" category page is treated as a link to a non-existing page, even if the category is non-empty. A link to a "non-existing" local image page of an image on Commons is treated as a link to an existing page, e.g. [:Image:Cow-on pole, with horns.jpeg](/image-cow-on-pole-with-horns-jpeg), except in the case of a link from an edit summary or log. An indication of the "non-existence" is the lack of a page history link and a related changes link.
