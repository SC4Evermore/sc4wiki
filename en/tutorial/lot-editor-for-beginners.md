---
title: "Lot Editor for Beginners"
description: ""
published: true
date: '2019-08-09T02:32:13Z'
tags: ["LOT Tutorials"]
editor: markdown
dateCreated: '2008-10-20T19:17:06Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [Threestooges](/people/threestooges), from [SimCity 4 Devotion](/simcity-4-devotion).

For this tutorial, you will need the Lot Editor and Plugin Manager installed (as well as SC4 naturally). This tutorial begins at the point you would be at if you had just created and exported a model in the BAT (or other similar tool). If you just want to work on a lot you may jump down the page a bit (but the stuff on the plugin manager is useful to know too).  
  
To make this easier, clear your plugins folder. This will reduce the number of props at your disposal, but will make things easier to work through (and also let the LE load faster). For the purposes of this tutorial, I have left the following two model files. I believe these came with the Lot Editor, so you should have them somewhere too. If not, you may use one of the buildings already on the lot (we'll get to that in a moment) or use one you have made in the BAT.  
<http://img130.imageshack.us/img130/4254/pic1fk3.jpg>  
  
Begin by opening the Plugin Manager. You will be greeted with the following screen. Notice the bar the arrow is pointing to: by hovering your mouse over it, it will turn into a double arrow and, by clicking and dragging, you can adjust the left and right window sizes. This is useful to see longer file names (on the right) or sub categories in the 'descriptor' tree(on the left).  
<http://img130.imageshack.us/img130/4467/pic2ac5.jpg>  
  
By default, 'models' is selected on the left. This results in all available models (at least, all that are in your plugins folder) being shown and placed in sub categories. For the purposes of this tutorial, select 'Stone House' and drag it into the medium wealth residential category (or whatever category you want... it will just result in some different options later). Note: models can be turned into props for the LE here too. Close to the bottom of the descriptor tree is a selection that says 'Prop'. Put the model in there and you'll have a new prop to use.  
<http://img130.imageshack.us/img130/9357/pic3yv3.jpg>  
  
When you release the mouse, the following screen will pop up. This allows you to define various values for your model:  
<http://img212.imageshack.us/img212/5602/pic4bx1.jpg>  
  
-Building Value: value of the building that will be used to calculate taxes  
-Bulldoze Cost: how much it will cost to bulldoze the building  
-Capacity Satisfied: haven't used it much, but it deals with RCI demand  
-Construction Time: how long (in game days) the building will take to build  
-Exemplar Name: How the model will be known in the LE  
-Flammability: higher number, greater chance of catching fire  
-Max Fire Stage: how long it will burn before being destroyed  
-Pollution at center/pollution radii: how much pollution the lot will produce, and how far out it will spread  
-Power/Water Consumed: just what they say- the bigger the number, the more that is used  
-Worth: the value of the property that will go toward damage calculations if destroyed in emergency  
  
There will be other options not shown here (education values if you put it in a school category, health if you put it under Hospital), you can play around with these all you want.  
  
IMPORTANT: make sure you put the model into the category of the building you want to make. When editing a lot in the LE the buildings available are determined by the type of lot (which comes from where the model is placed here in the plugin manager).  
  
Once you click 'OK' you will get a message saying 'Plug-In Saved Successfully' and if you click on the appropriate category on the tree on the left, you should see your model there. If you look under 'file type' in the window on the right it says "SC4DESC." It is no longer a model, but a descriptor file (remember the tree on the left was called a descriptor tree). What this means is that your model has had certain descriptions attached to it, and will influence properties of the lot in-game.  
<http://img212.imageshack.us/img212/6940/pic5mo5.jpg>  
  
Now I know this is a tutorial about the Lot Editor, but so far all we have done is worked around with the plugin manager... this is about to change.

## Lot Editor

It is important to know the whole process though, especially if you get involved with the BAT (you'll have to get your models in the game somehow).  
  
Now go ahead and close the plugin manager and open the Lot Editor and...you will get the picture below. This can be a bit daunting if you aren't familiar with what you are looking at. The LE does not start you with a blank lot. It asks you to choose one to edit. First, a bit about how it is organized:  
  
-the string of letters and numbers on the left is the lot's hexadecimal ID (I think that's what it's called) but it's basically how the lot is identified in the game.  
-Just to the right of that (CO\$\$\$1_2x2...) is the type of lot (Commercial Office), wealth level (\$\$\$), growth stage...I think (1) followed by an underscore and the lot size (2x2)  
  
<http://img130.imageshack.us/img130/3226/pic6yu6.jpg>  
  
It can be a bit annoying, but it gets easier when you figure out what you are looking for. Back in the plugin manager we put our model in a medium wealth residential category. You can scroll down the list if you want (go ahead, and see the options), but it can take a while if you are searching for something in particular. At the top of the window is a "find" field. This will find direct matches to whatever is typed in. It will find the first match going straight down the list, but if that is not what you want, you can hit the enter key and it will move to the next matching entry.  
  
The residential code is 'R' and medium wealth is '\$\$'- go ahead and type it in as shown in the pic below (it's not case-sensitive as far as I know).  
  
<http://img212.imageshack.us/img212/3524/pic7ma7.jpg>  
  
Notice that the first item to come up is a R\$\$\$ lot, we don't want that, so hit enter or use the scroll bar (or just type in the highlighted file name as shown in the pic below) so that you find this lot: R\$\$4_1x2  
  
This will give a 1x2 lot with a medium wealth classifcation. Select it and hit OK  
  
<http://img130.imageshack.us/img130/4297/pic8bx2.jpg>  
  
There is your lot. It may look familiar from the game, but we will soon change that.  
  
But first, we should go over the basics of this window.  
  
<http://img212.imageshack.us/img212/9369/pic9ll6.jpg>  
  
There are a number of tabs in the bottom left corner (Base Texture, Building, Flora, Land, etc) and each of these allows you to maniuplate a particular aspect of the lot. Each aspect will only be adjustable if it's tab is selected. This is highly useful since the layers will tend to stack up pretty quick.  
  
Lot: this is the one that is shown in the pic below. It allows you to alter such things as the lot's dimensions, if it will grow on a corner lot (where it says "corners"), the slope tolerance and type of retaining wall it will use.  
  
Base Texture: gives you the option to add different types of surfaces to the lot. Each tile of the lot must have a base texture. (But there are lots with clear textures you say... there are a few ways to do this, the most reliable one that I am aware of is to use ilive's reader and removed them after using the LE; but this is outside the scope of what we need to to for the basics. So to keep it simple, all tiles need a base texture).  
  
Overlay Texture: Additional textures you can put on top of base textures to add diversity to the tile. In the current lot there is one at the front of the lot (it makes the path and brown foundation for the lot)  
  
Building: we'll come back to this one in just a moment, but it allows you to select the building to place on the lot  
  
Props: The life of a lot. I believe it was Cerulean or Simgoober (objection: hearsay: don't quote me on it, and please let me know if that's wrong so I can change it, I found it in <a linkindex="44" href="http://sc4devotion.com/forums/index.php?action=search2;topic=2248" target="_blank">this</a> thread) that said that the "props are meant to tell the story of the building." Since we have cleared out the plugins folder, such additions that others have made will not be available, but we will come back to this later.  
  
Flora: trees that will grow on the lot  
  
Land/water: I grouped together because they are usually used together. These options allow you to designate certain tiles that MUST be placed on land or water. The land tile(s) must be on land, and water tile(s) must be on water. To see these used, you can open the standard beach lot.  
  
Also, at the bottom left part of the LE window you will see 4 buttons:  
Open: opens a lot to edit  
  
Save: saves the lot in its current form under its current name  
  
Save As: saves the lot under a name you designate (making it something descriptive is useful: lot dimensions, wealth, etc) and note that the name is just what is shown in the plugin folder, the descriptions used in the game are changed in either the SC4Tool or in ilive's Reader.  
  
Exit: exits the LE  
  
MAKE SURE that you click the button you mean to hit. Once you save over a previous version of a lot, you can't get it back (unless you re-download/reinstall it). A good piece of advice for that would be to make a copy of the file you intend to modify before you start just in case.  
  
<http://img212.imageshack.us/img212/399/pic10qq6.jpg>  
  
So let's see if we can get our building on the lot. Go to the building tab and click "Replace Item" which will open the list of available buildings. That's odd, our building (Stone House) isn't listed. There is a good reason for this (and no, nothing went wrong earlier). In order for a prop/building to be available to be put on a lot, the dimensions of the lot itself must be bigger than the building/prop to be added. The model appears to be slightly larger than our current lot, so we need to make our lot larger. Click "Cancel" and go to the Lot tab.  
<http://img130.imageshack.us/img130/2875/pic11pz8.jpg>  
  
Change the lot size to 3x3 (I know mine says 5x5, but I did that just to ensure the building would be available). Note in the two windows that the road got longer and the black box on the border of the lot on the right got bigger too as a result of changing the dimensions. This may result in some parts of the lot being off-screen. You can use the two sets of zoom buttons (one for each window) and the rotate and move tools that work on both windows. Note: to turn off the move tool, just click the hand again.  
<http://img130.imageshack.us/img130/5516/pic12py5.jpg>  
  
When you have changed the lot size, go back to the building tab and look for the building (it should be there as shown...if not, make the lot bigger, it can always be made smaller after that, if that doesn't work, go back and try the plugin manager steps again).  
<http://img519.imageshack.us/img519/8290/pic13uy0.jpg>  
  
Select the building. The original house will disappear, and you will now be able to place your new building. Once you have placed it, you can still move it around.  
<http://img519.imageshack.us/img519/9495/pic14uu1.jpg>  
  
Now then, you might want to start with a fresh lot, without everything left over form the original lot.  
First, Select the base texture tab. In the right-hand window drag a box around the two tiles shown this will select both (you can select them individually by clicking on just one). Hit the delete key, and they are gone.  
  
Next, go to the overlay textures tab and do the same to any remaining overlay textures.  
<http://img130.imageshack.us/img130/5548/pic15uf0.jpg>  
  
After you have done that, all that's left are some little squares (and rectangles too). These represent props on the lot. drag a box around them and note how the prop will get a white outline to show it will be selected. Also note how the prop must be fully encircled by the box to be selected and not just touching it. Select and delete all of the props on the lot (unless you see some you want to keep... you can move these wherever you want...as long as the prop tab is selected though).  
<http://img519.imageshack.us/img519/6357/pic16vg5.jpg>  
  
There are still two little green things left. These trees count as flora. Select the flora tab and you can select and delete these trees too.  
<http://img212.imageshack.us/img212/3664/pic17bc4.jpg>  
  
There: a fresh lot to play with.  
  
Let's start with the basics: the base textures. I thought I would make this a lush, green, lot. Under the Base Textures tab, click Add Item and select the texture you like (they are ordered numerically by the 'hex' number)  
<http://img519.imageshack.us/img519/2551/pic18ja7.jpg>  
  
Not every tile must have the same texture, but I chose to do it that way, just click on one tile of the lot and the texture will be placed. Go ahead and fill all the tiles with the textures you want. Note: for larger lots, plopping each single base texture can be a pain if they are all the same. You can plop a few and then select them, hit 'duplicate selected', and plop the duplicate to cover more ground faster  
<http://img212.imageshack.us/img212/4461/pic19fq0.jpg>  
  
If you look at the display on the left, the building now has a nice green lawn. However, I think that a path to the front door would be nice. We have already plopped down the base textures, but we can add overlays too. I chose the overlay texture shown in the pic below and placed it over the two tiles shown. Note how there is now a path going toward the front door. This allows many more options than would be offered by base textures alone.  
<http://img519.imageshack.us/img519/9687/pic20mc3.jpg>  
  
Now then, as I quoted earlier, props tell the story of the building. Piles of garbage will make it look rundown, a pool might make it look rich. Here, there are many options (many more if you use prop packs from other lots you have downloaded/made).  
  
One thing you should keep in mind here, if you plan to release your lots to the public, is that unless they have downloaded the same lots as you, they may have to track down the dependencies. If you have used one prop from each of five or so packs, the dependency list can climb quickly. If you are using it for your own personal enjoyment, go wild, but remember you must keep the source of the prop in your plugin folder otherwise it won't show up in game.  
  
Click Add Item and it will open the prop list. This is also alphabetized and will become easier to navigate with time. Similar to the buildings, they have: hex number, name, size, some form of description. If it is from a prop pack, it may have the name/initials of the person that made it in there too (which is a good way to search for specific props)  
<http://img169.imageshack.us/img169/7015/pic21sq6.jpg>  
  
I used these two selections to add the flower boxes out front and the flowers in the interior.  
  
When placing a prop, you may wish to rotate it so it will fit better. To rotate a prop, us the Page Up/Page Down keys on the keyboard. I rotated the planters to have them align with the path and placed some flowers inside the courtyard.  
<http://img169.imageshack.us/img169/3730/pic22sh7.jpg>  
  
Now I want that row of flowers to be duplicated on the other side of the courtyard. I could just plop a few more flowers over there, or I could just duplicate what I've already placed and move it over as a group. Drag a box around the flowers and click duplicate selected. Move the selection (by clicking and dragging it) to the other side of the courtyard.  
<http://img212.imageshack.us/img212/2176/pic23rx1.jpg>  
  
In doing so we moved them out of view. Rotate the view so you can see them in the display on the left.  
  
Here's a problem: the flowers appear to disappear into the building. This is caused by the building's LOD (which I think stands for Level Of Detail). The LOD is what the game 'draws' the model on. It will obstruct anything else that gets in its way. You can either change the LOD for this model (takes a while, and is outside the scope of this tutorial) or you can work around it. Just move the flowers until they are completely visible then rotate around them to make sure there are no other problems that you can see.  
<http://img519.imageshack.us/img519/9269/pic24rn2.jpg>  
  
I added a few trees (from the prop menu) but thought I would also point this out: It is somewhat of a secret that each of the landmarks in the game comes with a "hidden gnome" that will appear somewhere on it at some point during the game year. If you want you can include these on your lot, but this is just to let you know they exist (and to let you know what they are).  
<http://img169.imageshack.us/img169/6130/pic25ef0.jpg>  
  
I also added a white picket fence. You can find it by searching for fence in the prop menu's find box (it's one of the first few choices, just keep hitting enter until you find it). I placed it on the lot just to make a boundary, rotating it to make the corners and head up the sides of the lot. I also used it to kind of cheat with the LOD as well. Look at the two sections of fence going along the front path. These are the same prop that borders the lot. They are the same length but are sheared off by the building's LOD letting them appear to go into the wall. You can use this trick or you can just use shorter props (if they exist). The thing is to make sure it is something you like.  
<http://img212.imageshack.us/img212/7964/pic26wm0.jpg>  
  
Now then, you probably want to save your hard work, and you see to buttons near the bottom left to do just that: Save, and Save As.  
  
DO NOT CLICK SAVE UNLESS YOU WANT TO OVERRIDE THE ORIGINAL LOT. If, for example, you were working on the basic elementary school lot, the original school would no longer exist as it was.  
  
If you are planning to make a new lot to act as an option for the existing one, click Save As.  
<http://img519.imageshack.us/img519/5142/pic27xp3.jpg>  
  
It will prompt you to select a name to save it under. I use the abbreviation TS to locate my lots and then some sort of useful description. You can name it whatever you want.  
<http://img169.imageshack.us/img169/9628/pic28rv4.jpg>  
  
This should conclude the Lot Editor tutorial. You can use such things as the SC4Tool to further tinker with your lots, but again, that goes beyond the scope of this basic tutorial. If you have any questions, comment, concerns, etc, (or if you have anything else you would like to see in this tutorial) please let me know. Hope this helps.
