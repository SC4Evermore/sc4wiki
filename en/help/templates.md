---
title: "Templates"
description: ""
published: false
date: '2019-08-04T05:36:02Z'
tags: ["Templates"]
editor: markdown
dateCreated: '2008-07-29T14:37:40Z'
---

A list of templates and reasons why you would use them, including appropriate locations, etc...

## How to Use a Template

To use a template in a document just include the code in the *What you type* column in the tables below. Or use the info under the Syntax heading on the template page itself. Remember to fill in all the parameters associated with the template, or it wont display properly.

For example, to include the Language template (on a page with Dutch, French and Japanese translations):

will look like this:

## Curent Templates

The the sections below show all of the templates currently available on the wiki.

### Userpage Templates

> Main article: [Help:Userboxes](/help/userboxes)

<table>
<thead>
<tr>
<th style="background:#1e90ff;"><p>Template Name</p></th>
<th style="background:#1e90ff;"><p>What you type</p></th>
<th style="background:#1e90ff;"><p>What you see</p></th>
<th style="background:#1e90ff;"><p>Variables</p></th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td><p><!-- unconverted template: SiteProfile --></p></td>
<td><p><!-- unconverted template: SiteProfile --></p></td>
<td><ul>
<li><strong>site</strong> - The name of the site</li>
<li><strong>id</strong> - Your user ID</li>
<li><strong>name</strong> - (optional) can be added if you want your name to replace "My"</li>
</ul></td>
</tr>
<tr>
<td></td>
<td><pre><code><!-- unconverted template: Userbox --></code></pre></td>
<td><p><!-- unconverted template: Userbox --></p></td>
<td><ul>
<li><strong>border-c:</strong> The border colour of the userbox</li>
<li><strong>border-s:</strong> The border size of the userbox</li>
<li><strong>id-c:</strong> The background colour of the id box</li>
<li><strong>id-s:</strong> The font size of the id box</li>
<li><strong>id-fc:</strong> The font colour of the id box</li>
<li><strong>id-p:</strong> The distance between the border and the content of the id box</li>
<li><strong>id-lh:</strong> The distance between lines of text in the id box</li>
<li><strong>info-c:</strong> The background colour of the info box</li>
<li><strong>info-s:</strong> The font size of the info box</li>
<li><strong>info-fc:</strong> The font colour of the info box</li>
<li><strong>info-p:</strong> The distnace between the border and the content of the info box</li>
<li><strong>info-lh:</strong> The distance between lines of text in the info box</li>
<li><strong>id:</strong> The content of the id box</li>
<li><strong>info:</strong> The content of the info box</li>
</ul></td>
</tr>
</tbody>
</table>

### Infobox Templates

<table>
<thead>
<tr>
<th style="background:#1e90ff;"><p>Template Name</p></th>
<th style="background:#1e90ff;"><p>What you type</p></th>
<th style="background:#1e90ff;"><p>What you see</p></th>
<th style="background:#1e90ff;"><p>Variables</p></th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td><pre><code>
<div class="infobox">
<table>
<tr><th colspan="2">Templates</th></tr>
</table>
</div></code></pre></td>
<td><p>See [ the template description](/template-infobox-tgi#example) for details</p></td>
<td><ul>
<li><strong>name</strong> - The name of the TGI.</li>
<li><strong>format</strong> -</li>
<li><strong>type</strong> - The Type ID of the object, defines what file type the file is (?)</li>
<li><strong>group</strong> - The Group ID of the object</li>
<li><strong>instance</strong> - The Instance ID of the object</li>
<li><strong>comments</strong> (optional) - Any comments on the TGI.</li>
</ul></td>
</tr>
<tr>
<td></td>
<td><pre><code>
<div class="infobox">
<table>
<tr><th colspan="2">Templates</th></tr>
</table>
</div></code></pre></td>
<td><p>See [ the template description](/template-infobox-lot#example) for details</p></td>
<td><ul>
<li><strong>type</strong> - the type of lot it is (either plop or grow).</li>
<li><strong>image1</strong> - an example image.</li>
<li><strong>image2</strong> - another example image.</li>
<li><strong>desc</strong> - the lot description (readme)</li>
<li><strong>credits</strong> - any credits</li>
<li><strong>supports</strong> - any supporting acts</li>
<li><strong>download-site</strong> - the download site</li>
<li><strong>download-id</strong> - the download lot id</li>
</ul></td>
</tr>
<tr>
<td></td>
<td><pre><code>
<div class="infobox">
<table>
<tr><th colspan="2">Templates</th></tr>
</table>
</div></code></pre></td>
<td><p>See [ the template description](/template-infobox-grow#example) for details</p></td>
<td><ul>
<li><em>image1</em>, <em>image2</em>, <em>desc</em>, <em>credits</em>, <em>support</em>, <em>download-site</em>, <em>download-id</em> - See [Template:Infobox_lot](/template-infobox-lot) for details.</li>
<li><strong>size</strong> ([a]x[b]) - Lot size a tiles long by b tiles wide.</li>
<li><strong>type</strong> - The type of lot Residential, Commercial, Industrial, Agricultural</li>
<li><strong>style</strong> - The [Tileset](/tileset) the lot grows under</li>
<li><strong>stage</strong> - The [Growth Stage](/growth-stage) of the lot.</li>
<li><strong>occupants</strong> - The maximum number of Sims that can live/work in the LOT</li>
<li><strong>worth</strong> -</li>
<li><strong>bulldoze-cost</strong> - The number of Simoleons (without the § sign as that is already there) the building costs to demolish.</li>
<li><strong>construction-time</strong> - The time it takes for the lot to be constructed</li>
<li><strong>fire</strong> - The maximum fire stage, if the lot reaches this stage in a fire it will be destroyed.</li>
<li><strong>power</strong> - The amount of electrical power consumed by the lot, in MWh/month.</li>
<li><strong>water</strong> - The amount of water consumed by the lot, in Gallons/month.</li>
<li><strong>air-mag</strong> - The magnitued of Air Pollution over <strong>air-spr</strong> tiles.</li>
<li><strong>water-mag</strong> - The magnitude of Water Pollution over <strong>water-spr</strong> tiles.</li>
<li><strong>garbage-mag</strong> - The magnitude of Garbage Pollution over <strong>garbage-spr</strong> tiles.</li>
<li>'''depend - Any dependencies that are needed for this lot to work.</li>
</ul></td>
</tr>
<tr>
<td></td>
<td><pre><code>
<div class="infobox">
<table>
<tr><th colspan="2">Templates</th></tr>
</table>
</div></code></pre></td>
<td><p>See [ the template description](/template-infobox-plop#example) for details</p></td>
<td><ul>
<li><em>image1</em>, <em>image2</em>, <em>desc</em>, <em>credits</em>, <em>support</em>, <em>download-site</em>, <em>download-id</em> - See [Template:Infobox_lot](/template-infobox-lot) for details.</li>
<li><strong>size</strong> ([a]x[b]) - Lot size a tiles long by b tiles wide.</li>
<li><strong>menu</strong> - The menu the lot resides in.</li>
<li><strong>jobs</strong> - The number of jobs the lot supplies (can be formatted with $'s if the lot supplies multiple wealth jobs).</li>
<li><strong>plop-cost</strong> - The number of Simoleons (without the § sign as that is already there) the building costs to build.</li>
<li><strong>bulldoze-cost</strong> - The number of Simoleons (without the § sign as that is already there) the building costs to demolish.</li>
<li><strong>park-mag</strong> - The magnitude of Park Effect over <strong>park-spr</strong> tiles.</li>
<li><strong>landmark-mag</strong> - The magnitude of Landmark Effect over <strong>landmark-spr</strong> tiles.</li>
<li><strong>fire</strong> - The maximum fire stage, if the lot reaches this stage in a fire it will be destroyed.</li>
<li><strong>power</strong> - The amount of electrical power consumed by the lot, in MWh/month.</li>
<li><strong>water</strong> - The amount of water consumed by the lot, in Gallons/month.</li>
<li><strong>air-mag</strong> - The magnitued of Air Pollution over <strong>air-spr</strong> tiles.</li>
<li><strong>water-mag</strong> - The magnitude of Water Pollution over <strong>water-spr</strong> tiles.</li>
<li><strong>garbage-mag</strong> - The magnitude of Garbage Pollution over <strong>garbage-spr</strong> tiles.</li>
<li>'''depend - Any dependencies that are needed for this lot to work.</li>
</ul></td>
</tr>
</tbody>
</table>

### Request/Marking Templates

> Main article: [Help:Marking Articles](/help/marking-articles)

<!-- unconverted template: Help:Marking Articles -->

### Language Templates

<table>
<thead>
<tr>
<th style="background:#1e90ff;"><p>Template Name</p></th>
<th style="background:#1e90ff;"><p>What you type</p></th>
<th style="background:#1e90ff;"><p>What you see</p></th>
<th style="background:#1e90ff;"><p>Variables</p></th>
</tr>
</thead>
<tbody>
<tr>
<td width="10%"></td>
<td width="10%"><pre><code></code></pre></td>
<td width="60%"></td>
<td width="20%"><p>*<strong>lang</strong> (multiple, optional) - the 2 character code of the languages where a translation of this page is available. <strong>The code for English (en) does not need to be inlcuded, its presence is assumed by the template.</strong></p></td>
</tr>
</tbody>
</table>

### Other Templates

<table>
<thead>
<tr>
<th style="background:#1e90ff;"><p>Template Name</p></th>
<th style="background:#1e90ff;"><p>What you type</p></th>
<th style="background:#1e90ff;"><p>What it does</p></th>
<th style="background:#1e90ff;"><p>Variables</p></th>
</tr>
</thead>
<tbody>
<tr>
<td></td>
<td><pre><code></code></pre></td>
<td><p>Will provide a link to a download on one of the SC4 Exchanges (SC4D/BSC LEX, STEX, TPPEX or PLEX).</p></td>
<td><ul>
<li><strong>Exchange:</strong> The name of the exchange. Can be; LEX, STEX, TPP or PLEX.</li>
<li><strong>id:</strong> The id of the download on that exchange (if Exchange isn't specified, ID is the full URL).</li>
</ul></td>
</tr>
<tr>
<td></td>
<td><pre><code>
> Main article: [articlename](/articlename)</code></pre></td>
<td><p>Used when transcluding a section of an article to provide a link to the whole article.</p></td>
<td><p><strong>articlename:</strong> Replace this variable with the title of the article you wish to link to.</p></td>
</tr>
</tbody>
</table>

### Navbox Templates

See [:Category:General article templates](/category/general-article-templates) for navboxes in use at this site.

## How to Make a Template
