---
title: "Creating Prop Families"
description: ""
published: true
date: '2019-10-24T17:01:19Z'
tags: []
editor: markdown
dateCreated: '2008-10-28T05:27:23Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [Jeronij](/people/jeronij), from [SimCity 4 Devotion](/simcity-4-devotion).

Hi everyone, after some questions over at [SC4 Devotion](/sc4-devotion), I wrote up a little tutorial on prop families. I made it mostly for my own use as the tutorial I used to use is a little out of date (its the one on the [STEX](/stex)), but thought it might be useful for Jeronij's site if he wanted it. I'm not sure if there is an existing tutorial that covers the same material (if so then this one is redundant)  
  
I've posted it here first for people to preview if they want, and comment on whether or not its suitable for release. I think it probably covers some existing material, but I could leave it out if necessary.  
  
Also, since its based on what I understand of prop families there may be some mistakes, inaccuracies or omissions. So I didn't want to post it publicly without letting people here see it first and having option of veto. Especially since most if it is BSC material. I thought it might be useful to have a current compilation if there wasn't already one.  
  
<span style="font-weight: bold;">Tutorial: Using Existing Props in New Prop Families</span>  
  
This tutorial expands on my basic outline of how to make prop families. It also explains how to make a copy of prop files and add them to a new prop family while leaving the original files intact. I have learned the hard way to never modify core dat files, or dependency files from other creators.  
  
Disclaimer: this is a new tutorial and there may still be some minor errors or omissions. If you find any please let me know so I can correct them. Its also not official material, it is just how I do this process. Other people may have different methods. None of this material is my original work (except the compilation of it), it has been a long process of research by many people to work this out. Many of those people were BSC members.The tutorial assumes the audience is fairly familiar with Ilive's Reader and its functions.  
  
<span style="color: darkblue;"><span style="text-decoration: underline;">What is a Prop Family?</span>  
  
When using the Lot Editor, you can place props on a lot. When you place an ordinary prop it always uses the same prop when the lot is plopped or grown in the game.  
  
You can make your lots more interesting by using prop families. A prop family contains a number of different prop models. If you place a prop family on a lot, each time you plop or grow the lot in the game, it will choose a random prop from the family. This way you can make one lot, but have it look different each time it is used in the game.  
  
You can make your own prop families, but it requires a bit of modding. Its not too difficult though.  
  
<span style="text-decoration: underline;">Prop Family IID Range</span>  
  
If you are going to create your own prop families, then please ask Barbyw for an instance (iid) range for your families. Each prop family must have a unique iid, and using your own range will ensure that yours don't conflict with anyone else's. There is a request thread [here](http://www.simtropolis.com/forum/messageview.cfm?catid=109&threadid=8226).

  
  
It is the prop family iid that links all the props into the family. This is how the game knows which props are in the list for it to pick from. </span>  
  
<span style="text-decoration: underline;">Making a prop family from existing props</span>  
  
I do not create my own props. I must use props that others create, and these are usually found in published prop packs. Lets say I find some nice props, and I want to put them into a prop family.  
  
I will assume that I already know the names of the props I want to use, and which prop pack they are in. I will also assume that the original creator has said its ok for me to use his or her props.  
  
I'm going to use for my example Cycledogg's four Street Trees that can be found in his BSC CP PropPack Vol02 (CP_PropPack_Vol02.dat). The prop exemplar names I want are:  
CP_SpruceTree_StreetA  
CP_SpruceTree_StreetB  
CP_SpruceTree_StreetC  
CP_SpruceTree_StreetD  
  
Firstly I start Ilive's Reader and then open BSC CP PropPack Vol02. I locate the four exemplar files that I want and highlight them in the middle pane.

  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image1.jpg>  
  
Then (still in the middle pane and with my mouse over one of the four exemplars) I right click, and from the pop-up menu, select Copy Files.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image2.jpg>  
  
Now I create a new dat file (go to the File menu and select New)  
  
In the middle pane of the reader, I right click and choose Paste Files. The screen should look similar to the picture below.  
  
Now I have a new file with the four prop exemplars in it.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image3.jpg>  
  
At this point we have a problem. You may notice that the TGI numbers of these exemplars are exactly the same as those in Cycledogg's original prop pack (compare the images above). We need to make sure our new exemplars have their own unique TGI numbers. (TGI: Type Group Instance)  
  
To do this, in the middle pane, I select all four exemplar files, right click and select Generate New Group and Instance.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image4.jpg>  
  
The results should now be similar to below. Notice the exemplars now have different TGI numbers.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image5.jpg>  
  
At this point ReIndex and Rebuild the directory file (in the middle pane, right click, and pick ReIndex. Then, again in the right pane, right click and pick Rebuild Directory File).  
  
Then save the new dat file before something bad happens (go to the File menu and choose Save As). Give it a good name. I'm going to call mine sam_CP_SpruceStreetTrees_propFamily.dat With this name I can tell:  
It is a file I modified  
It contains prop families  
The original creator was Cycledogg (CP)  
It contains the Spruce Street Tree prop exemplars  
  
These exemplars should not now conflict with any other in game file. But it still doesn't do what we want. The props still belong to the families that Cycledogg originally gave them.

  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image6.jpg>  
  
To change these, I select the first exemplar file in the middle pane. Then in the right hand pane, I double click the Building/Prop Family property. The results are shown below:  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image7.jpg>  
  
Since this is a new exemplar file I can safely delete the iids that Cycledogg added (since they are still in the original file), and add my own.  
  
I will delete the first rep (the first white cell under the values list) by clicking on it, then clicking the Remove button.  
  
I will delete the second rep the same way.  
  
I will then find the next available prop family iid in my range, which is 5A100050. I overwrite the third rep with 0x5A100050.  
  
Then I click the apply button on the lower right, then click the apply button on the lower left.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image8.jpg>  
  
Your results should look similar to the picture below. Note the value in the Prop/Building Family property now appears as we wish it to.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image9.jpg>  
  
But we have only done the first exemplar out of four. So at this point, you will need to change the other three in the same way (ie pick the file to modify in the middle pane, then in the right pane, find the Prop/Building Family property, double click it, delete any unwanted values and add your own)  
  
Then all four of our new exemplars should belong to our new prop family.  
  
At this point it is wise to ReIndex and Rebuild the directory file, then save your dat file.  
  
We now have our new props in a new prop family. They should be available in the Lot Editor, listed under the family iid.  
  
<span style="text-decoration: underline;">Advanced Feature - Naming Your Prop Family</span>  
  
We can if we wish, give the family a name by adding a Parent Cohort file, using the method outlined by Jeronij. <span style="color: darkblue;">This name will appear in the list of prop families in the Lot Editor, which makes choosing the right family for our lots much easier.</span>  
  
In my example above, the iid of my Parent Cohort file must be 6A100050 (because the family iid was 5A100050, I must add 1 to the left most digit). Then in the Lot Editor, the new family will appear in the list with its name.  
  
To do this, I'm going to copy a Cohort File from one of my previous prop families. (Open the file that contains the family, find the Cohort file to copy in the middle pane, right click, and select Copy File)  
  
The Parent Cohort file should appear in the middle pane before any of the prop exemplars that use it. To do this, in the middle pane I'm going to click on the first exemplar file in the list. Then I right click and choose Paste File.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image10.jpg>  
  
This will put the Cohort file as the second item in the list which is not what we really want.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image11.jpg>  
  
So I will now copy the first file in the list (the exemplar file above the cohort file), click on the parent cohort file, and paste the exemplar file.  
  
This will put a new copy the first exemplar file below the parent cohort in the list. Now we have two copies of the same exemplar, so I can safely remove the copy above the parent cohort file in the list. (In the middle pane click on the file to be removed, then right click and select Remove File)  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image12.jpg>  
  
Now all our files are present and in the correct order, but I need to make some changes to the Cohort file. First I change its instance id to 6A100050. (In the middle pane, click on the Cohort file. Then on the Reader's top button bar, click File Info button. On the pop-up screen click the Edit button. You will get a new pop-up screen. In your head or on a piece of paper, take your prop family iid and add 1 to the left most digit (my prop family iid was 5A100050 so the new number will be 6A100050). Type this new number into the Instance box of the latest pop-up screen, then click ok. (see the second picture below)  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image13.jpg>  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image14.jpg>

  
  
Close the File Info box.<span style="color: darkblue;"> Its a good idea to Save.</span>  
  
Now I need to alter some of the properties in the Parent Cohort file. (If you click on the cohort file in the middle pane, the properties are shown in the right pane). Note in the picture below the properties of my cohort file have incorrect values (because it is just a copy from another family)  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image15.jpg>  
  
First I need to alter the Building/Prop Family property to match the prop family iid that I have used for the family, ie 5A100050  
  
In the right pane, double click the Building/Prop Family property. There should only be one Value box. I change this to match the prop family iid and apply the changes.  
  
Now I alter the prop Exemplar Name property. To do this, in the right pane I double click it, and in the values box, I give it the name I want. This is the name that will appear in the prop families list in the Lot Editor. My personal preference is to put the family iid at the front of this name, so that I always know which family I am using in the LE. Apply the changes.  
  
<span style="color: darkblue;">Tip from Deadwoods: make sure the family name is not too long or you won't see all of it in the family window in the LotEditor. </span>  
  
The Cohorts properties should now look similar to the image below.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image16.jpg>  
  
Re-Index, Rebuild the directory file and Save.  
  
Our prop family file is now done. We should be able to use it in the Lot Editor now.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image17.jpg>  
  
Note: Our prop family only contains the descriptor files for our props. The model files are still in the original prop pack, so this prop pack will still be a dependency of any lot that that uses this prop family. Unfortunately this may not be detected by some dependency scanners. I always keep a spreadsheet of the prop families I have created and the prop packs the models came from. This way I can make a complete dependency listing for them.  
  
<span style="text-decoration: underline;">Appendix:</span>  
  
One other thing I should have mentioned - when I create new prop exemplars from existing props I usually change their exemplar names. Every prop exemplar is listed in the Lot Editor props list (the list that appears when you click the Add Prop button). This can clutter up the menu if we keep making copies of props, and make things hard to find.  
  
Usually I add to the original exemplar name a prefix which indicates the new props are from a family. This way I know not to use them when adding props from the prop list (as opposed to the prop family list). For example, I might rename the first prop exemplar above to zz_spf_CP_SpruceTree_StreetA  
  
zz\_  
this should make the prop appear towards the end of the Lot Editor's prop list, out of the way of the regular props  
  
spf\_  
short for sam's prop family (indicates its a prop family prop made by sam)  
  
CP_SpruceTree_StreetA

  
indicates the original prop exemplar this prop is a copy of, and that it was made by Cycledogg.  
  
I renamed the exemplars I used in my prop family and you can see from the picture below, the individual props now appear at the end of the Lot Editor's prop list, well out of my way.  
  
<http://img.photobucket.com/albums/v154/sam71/tutorials/spf_image18.jpg>  
  
This is purely a personal preference of mine, but other people are likely to have different methods.
