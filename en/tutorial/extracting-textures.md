---
title: "Extracting Textures"
description: ""
published: false
date: '2019-10-24T17:10:45Z'
tags: ["MOD Tutorials/Textures"]
editor: markdown
dateCreated: '2008-10-28T05:52:19Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [Jeronij](/people/jeronij), from [SimCity 4 Devotion](/simcity-4-devotion).

Hi, I just answered somebody\`s private question, and I though the answer could be useful for other players as well, so I post (and extend) it here:  
  
This is a tutorial for newbies who want to start dealing with custom textures and BAT models using the original Maxis textures.  
  
<b><span style="font-size: 10pt; line-height: 1.3em;"><span style="background-color: red;">TRANSIT TEXTURES</span></span></b> ( The easy ones)  
  
You need the Ilives Reader installed and linked to the game folders.  
  
Open Ilives Reader and go to : Tools --\> Texture Viewer.  
Then select the desired transit network ( tree on the left) and the textures appear on the right. Zoom 5 for the right textures.  
Right click on the texture you want to export and choose "Save FSH". Two files will be created wherever you saved the texture.  
  
Now you need to open the new fsh file with Ilives Fishman tool to convert it into a bitmap file  
  

<div class="quoteheader">

Quote

</div>

<div class="quote">

<b>Creating and editable bitmap file with Fishman.</b>  
Go to File --\> Open and open your file. In the tree on the left select the Bitmaps folder. Right click on the small bitmap icon and select --\> Export --\> Color.  
Select bmp type and give it a name. Save and you have your texture in a useful filetype for any software.  
You can also extract the alpha maps ( for transparency) using the same method. Just select "alpha" instead "color"  

</div>

  
You can find both programs, <b>Ilives Reader and Fishman</b>, in the <i>Modds and Downloads </i> section at [Simtropolis](/simtropolis).  
  
<b><span style="font-size: 10pt; line-height: 1.3em;"><span style="background-color: red;">OTHER TEXTURES</span></span></b> ( Rock, water, custom textures, etc...)  
  
You need to start Ilives Reader. Open the dat file containing the textures. The Maxis textures are found in the 5/6 original Maxis files. SimCity_1.dat to SimCity_5.dat. Also EP1.dat (in my version) contains textures (mainly buildings).  
Once you have found your texture ( you can use Ilives Reader filters to help you with this), make sure you select the biggest one in the series.  
  

<div class="quoteheader">

Quote

</div>

<div class="quote">

<b>Extra quick explanation about textures IDs</b>.  
   
Normally you will find until 5 textures for each final texture. One per zoom level. Its Instance number keeps the following patterns:  
  
For Lot Editor Base and Overlay textures and Water textures:  
XXXXX001 to XXXXX004  being XXXXX004 the biggest texture ( closest zoom level)  
  
For Rock textures:  
XXXXX044 to XXXXX444 being XXXXX444 the biggest texture ( closest zoom level)  
  
Quick Info:  
The TGI for rock mods is:    7AB50E44     891B0E1A     00000444  
The TGI for water mods is:  7AB50E44     891B0E1A     09187304  
  

</div>

   
You can already see the idea, right ?¿  
  
Back to topic, once you have found your texture, select it and right click on it. Click on : " Save decoded file(s)" and save your file. You can give it a .fsh extension or not. It will work anyway.
