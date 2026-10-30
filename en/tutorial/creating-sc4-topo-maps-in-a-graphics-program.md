---
title: "Creating SC4 Topo Maps in a Graphics Program"
description: ""
published: false
date: '2019-08-09T02:32:11Z'
tags: []
editor: markdown
dateCreated: '2009-03-18T19:34:52Z'
---

## General

So, okay- they're not really topo maps. At least not yet. They lack a "collar" (the white border around such maps with all that additional information printed on it), a scale, a north arrow and any 'built environment" symbology. There's no place or feature names.

But 3RR isn't a real place, either.

*...heh...*

Topo mapping, to be completely honest, is only a secondary feature of the game. SC4 does not allow their creation, as you will see, without a great deal of effort. My guess is that most will find them interesting, so long as someone else is doing them, but few will actually go to the extent of creating them.

It is for those few that I have made this tutorial.

Note at the outset that I do not claim that this is *the way* to create SC4 topos. It is a way, likely one of many. The form I have developed is not necessarily perfect or intended to set a standard- it simply suits me. Judging by the comments, it suits others as well. Doing things the same way each time allows me to create topo maps that are uniform across the board. Ultimately I plan to have 256 of them- one for each Three Rivers Region quad. I'm focusing on the 20 or so that are "collaboration" quads first- about half these are done up to the point of detailing. I am trying to do two a day- I'll keep you posted.

Once again, this is not a task to be approached lightly. These are not simple to make, and each generally requires some hand editing. I use two graphics programs: Paint Shop Pro 8, because I am very familiar with its features and PhotoShop Elements 5.0 because it provides one image processing function that PSP8 doesn't. On that note, I'd love to hear from anyone who could figure out how to do topos in one or the other program, or even some third program altogether.

So, for the few still with me- here we go...

## The Process

The tutorial is divided into three parts. The first two, which are posted on July 9, 2007, take the steps through the point of creating the basic map. The last part, which will be posted in the next week or so, will describe the steps involved in annotating the map with placenames and features in creating a completed product.

Part Two is found [here \[linkie\]](http://sc4devotion.com/forums/index.php?topic=112.msg50351#msg50351). Part Three will be found here \[\[color=red\]linkie not active yet\[/color\]\].

I'm presuming a good degree of familiarity with the SC4 end of things, so have focused the step-by-step instructions on the graphics program end of things.

- \* \*

Open the quad from which you want to create a map in SC4. From the Mayor menu, open the "Data Views" panel, select "All Off," and display the small square map from the panel. Take a screenshot, then close SC4. Open Paint Shop Pro 8 (or whatever other graphics program you are going to use). Paste the screenshot you just took as a new image.

You're on your way!

1  
Select (1) the crop tool. Carefully (2) outline with the tool the exact edges of the small map- zoom in if necessary to align the border with the edges of the map. Confirm (3) that the outlined area is 256 pixels high by 256 pixels wide. Click inside the selected area to complete the crop.

2  
You'll be left, after the crop, with a square terrain map like this.

3  
We'll resize this map to the common dimemsions and pixels per inch (ppi) we use for all 3RR topo products. Bring up the "Resize" dialog box from the "Image" menu, then (1) set ppi at 150 and (2) the width and height at 1,024 ppi. Click (3) the "Save" button to make these changes.

4  
Do I have to tell you to save your work as you go along?

Seriously, if you are going to do, as I am, a lot of these, it will pay big dividends later to start organized. I have created a "Topos" subfolder in my main SC4 folder, and I'm filling that with subfolders numbered for each quad- this one is "236."

I then am calling each terrain image saved at this stage of the process by the quad number followed by an underscore followed by "Terrain" when I save them- thus this one is SC4\>Topos\>236\>236_Terrain. I'm saving these files in ".psp" format, which is native to PSP8 and preserves layers and other information with the save file.

Once you've saved the terrain map, you can close PSP8 and open SC4TerraFormer.

5  
You might be noticing that 236 is a "one-quad" region all by itself. I'm a big believer in using a "testbench" style of working on individual quads- it speeds things up and, for me, is less distracting. It also, I believe, helps immunize my overall 3RR region files folder from corruption- once I'm sure something works right, I shuttle it back in using standard copy\>paste techniques.

So. just click "OK" on the quad you are mapping. We won't be altering it, so you don't need to protect anything.

6  
Cliick on the "Export..." button under "Global Tools."

7  
When the "Export Region" dialog box comes up, first navigate (1) to the specific subfolder this quad's files are kept in. Next, select (2) "RGB files" as the type of output. Label (3) your new file with a unique name- I use the quad number followed by an underscore then "RGB"- in this case resulting in "236_RGB." Finally click (4) "OK."

Fire PSP8 back up, then open this file.

8  
The first thing we'll do is resize the file to our common size and ppi. Call the "Resize" dialog box, then set (1) the ppi to 150 and (2) the height and width to 1,024 pixels. Click (3) the "OK" button to input these changes.

9  
*...oh, wow, man...like, far out!*

10  
We'll start editing this colorful image by pulling (1) down the "Image" menu, then choosing (2) "Split Channel" which allows us to select (3) "Split to RGB" from the flyout submenu.

11  
Three new images will pop up: Red, Blue and Green. These in the case of PSP8 are following by a sequence number, in this case "23." The windows containing the Red and Blue images can be closed outright with out saving- they aren't needed. The "RGB" image can also be closed without a resave.

12  
Call the "Save As" dialog box from the "File" menu and navbigate (1) to the quad's subfolder. Make sure the type of file selected to be saved is Portable Network Graphics (".png"). Type (3) a unique name for the save file- I use the quad number followed by an underscore followed by the word "Green." Here that results in "236_Green." Finally, click (4) "Save." You may once again exit Paint Shop Pro at this point.

Open Photoshop Elements 5.0 and then the file you just saved.

13  
Drop down (1) the "Filter" menu. then choose (2) "Stylize." Select (3) "Find Edges" from the resulting flyout menu.

14  
The result of the Find Edges process is a new image with contour-like lines at uniform elevations. In this instance, some are from below the water level. There will also be a certain amount of "noise" in the form of small dots and other artifacts resulting from the process. Don't worry about these- we'll deal with them shortly.

15  
Bring up the "Save As" dialog box from the "File" menu and navigate (1) to the subfolder where you are keeping images connected with this quad. Make sure (2) that the type file to be save remains .png and give (3) your new image a unique name. Here, we've used the quad number folowed by an underscore followed by the words "RawLines." That gives us "236_RawLines." Save (4) the new image and close PhotoShop Elements, then reopen the image in Paint Shop Pro.

16  
At this point, you should be seeing the same thing you just saved in PS Elements.

17  
From the "Layer" pallette floating window, click (1) on the icon that creates a new raster layer. This brings up the "New Raster Layer" dialog box, where you click (2) "OK" to add (3) the new layer.

18  
Call the "Material" dialog box and choose brown (R: 128 G: 0 B: 0) as the draw color. Click "OK" to confirm the selection.

19  
Confirm (1) that brown is in fact the draw color and (2) that you are working in (i.e.: the active layer is) the raster layer you just created. For those of you unfamiliar with the use of layers in graphics programs, this means that you will only be changing that layer- other layers, which here is the "RawLines" image created in PS Elements, will remain unchanged. Think of drawing over an existing image on clear plastic or tracing paper- that's basically the same thing.

20  
Select (1) the freehand draw (paintbrush) tool and make the drawtip (2) round and (3) four pixels in size.

21  
We've zoomed in here to make the tracing process easier. Yes- you will actually just trace over the grey "rawlines" on the new layer you've created. While you should try to do this as neatly as possible, small wobbles and deviations don't really matter a whole lot. You can also ignore artifacts and places where the rawlines are smudged or make impossibly tight curves. Trust me- your country's national mapping agency (the [US Geological Survey \[linkie\]](http://www.usgs.gov/) in the US) does the same thing.

22  
Here's all the traced contour lines that are above the game water level (250 meters/820 feet in elevation) in this quad. As has been noted a couple of posts back, some quads- the flattish ones- are very simple- maybe only a line or two. Hilly or mountainous quads require more work. I can trace the average 3RR quad in hust a few minutes. A really mountainous one might take most of an hour for just this step.

23  
Now we'll add another layer by clicking (1) on the raster layer icon, confirming (2) it be clicking "OK," and checking to make sure it's positioned (3) immediately under the layer you've just drawn your contour lines on. If it is not, move it there by dragging and dropping.

24  
Next, hide (i.e.: make unvisible) (1) all layers except the new layer you've just created. In PSP8, this is done by clicking on the little "eye" icon that appears next to the layer. Confirm (2) you have the new layer selected as the active layer.

25  
Change (1) the draw color to white (R: 255 G: 255 B: 255), select (2) the flood fill (paintbucket) tool, then click (3) in the new layer to make it entirely white.

26  
Return the two layers you hid a moment ago to being visible. You should now just see your traced contour lines against a white background. The reason you don't see the grey "rawlines" is because they are behind the opaque white layer. Again, picture a stack of layers, with your traced contour line layer on top.

27  
We did that just to make that particular point. In the future, just leave (1) the "rawlines" layer hidden, then pull down the "Layers" menu and choose (2) "Merge." Select (3) from the flyout submenu the "Merge Visible" choice. This will combine your traced contour lines and the white layer into a single new layer.

28  
At this point, your PSP8 screen should look more or less like this.

End Part One.

29  
The contour lines we created are now merged with a white background, and we can now treat them as a single layer.

30  
From (1) the "Adjust" drop down menu, choose (2) "Blur," then select (3) this action again from the flyout submenu.

31  
You can see that this makes our contour lines more smooth and uniform.

32  
Return to the "Adjust" menu and select "Negative Image."

33  
This creates an interesting variation of our image...

34  
...and allows us to "thin" our contour lines. This is done by again going (1) to the "Adjust" menu and choosing (2) "Edge Effects," then selecting (3) "Erode" from the flyout submenu.

35  
The effect of the "Erode" procedure is pretty dramatic. Our contour lines are now much thinner and sharper. Return the image back to the brown lines against a white background by dropping down the "Adjust" menu and selecting "Negative Image" again.

36  
This is the first point where you'll find yourself doing some close editing. Using "Erode" will sometimes leave, in places (1) where the lines come close together, a brown smudged area between them. To correct these places, make sure (2) your "draw" color is white (R: 255 G: 255 B: 255). Then, select (3) the "Draw" (paintbrush) tool. You'll need to set (4) the tooltip at two pixels, and sometimes to just one. Then, color over (5) the smudged areas until the contour lines are clean and uniform on each side.

37  
Here are our thinned and cleaned up contour lines.

38  
Let's save here. Call the "Save As" dialog box and navigate (1) to the subfolder that your are working from. Select (2) Paint Shop Pro's native .psp save file format. Next, choose (3) a uniform file name- we use the quad number followed by an underscore and the words "ContourLines, giving us here "236_ContourLines." Click (4) "Save" to complete the task.

39  
Next, reopen the "236_Terrain" file we saved at the start of our tutorial. When it is displayed, drop down the "Selection" menu and select the "Select All" menu choice. When the dashed line appears around the image, press \[ Ctrl \] and \[ C \] to copy it to the Windows clipboard. Close the "236_Terrain" file.

40  
Now we'll return to the "236_ContourLines" image. From (1) the "Edit" dropdown menu, choose (2) "Paste" and then select (3) "Paste in New Layer" from the flyout submenu.

41  
When you first add the terrain image layer, you can't see anything underneath it. Making sure (1) that it is the active layer, adjust (2) the transparency index to "85." You'll see (3) the contour lines appear.

42  
They still appear "thick" and out of proportion, though. We'll make sure we are working in the layer that they are are in- in this case the "Merged" layer.

43  
Just as before, we'll select "negative Image" from the "Adjust" menu.

44  
Then select "Erode" from the flyout "Edge Effects" choice of the "Effects" menu.

45  
Complete these contour line thinning steps by reversing the negative image through selecting "Negative Image" from the "Adjust" dropdown menu.

46  
Now the contour lines are properly thinned, but have become indistinct in the process. We'll correct this by returning (1) to the "Adjust" menu and choosing (2) "Sharpness, then selecting (3) "Sharpen" from the flyout submenu.

47  
The final step in adjusting the contour lines is to immediately repeat the last action one more time, except this time selecting "Sharpen More" from the flyout submenu.

48  
Our topo map now looks like this. The last processing steps involve deliniating shoreline and river and stream banks, and making water bodies a uniform color.

49  
Select (1) the vector line (pen nib) drawing tool. Set (2) the line width to two pixels and make sure (3) that "Anit-alias" is checked. Call the "Material" dialog box and select (4) a medium blue (R: 64 G: 64 B: 255) as the draw color, then click (5) "OK" to save this choice.

50  
Confirm (1) that your medium blue color is the draw color. Because you are about to create new vector objects, which will automatically establish a new layer, simply confirm (2) that the topmost layer is the one currently selected. Turning to the image, you'll note that the water's edge (3) on larger bodies of water is indistinct, as the "land color" extends in the game terrain map for some distance offshore.

51  
Create a new vector line down from the top of the image then add and drag nodes to make it conform to the shoreline. This looks much harder than it actually is in practice. While teaching vector line drawing is beyond the scope of this tutorial, it's just one of those things, like riding a bicycle, that you have to just "get" one time- after that, it's easy. You may, though, find yourself referring to the quad in the game itself to work your way through indistinct areas of shoreline.

52  
Here's the southern end of Pratt Island completely outlined. Note the offshore "land" color.

53  
Here's the little pond on the main island outlined. If you look back at earlier images in this tutorial, you'll see that we also edited, along the way, the contour lines in the area of the lake.

When I look at these close-ups, I am always stunned at how well the game terrain map captures the small nuances of ground features,

54  
All the shoreline outlining is now done.

55  
We add the two stretches of stream. For small rivers and wide streams, I use (1) a three pixel width drawtip. For other streams, creeks and brooks, I set (2) the pixel width to 2.

56  
The final step involves creating one last raster layer as the new top layer.

57  
Once this layer is set up, hide (make unvisible) all the layers below the vector layer you just drew the edges of your water bodies and rivers and stream on.

58  
Call the "Material" dialog box again and set up a light blue (R:64 G:255 B:255) as your working color.

59  
Making sure you are in the top layer and the working color you just set is applied, select (1) the flood fill (paint bucket) tool and click it (2) in the middle of the water body you want to color.

60  
Last, unhide (make visible) all of the layers except our original background layer. The topo map can now be saved as is for future editing or merged down to a single layer for use in your regional play.

Leaving the graphics program behind, what we've created looks like this.

  
In a subsequent tutorial, we will annotate this map with features and labels.
