---
title: "Formatting"
description: ""
published: false
date: '2019-08-09T21:35:24Z'
tags: []
editor: markdown
dateCreated: '2019-08-09T21:35:24Z'
---

You can format your text using wiki markup. This consists of normal characters like asterisks, single quotes or equation marks which have a special function in the wiki, sometimes depending on their position. For example, to format a word in *italic*, you include it in two single quotes like `''this''`

> **Note:** This article needs expanding.

## Text formatting markup

<table>
<thead>
<tr>
<th style="background:#1E90FF;"><p>Description</p></th>
<th style="background:#1E90FF;"><p>You type</p></th>
<th style="background:#1E90FF;"><p>You get</p></th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="3" style="text-align: center;"><p><em>Tags which apply anywhere:</em></p></td>
</tr>
<tr>
<td><p>Italic text</p></td>
<td><p><code>''italic''</code></p></td>
<td><p><em>italic</em></p></td>
</tr>
<tr>
<td><p>Bold text</p></td>
<td><p><code>'''bold'''</code></p></td>
<td><p><strong>bold</strong></p></td>
</tr>
<tr>
<td><p>Bold and italic</p></td>
<td><p><code>'''''bold &amp; italic'''''</code></p></td>
<td><p><strong><em>bold &amp; italic</em></strong></p></td>
</tr>
<tr>
<td><p>Escape wiki markup</p></td>
<td><p><code>&lt;nowiki&gt;no ''markup''</code></nowiki></p></td>
<td><p>no ''markup''</p></td>
</tr>
<tr>
<td colspan="3" style="text-align: center;"><p><em>Tags which can only be used at the beginning of the line</em></p></td>
</tr>
<tr>
<td><p>Indent text</p></td>
<td><p><code>:Indent text</code></p></td>
<td><p>    Indent text</p></td>
</tr>
<tr>
<td><p>Headings of different levels<br />
Use of a heading created by single equal signs is discouraged as it appears with the same formatting and size as the page title, which can be confusing. An article with four or more headings will automatically create a <a href="http://en.wikipedia.org/wiki/Wikipedia:Section#Table_of_contents_.28TOC.29">table of contents</a>.</p></td>
<td><p><code>==level 1==</code><br />
<code>===level 2===</code><br />
<code>====level 3====</code><br />
<code>=====level 4=====</code></p></td>
<td><h2 id="level_1">Level 1</h2>
<h3 id="level_2">Level 2</h3>
<h4 id="level_3">Level 3</h4>
<h5 id="level_4">Level 4</h5></td>
</tr>
<tr>
<td><p>Horizontal rule</p></td>
<td><p><code>----</code></p></td>
<td><hr /></td>
</tr>
<tr>
<td><p>Bullet list</p></td>
<td><p>* one<br />
* two<br />
* three<br />
** three and one-third<br />
** three and two-thirds<br />
</p></td>
<td><ul>
<li>one</li>
<li>two</li>
<li>three
<ul>
<li>three and one-third</li>
<li>three and two-thirds</li>
</ul></li>
</ul></td>
</tr>
<tr>
<td><p>Numbered list</p></td>
<td><p># one<br />
# two&lt;br&gt;spanning several lines&lt;br&gt;without breaking the numbering<br />
# three<br />
## three point one<br />
## three point two<br />
</p></td>
<td><ol>
<li>one</li>
<li>two<br />
spanning several lines<br />
without breaking the numbering</li>
<li>three
<ol>
<li>three point one</li>
<li>three point two</li>
</ol></li>
</ol></td>
</tr>
<tr>
<td><p>Mixture of bulleted<br />
and numbered lists</p></td>
<td><p># one<br />
# two<br />
#* two point one<br />
#* two point two<br />
</p></td>
<td><ol>
<li>one</li>
<li>two
<ul>
<li>two point one</li>
<li>two point two</li>
</ul></li>
</ol></td>
</tr>
<tr>
<td><p>Definition list</p></td>
<td><p>;Definition<br />
:item 1<br />
:item 2<br />
</p></td>
<td><dl>
<dt>Definition</dt>
<dd>
item 1
</dd>
<dd>
item 2
</dd>
</dl></td>
</tr>
<tr>
<td><p>Preformatted text</p></td>
<td><p>  preformatted text is done with<br />
  a space at the<br />
  beginning of the line<br />
</p></td>
<td><p><code>preformatted text is done with</code><br />
<code>a space at the </code><br />
<code>beginning of the line</code></p></td>
</tr>
<tr>
<td><p>Blockquotes</p></td>
<td><p>Body<br />
text text text text text text text text text text text text text text text text text text text text text text text text</p>
<p>&lt;blockquote&gt; quote quote quote quote quote quote &lt;/blockquote&gt;</p>
<p>text text text text text text text text text text text text</p></td>
<td><p>Body<br />
text text text text text text text text text text text text text text text text text text text text text text text text</p>
<blockquote>
<p>quote quote quote quote quote quote</p>
</blockquote>
<p>text text text text text text text text text text text text</p></td>
</tr>
</tbody>
</table>

## Paragraphs

MediaWiki ignores normal line breaks. To start a new paragraph, leave an empty line. You can also start a new line with the HTML tags `<br> or <br/>`.

## HTML

Some [HTML](http://www.wikipedia.com/wiki/html) tags are allowed in MediaWiki, for example `<code>`, `<div>`, `<span>` and `<font>`.

## Other formatting

Beyond the text formatting markup shown above, here are some other formatting references:

[More Formatting from Wikipedia](http://en.wikipedia.org/wiki/Wikipedia:WikiProject_User_Page_Help/Do-It-Yourself/Formatting_Text)
