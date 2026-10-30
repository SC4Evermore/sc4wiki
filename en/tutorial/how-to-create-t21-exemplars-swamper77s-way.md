---
title: "How to Create T21 Exemplars (Swamper77s way)"
description: ""
published: true
date: '2019-08-09T22:19:19Z'
tags: []
editor: markdown
dateCreated: '2009-01-27T07:01:04Z'
---

NETWORK PROPS To do this, you will need the Reader and the Lot Editor. I'm also assuming you know how to use the Reader, as this is intermediate modding.

This is my method of working with Type 21 Exemplars, aka Network Lots:

- Save a copy of one of the simple park lots the game has (either the grass lot or the cement lot)
- Now exit and load the lot in the Reader.
- Locate the network lot that you wish to edit. This is easily done by loading the SimCity_1.dat file from the section labeled "SimCity DAT" in the left pane and opening the Exemplar Analyzer (magnifying glass with "EX" on it). Under "Filter", have only "21 Network Lots" selected. Close the Filter Dialog Window and click "Search". After a brief moment, you should have a list of items. Now, click the "Lot" button and then click one of the items in the list. The Lot Window will show you what the textures for that network tile are, so you can see what texture the props are being placed on.
- Once you find the network lot you want, select all the "LotConfigPropertyObject" Lines. These are the props/flora that appear on that tile. Copy them to your lot you saved in earlier in the Lot Editor and then select "Re-Index LotConfig". This last command will make sure the lot displays properly when you go back to the Lot Editor to edit it. Save your lot and quit the Reader.
- Load your lot in the Lot Editor and arrange the props as you prefer. NOTE: The images you saw in the Lot Viewer in the Reader are actually 180 degrees to the actual network tile. Keep this in mind as you place the props on the lot. I build a mock-up of the network tile with the default overlays to represent the roadway of the particular tile I'm working with.
- After you have arranged your props to your liking, save and quit LE and open the lot in the Reader. Also relocate the network tile from the SimCity_1.dat file as before. Write down the number of the exemplar (the Instance ID or the FilePosition number). Now locate the number in the SimCity_1.dat file. If you wrote down the Instance ID, use the GoTo command (CRTL+G) and enter the Instance ID number into the dialog. Otherwise, you will have find the file manually as the GoTo command doesn't locate files by their number.
- Once you have located the file, copy it to a blank DAT file. Save this new DAT file with a name that you will be able to recognize, incase you need to delete it later.
- Now, delete the "LotConfigPropertyObject" lines from the network lot and copy the properties from your lot to this network lot. Lines starting with "0x00000001" or "0x00000004" are the only ones that can be on network lots. The others won't work. 0x00000001 lines are props and 0x00000004 lines are flora.
- Re-Index the LotConfig and then save and exit the Reader.
- Run the game and test out your customized network lot.

A few things to note: - Network Lots can be setup to appear in certain zones at certain wealth levels. (Charts below) - If you don't want to replace an existing network tile, assign a unique Instance ID to the following: the Exemplar's Instance ID and the property "Exemplar ID". The property "kPropertyID_LotConfigNetworkTileID" determines which network texture/model this exemplar will appear on. - The tiles seem to be chosen at random when multiple network tiles are assigned to the same texture/model. Keep clicking with the network tool and yours should show up eventually.

Zone Mappings:

`0x00=None`  
`0x01=Low Density R`  
`0x02=Medium Density R`  
`0x03=High Density R`  
`0x04=Low Density C`  
`0x05=Medium Density C`  
`0x06=High Density C`  
`0x07=Agriculture/Farming`  
`0x08=Medium Density I`  
`0x09=High Density I`  
`0x0A=Military`  
`0x0B=Airport`  
`0x0C=Seaport`  
`0x0D=Spaceport`  
`0x0E=Landfill`  
`0x0F=Civic/Plopped`

Wealth Mappings:

`0x00=None`  
`0x01=Low`  
`0x02=Medium`  
`0x03=High`

## See Also

<!-- unconverted template: Cat -->
