---
title: "Crime Bug"
description: ""
published: true
date: '2019-08-09T02:32:11Z'
tags: ["MOD Tutorials/General"]
editor: markdown
dateCreated: '2008-10-27T16:08:23Z'
---

> **This article is a [tutorial](/tutorials).** Originally written by [RippleJet](/people/ripplejet), from [SimCiy 4 Devotion](/simciy-4-devotion).

How many times have you got the message *"Undercover Cop Unearths Den of Crime"*?  
Have you ever been urged to build a police station next to an airport, an army base, a country club, a university or a custom megalot?  
  
Do I have to cheat in order to get rid of all those messages which won't disappear regardless how many police kiosks I build around my airport?  
Well, not necessarily... but you will need to build a new police station! <http://sc4devotion.com/forums/Smileys/JasonSmilies/rolleyes.gif>  
  
  
However, let's start with the experiment I've done, and return to the modding later on...  
  
  

<hr>

  
  
Let's start with a relatively young city in a well developed region. A university has already been built, but for the purpose of this test we will bulldoze all other schools (RalphaelNinja's Mini Hogwarts and the CSX Acadamy - Bates Polytech were used to quickly raise the EQ to 200). We enter the scene in April-04. At this point no police station has yet been built, and we've just had our first riot:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug1FirstRiot.jpg>  
  
The mayor decides to build a large Maxis police station on the southern side of the city, close to the crime infested university:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug2FirstPolice.jpg>  
  
Within a year after the first staion was built (red arrow),  
the mayor decided to build another similar police station on the northern side of the city (purple arrow).  
  
With these two stations, most of the city is covered and most criminals were caught.  
Initially there were only about 2 crimes per month, but when the city grew, the number of crimes increased.  
  
The graph below shows the crimes and arrests from September-03 till August-13.  
Despite the two stations, you can see that some criminals won't get arrested (compare the blue and green graphs):  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug3CrimeGraph.jpg>  
  
The picture below show a typical six crimes per month. This also shows that the university always stays at least yellow.  
It never became less yellow than this. The criminality drops 20% every month, unless there's a new crime committed.  
However, within the vaste area of the university, a new crime is always committed before criminality disappears completely.  
  
If a criminal isn't arrested, there's a 66% chance that he will commit another crime in the next month.  
Thus, the most important thing is to have a proper police coverage.  
If the police coverage is at least 20%, all criminals will be arrested.  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug4BeforeBuildingBathurst.jpg>  
  
Now, the mayor (who shakes his head when someone mentions cheating), heard about a new police station.  
In March-14 he decided to replace the southern station with this new one.  
  
The new station is slightly larger than the large station by Maxis.  
It didn't stop the crimes from happening, as you can see from this assault at the university which took place in July-15:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug5AssaultinUniversity.jpg>  
  
However, with the new station, the police made a better job, and in February-17 the university was cleared:  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug6UniversityCleanedUp.jpg>  
  
Now, let's take a look at the graph showing the number of crimes and arrests from January-10 till December-19.  
Let's see what happened after replacing the southern station (green arrow).  
  
There are two differences. On the other hand, the number of crimes dropped from about 6 to 4 per month.  
Most importantly though, all criminals seem to be arrested now.  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug7CrimeGraph.jpg>  
  
After this the mayor could be more at ease. The police was taking care of the criminals, and in his 33rd year he decided to remove the northern station and try to manage with only the southern one (orange arrow).  
  
After 50 years in power he looked back and noticed two things:  
1. After removing the northern station, some criminals managed to escape the police network.  
2. Despite this, the criminality continued to drop.  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug8CrimeGraph.jpg>  
<http://i232.photobucket.com/albums/ee198/RippleJet/Crimebug9EducationGraph.jpg>  
  
The time scale for the criminality and education above are the same, from January-01 till December-50.  
The blue arrow shows what happened when a private school was offered and built.  
It was bulldozed a few years later in order to get the EQ down below 160 again.  
  
The reason for the criminality to drop, was the ever rising EQ, that started to climb roughly at the same time as the northern station was removed.  
Even if the city had no other educational facilities but the university, the aging population (almost all of them were older than 30 years) got an EQ of around 190.  
  
With an EQ of 200, all criminals would disappear.  
On the other hand, with an EQ of 0, as many as 40% of the R§, 15% of the R§§ and 10% of the R§§§ population are criminals.  
  
A perfect educational system is always better at handling crimes than a perfect police system. <http://sc4devotion.com/forums/Smileys/JasonSmilies/thumbsup.gif>" alt="thumbsup" border="0"\>  
  
  

<hr>

  
  
Now, let's return to the modding of this new police station, which is the [**Bathurst Street Police Station**](http://sc4devotion.com/csxlex/lex_filedesc.php?lotGET=1358) by <b>Mattb325</b>.  
First of all, the experiment above was conducted in a city not having the CAM.  
With the CAM, the number of crimes would have been fewer, due to the better Crime Attenuation from Police Protection.  
  
For each police station there are 6 properties that determine the strength of the police protection within the coverage area.  
  
The Center Strength, the Exterior Strength and the Radius determine the basic police strength and crime attenuation.  
For Maxis' large police station, the strength is 300/255 = 118% at the center and 0% at the rim of the coverage circle, having a radius of 585 m.  
  
The Dispatch Center Strength, the Dispatch Exterior Strength and the Dispatch Radius determine the ability of the police to catch criminals.  
Depending on how far from the street the crime is taking place, the police force has to move by foot to reach the criminals.  
  
As soon as they leave their car, the strength drops rapidly though.  
For Maxis' large police station, the dispatch center strength is 200/255 = 78% of the relevant basic strength where they left their car.  
The dispatch range decreases rapidly down to only 20/255 = 8% of the strength where the car is. And the dispatch radius is only 48 m (3 tiles).  
  
As a comparison, all in-game fire stations have a dispatch radius of 128 m (8 tiles), which means a fire can be extinguished in an airport, but a criminal cannot be caught.  
Police stations (and fire stations) created with the "X" Tool will get all these properties set depending on the size of the station.  
  
The Bathurst Street Police Station is larger than the in-game large station, and was given the following property values:  

<table style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;">

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Center Strength:

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

460

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Exterior Strength:

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

50

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Radius:

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

928

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Dispatch Center Strength:

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

200

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Dispatch Exterior Strength: 

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

20

</div>

</td>

</tr>

<tr>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

Dispatch Radius:

</td>

<td style="font-family: inherit; font-style: inherit; font-variant: inherit; font-weight: inherit; font-size: inherit; line-height: inherit; font-size-adjust: inherit; font-stretch: inherit; -x-system-font: none; color: inherit;" valign="top">

<div style="text-align: right;">

120

</div>

</td>

</tr>

</table>

  
The graph below compares the strength of the Bathurst Police force and that of the Maxis large station, if the university is situatued 240 m (15 tiles) from the police station. Not that the Maxis police force is only able to arrest criminals within two tiles from the street. After that the strength drops below 20%, and the criminal escapes. With the Bathurst police force, the criminal is caught if hiding within 7 tiles from the street.  
  
<http://i232.photobucket.com/albums/ee198/RippleJet/BathurstPoliceStationStrength.jpg>  
  
All new police stations made with the "X" Tool will have strength properties that increase, the larger the station is.  
If you are playing for realism, I'd recommend to use these instead of those by Maxis.  
  
Also, try to build roads/streets all around your megalots. Placing an airport in the city corner with no road around it is generally not a good idea if you want the police patrols to be able to reach criminals within the airport.  
  
In addition to these there are of course cheating stations, such as the Modd Squadd Safety by RalphaelNinja or the CSX City Hall, which both have excessively high values for all strength related properties, including the radii. Use them only if you agree on the cheating. <http://sc4devotion.com/forums/Smileys/JasonSmilies/tongue.gif>
