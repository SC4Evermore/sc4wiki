---
title: "Switch Language and Driving Sides"
description: ""
published: true
date: '2019-08-09T02:32:16Z'
tags: ["OTHER Tutorials"]
editor: markdown
dateCreated: '2008-10-27T16:47:09Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [RippleJet](/people/ripplejet), from [SimCity 4 Devotion](/simcity-4-devotion).

Depending on where in the world you live, your copy of SimCity 4 was shipped with more than one language.  
You can select this language when you install the game. However, you can also change the setting later on.  
  
Now, why would I want to change the language of the game? <http://sc4devotion.com/forums/Smileys/JasonSmilies/confused-smiley-001.gif>  
  
There are a number of reasons listed below. Changing these settings doesn't affect only the language of the game though.  
You will also get different settings for the date format and you can determine which side of the road cars will drive on.  
  
1. If more than one language is spoken in your family, you might want to change it every now and then.  
2. If you want to play the game in English, despite having installed it in your native tongue.  
3. If you want to switch into English for the purpose of taking screen shots most people can understand.  
4. If cars are driving on the left hand side in the country you live, but on the right hand side in the game (e.g. Australia or Thailand).  
5. If you want to test [**multilingual lots**](http://sc4devotion.com/forums) made for other languages than your primary one.  
  
  

<hr>

  
  
<span style="font-size: 12pt; line-height: 1.3em;"><b>Changing the Langauge in the Registry Editor</b></span>  
  
  
In order to change the language and other settings, you need to start a program called the Registry Editor.  
The easiest way to run that program is to click Run in the Start menu and enter "regedit" into the field:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/StartRegedit.jpg>  
  
Note that my operating system is talking Swedish, but I'm sure you can find out which buttons to press on your computer.  
Press OK and the Registry Editor will start:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/MaxisRegistry.jpg>  
  
Use the window on the left to find the following folder: HKEY_LOCAL_MACHINE\SOFTWARE\Maxis\SimCity 4\1.0  
One of the "keys" contained in there is called <b>Language</b>, set to 0x00000001 (1) in the example above.  
  
This is the only key that you need to change in order to change the language your game runs on.  
Changing the key LanguageName won't affect the game in any way.  
  
Warning! Never change the registry while the game is running.  
  
  

<hr>

  
  
<span style="font-size: 12pt; line-height: 1.3em;"><b>Which languages are available?</b></span>  
  
  
That is largely dependent on where you bought the game.  
In order to check your options, you first have to locate the installation folder of SimCity 4.  
  
That would normally be <b>C:\Program Files\Maxis\SimCity 4\\</b> if you installed the Vanilla version and upgraded it to Rush Hour.  
If you bought the DeLuxe verision, you have probably installed it in <b>C:\Program Files\Maxis\SimCity 4 Deluxe\\</b>.  
Note that C:\Program Files\\ is called something else if you operating system isn't speaking English...  
  
Below is a typical installation folder for SimCity 4 Deluxe bought in North America:  
<http://i232.photobucket.com/albums/ee198/RippleJet/SC4Folder-US.jpg>  
  
There are two folders marked with a red dot. Those are the only languages available in this case.  
  
Below is another typical installation folder for SimCity 4 bought in Europe:  
<http://i232.photobucket.com/albums/ee198/RippleJet/SC4Folder-EU.jpg>  
  
Note that there are a lot more languages available for European players.  
Note also the spelling of the folders Norwgian, Portgese and UKEnglsh.  
No folder name contains any more than 8 characters...  
  
~~If you've bought your game in the far east, you would probably find folders called e.g.  
Japanese, Korean, SChinese (for Simplified Chinese), TChinese (for Traditional Chinese) or Thai.~~  
  
If you've bought your game in Japan, you'd find only one folder, called Japanese.  
  
  

<hr>

  
  
<span style="font-size: 12pt; line-height: 1.3em;"><b>Which number is which language in the Registry?</b></span>  
  
  
Depending on the Language number in the SC4 Registry, the game looks for a file called SimCityLocale.DAT in one of the folders above.  
The name of the file is the same in all language folders. Only the name of the folder identifies which language the file includes.  
  
The SimCityLocale.DAT file contains almost 6,000 LTEXT files. These files include all texts that are displayed in the game.  
By loading another SimCityLocale.DAT file at startup, all texts in your game would change accordingly.  
  
The name of the folder that the game is looking for is directly dependent on the Registry Setting.  
If the Language is set to 1 (as in the example above), the game would be looking for a SimCityLocale.DAT file in the folder English.  
  
Below is a summary of all Key values that can be used.  
As mentioned above, the Language also determines which side the cars are driving on.  
  

<table style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;">

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>   Registry Key     
Language</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<b>Folder Name   </b>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>Cars Drive on</b>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b> </b>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x01</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

English

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x02</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

French

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x03</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

German

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x04</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Italian

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x05</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Spanish

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x06</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Swedish

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x07</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Finnish

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x08</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Dutch

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x09</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Danish

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x0A</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Portgese

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b><span style="color: rgb(224, 224, 224);">0x0B</span></b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<span style="color: rgb(224, 224, 224);">Czech</span>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<span style="color: rgb(224, 224, 224);">Right</span>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b><span style="color: rgb(224, 224, 224);">0x0C</span></b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<span style="color: rgb(224, 224, 224);">Hebrew</span>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<span style="color: rgb(224, 224, 224);">Right</span>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b><span style="color: rgb(224, 224, 224);">0x0D</span></b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<span style="color: rgb(224, 224, 224);">Greek</span>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<span style="color: rgb(224, 224, 224);">Right</span>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x0E</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Japanese

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Left

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x0F</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Korean

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b><span style="color: rgb(224, 224, 224);">0x10</span></b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<span style="color: rgb(224, 224, 224);">Russian</span>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<span style="color: rgb(224, 224, 224);">Right</span>

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x11</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

SChinese

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x12</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

TChinese

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x13</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

UKEnglsh

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Left

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x14</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Polish

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x15</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Thai

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

<b>0x16</b>

</div>

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Norwgian

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div align="center">

Right

</div>

</td>

</tr>

</table>

  
Note that all Language numbers are hexadecimal. Thus they must be preceeded by 0x...  
  
Note also that, even if Czech, Hebrew, Greek and Russian are listed as options,  
there are no SimCityLocale.DAT files available in those languages.  
Obviously Maxis didn't have time to finish the translation into all languages...  
  
In addition to determining the folder where SimCityLocale.DAT is loaded and the side the cars drive on,  
changing the Language also affects the date format and might require another set of fonts to work 100%.  
  
  

<hr>

  
  
<span style="font-size: 12pt; line-height: 1.3em;"><b>Frequently Asked Questions</b></span>  
  
  
<b>Q: I live in Australia but the cars in the game drive on the right-hand side.</b>  
  
R: Your game is probably a US version.  
In the game's installation folder, create a new subfolder called <b>UKEnglsh</b>.  
Copy the file SimCityLocale.DAT from the folder English to this newly created UKEnglsh.  
Start the Registry Editor and change Language from 0x01 to 0x13.  
  
  
<b>Q: I live in Denmark and have installed the game in Danish, but I want the game to be English.</b>  
  
R: Do not reinstall the game in English as that will cause the cars to drive on the left-hand side.  
Instead, in the game's installation folder, create a new subfolder called <b>English</b>.  
Copy the file SimCityLocale.DAT from the folder UKEnglsh to this newly created English.  
Start the Registry Editor and change Language from 0x09 to 0x01.  
  
  
<b>Q: I live in USA and my brother-in-law from Mexico wants to play the game in Spanish.</b>  
  
R: Start the Registry Editor and change Language from 0x01 to 0x05.  
  
  
<b>Q: I live in Sweden and want to test a multilingual lot in German.</b>  
  
R: Start the Registry Editor and change Language from 0x03 to 0x06.  
  
  
<b>Q: I live in France and want to take English screen shots of my MD.</b>  
  
R: In the game's installation folder, create a new subfolder called <b>English</b>.  
Copy the file SimCityLocale.DAT from the folder UKEnglsh to this newly created English.  
Start the Registry Editor and change Language from 0x02 to 0x01.
