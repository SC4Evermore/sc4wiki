---
title: "Creating Textures"
description: ""
published: true
date: '2019-10-24T17:02:28Z'
tags: ["MOD Tutorials/Textures", "MOD Tutorials/Transport"]
editor: markdown
dateCreated: '2008-10-27T19:11:02Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [Jplumbley](/people/jplumbley), from [SimCity 4 Devotion](/simcity-4-devotion). [Original tutorial](http://sc4devotion.com/forums/index.php?topic=4140.0).

Transit textures are not so hard to make, in fact they arent any harder than making standard textures. There are a few differences though between transit textures and standard textures. Just like with standard textures there are base and overlay textures, but they are sidewalk (base) and the road surface (overlay) textures. I will explain when and how these textures are used as well as how to create them.

### Requirements

- Beginner to Intermediate Level Modder (comfortable using SC4Tool)
- [SC4Tool](/sc4tool)
- iLive's [Reader](/reader)
- [FSHman](/fshman)
- Photo Editor (perferably one that can deal with layers such as [Photoshop](/wp-photoshop) or [Paint Shop Pro](/wp-paint-shop-pro), but of course any photo editor will do that can save in PNG format)

## Extracting Textures

This section will explain how to extract any texture from a given DAT file including the MAXIS simcity\_\*.dat files. You will be using iLive's Reader and FSHman in this section. Extracting textures can be benefitial when making adjustments to existing textures, such as making a Euro Texture Mod.

We must start in iLive's Reader. First you must open the texture DAT that you are looking for in iLive's Reader, then select all the the textures you want and copy them into the Blank.dat as shown. Remember you dont need all 5 views of the textures, just the 04, 14, 24 and 34 textures (128x128 pixels). When you re-import the texture into a DAT later, you will only need the 128x128 pixel texture for all 5 zooms.

<div align="center">

<http://img81.imageshack.us/img81/9113/extractingtextures1lu1.jpg>

</div>

<div align="center">

<http://img81.imageshack.us/img81/508/extractingtextures2jo0.jpg>

</div>

When you have all the textures you want goto File -\> Export All Files.. Before you do this, I suggest that you create a "working" folder for you to extract the textures to. When you extract the files it will extract the files into two files, a FSH file and a TGI file. For us the TGI file is useless and you can remove it. The FSH files are what we are looking for.

<div align="center">

<http://img81.imageshack.us/img81/570/extractingtextures3vk7.jpg>

</div>

Now we are done with iLive's Reader, you can close it and you dont have to save anything. We now need to work with FSHman. FSHman cannot open DAT files so we must open each FSH file that we extracted separately and save them as PNG files. To do this select File -\> Open and click on the \*.FSH file. Then click on the \#1 under Bitmaps and then click File -\> Save as.. Save the file as a Portable Network Graphic (PNG) file.

<div align="center">

<http://img81.imageshack.us/img81/3679/extractingtextures4rr7.jpg>

</div>

Now you are able to extract existing textures!

## Texture Specifications

The most important transit texture specification is the IID. The IID is the piece of information that the RULs and EXE will reference when looking for a texture, if it is wrong your texture will not work in-game. This is how texture IIDs are designed.

### MAXIS IID Structure for Transit Textures

0x0nppppwz

n = network ID pppp = piece ID w = wealth of texture z = zoom of texture

#### Network IDs MAXIS used

0 Road 3 Rail 4 Avenue 5 Street 6 Water pipe 7 Subway 8 El-Rail 9 One Way Road A Highway C El-Highway D Monorail

- I forget off hand what the other network IDs are, but I will update this later when I remember. Others include Power Lines (2?)

### NAM Texture IID Structure

Originally, the texture IIDs used to be based off of a time stamp, but we have since reached the end of that time stamp and we could potentially start creating conflicts. Now we have come up with a solution to this and there is a new structure that is being used for projects like [SAM](/sam), [RHW](/rhw), [NWM](/nwm) and [HSRP](/hsrp). Any new textures will be assigned a range and any new transit textures will have to be syncronized with the rest of the NAM before release.

0x5rrpppwz

5 = NAM range rr = project range ppp = piece ID w = wealth of texture z = zoom of texture

### Wealths

0 = No wealth..... This has no sidewalk texture underneath the road surface texture 1 = Low wealth 2 = Medium wealth 3 = High wealth 4 = Low wealth (Medium and High Density) 5 = Medium wealth (Medium and High Density) 6 = High wealth (Medium and High Density) 7 = Agriculture

**\*Note** Wealths 4 through 7 default to wealth 0 if no texture exists. Wealths 0 through 3 are required for ingame to work properly.

**Zooms:** (pixel size) 0 = 8x8 1 = 16x16 2 = 32x32 3 = 64x64 4 = 128x128

## Creating Textures (Overlay Textures)

Road Surface Textures are exactly what the name portrays, they are textures for the road surface of the network. There are many textures required for a network and they are different for each network. I cannot really give a list of every texture, because there are too many to name, so it is best to extract the originals themselves for guidence on that.

Now, of course there are a few things that these textures are comprised of... The road surface, curb and grass as shown in the following texture.

<div align="center">

<http://img301.imageshack.us/img301/1470/roadsurfacetexture1qu6.png>

</div>

Some of you may wonder why is there no sidewalk on this texture. Well, this is because the sidewalks are actually an underlay that goes under the road surface.

So, now you are wondering, I have shown a texture with the whole texture covered and there is no invisible parts to show the sidewalk through. You, would be right, I still would have another another step to do before I import the texture using SC4Tool. This step includes the creation of an Alpha Texture.

An Alpha Texture is a texture that where there is Black it erases anything from that part of the texture and where there is White it keeps whatever is on the texture. So, for all intensive purposes:

**Black** = where the sidewalk will go **White** = everything else

<div align="center">

<http://img301.imageshack.us/img301/1016/roadsurfacetexture3wz2.jpg>

</div>

*This is an Alpha Texture.*

<div align="center">

<http://img301.imageshack.us/img301/7240/roadsurfacetexture2xa3.png>

</div>

*This is the Alpha Texture overlaid onto the texture and made 50% invisible so it will give you an idea of what I am talking about.*

For the sidewalk textures there are 4 and only 4 textures in the game. No more, no less. These 4 textures are wealth based and are used when the neighboring lot is of a certain wealth:

IID = 0x0840000z **Rural Wealth** IID = 0x0810000z **Low Wealth** IID = 0x0820000z **Medium Wealth** IID = 0x0830000z **High Wealth**

- The z is the zoom view of the texture.

Now, I am no expert when it comes to physically designing and creating the texture because that is your job. My specialty is taking existing textures and making more out of them using parts of the originals. But... You have the idea and you can bring that idea to life, I will just help you with getting it into a texture DAT now.

Using SC4Tool, we will be putting these textures into a texture DAT. So, to start, open SC4Tool and select "Create your own textures". Then hit the star to create a new texture DAT from scratch. To import the textures you now want to hit the picture next to the star.

<div align="center">

<http://img217.imageshack.us/img217/665/texturecreator1lm1.jpg>

</div>

<div align="center">

<http://img301.imageshack.us/img301/7643/roadsurfacetexture4dc1.jpg>

</div>

<div align="center">

<http://img301.imageshack.us/img301/3426/roadsurfacetexture5fq6.jpg>

</div>

First thing you need to do is set it so that you are creating a Traffic Texture by hitting radial button. Then you want to hit the folder next to the 128x128 Bitmap to load the road surface texture, to apply the 128x128 size to all 5 zoom textures just hit the little camera. Do the same thing for the Alpha Map and your almost good to go.

The final thing that you need is the texture IID, this is something that you should know before you start importing the texture. Do not ever click "next free IID", you need to know what texture you are replacing or adding. If you are adding a texture, the person writing the RULs will tell you what IID you need. If you are replacing a texture, the original texture will tell you what IID you need. This is the most important thing, because the IID is everything when it comes to Transit Textures, unlike with Standard Textures.

Another thing to think about when creating textures is the orientation. If the texture is a replacement, you MUST remember to have it rotated so that the entrance/exits of the tile are in the exact same places as the original texture. RULs define when and at what orientation the textures will show up at and if you are replacing the texture its easier to make the texture properly rather than change the RULs to fit the new texture.

Sometimes, it is possible to use the same texture over and over. For example, sometimes in the past for a replacement of the Avenue 4way Intersection the creator made 4 different textures, one for each tile in the intersection. But, through the use of RULs, it is possible to create that whole intersection with one texture. So, this is a caution to be mindful, think about how the textures will be used, if you can reuse a texture for something it is always the best thing to do. Always make it as simple as possible.

Now we have the textures into a DAT and you are ready to test away.
