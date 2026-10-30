---
title: "Understanding the Traffic Simulator/Old Tutorial"
description: ""
published: true
date: '2019-08-09T02:32:17Z'
tags: []
editor: markdown
dateCreated: '2013-05-20T02:45:49Z'
---

*Editor's note: This is the complete text of the tutorial originally located at [Tutorial:Understanding the Traffic Simulator](/tutorial/understanding-the-traffic-simulator), which has become obsolete and replaced with newer information.*

> **This article is a [tutorial](/tutorials).** Originally written by [Jplumbley](/people/jplumbley), from [SimCity 4 Devotion](/simcity-4-devotion).

## Intro

<span style="font:VERDANA">The Traffic Simulator is a very complicated simulator and it is very mathematically intensive. Each Property within the Traffic Simuator has a different effect, but many of the Properties are closely tied together and must be tuned as a whole. Due to this it is recommended that you do not tamper with the simulator without the proper knowledge and the confidence in your mathematical calculations. This is an informative guide that will help describe the Properties, their functions and how everything is tied in together.

Not all properties are known about and their effects can be harmful to your game if modified in anyway. In the future some additions to this guide may be added due to new discoveries.</span>

## Properties

The most important Properties in the Traffic Simulator are:

` The Network Speed properties`  
` Commute Trip Maximum Time`  
` Pathfinding Heuristic`  
` Network Traffic Capacity`  
` Travel Type Generates Traffic`  
` Travel Type Can Reach Destination`

These properties are the heart of the Traffic Simulator because they determine what the Simulator's boundaries are and how it is to react. The other properties affect the Simulator in other ways but are not required for the Simulator to run.

## Network Speed Properties

Sample:

<table>

<tr bgcolor="cadetblue">

<td>

**Walking Speed**

</td>

<td>

= 5,0,0,5,0,0,5,0,0,0,5,0,0

</td>

</tr>

<tr bgcolor="lightblue">

<td>

**Driving Speed**

</td>

<td>

= 60,0,100,40,0,0,60,0,0,0,60,100,100

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

**Bus Speed**

</td>

<td>

= 55,0,90,35,0,0,55,0,0,0,55,90,90

</td>

</tr>

<tr bgcolor="lightblue">

<td>

**Train Speed**

</td>

<td>

= 0,110,0,0,0,0,0,0,0,0,0,0,0

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

**Truck Speed**

</td>

<td>

= 55,0,90,35,0,0,55,0,0,0,55,90,90

</td>

</tr>

<tr bgcolor="lightblue">

<td>

**Freight Train Speed**

</td>

<td>

= 0,150,0,0,0,0,0,0,0,0,0,0,0

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

**Subway Speed**

</td>

<td>

= 0,0,0,0,0,0,0,150,0,0,0,0,0

</td>

</tr>

<tr bgcolor="lightblue">

<td>

**El Train Speed**

</td>

<td>

= 0,0,0,0,0,0,0,0,150,0,0,0,0

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

**Monorail Train Speed**

</td>

<td>

= 0,0,0,0,0,0,0,0,0,200,0,0,0

</td>

</tr>

</table>

These are the speeds of the corresponding Path Types. The Path Types have their own properties and each value for the properties define the speed for the specific Network. There are 13 values and in order the values define the speed for the following networks:

` Road`  
` Rail`  
` Highway (Elevated)`  
` Street`  
` Pipes`  
` Power Poles`  
` Avenue`  
` Subway`  
` Elevated Rail`  
` Monorail`  
` One Way Road`  
` Dirt Road (ANT/RHW)`  
` Ground Highway`

Or in a table format:

<table>

<tr>

<td bgcolor="lightgrey">

**Traffic Type:**

</td>

</tr>

<tr>

<td bgcolor="lightgrey">

**Network Type:**

</td>

<th bgcolor="lightblue">

Ro

</th>

<th bgcolor="cadetblue">

Ra

</th>

<th bgcolor="lightblue">

Hw

</th>

<th bgcolor="cadetblue">

St

</th>

<th bgcolor="lightblue">

Pi

</th>

<th bgcolor="cadetblue">

Po

</th>

<th bgcolor="lightblue">

Av

</th>

<th bgcolor="cadetblue">

SW

</th>

<th bgcolor="lightblue">

ER

</th>

<th bgcolor="cadetblue">

MR

</th>

<th bgcolor="lightblue">

1W

</th>

<th bgcolor="cadetblue">

DR

</th>

<th bgcolor="lightblue">

GH

</th>

</tr>

<tr>

<td bgcolor="cadetblue">

**Walking Speed**

</td>

<td bgcolor="lightblue">

5

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

5

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

5

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

5

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Driving Speed**

</td>

<td bgcolor="lightblue">

60

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

100

</td>

<td bgcolor="cadetblue">

40

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

60

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

60

</td>

<td bgcolor="cadetblue">

100

</td>

<td bgcolor="lightblue">

100

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Bus Speed**

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

90

</td>

<td bgcolor="cadetblue">

35

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

90

</td>

<td bgcolor="lightblue">

90

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Train Speed**

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

110

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Truck Speed**

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

90

</td>

<td bgcolor="cadetblue">

35

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

55

</td>

<td bgcolor="cadetblue">

90

</td>

<td bgcolor="lightblue">

90

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Freight Train Speed**

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

150

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Subway Speed**

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

150

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**El Train Speed**

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

150

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

<tr>

<td bgcolor="cadetblue">

**Monorail Speed**

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

200

</td>

<td bgcolor="lightblue">

0

</td>

<td bgcolor="cadetblue">

0

</td>

<td bgcolor="lightblue">

0

</td>

</tr>

</table>

The speed value for the Path Types are in \# of Tiles per Unit of Time. Therefore in 1 unit of time based on the above example, a Sim will walk 5 tiles.

## Commute Trip Maximum Time

This has one value. It is the maximum trip value as stated in the title. The MAXIS default value is 6. This means if the speed of the Path Type is 31 tiles per unit of time then for the entire there and back travel distance can be 186 tiles.

Tiles per Unit of Time = 1/31 Maximum Commute Time = 6

1/31 = 6 Travel Distance = 31x6 = 186 Tiles

Due to this being there and back, this would mean the maximum distance from work being from home can be 93 tiles. Since it would be 93+93 = 186 tiles.

- Note: The Maximum Mass Transit Strategy Trip Length operates in the exact same fashion as the Commute Trip Maximum Time property.

## Pathfinding Heuristic

This is an accuracy function of the Simulator. Basically, the lower the value the more accurate and more paths the Simulator will search before selecting the route for the Traffic.

The way the Simulator calculates the path is based on a Manhattan A\* Algorithm. There are articles around the web that can explain this Algorithm better than I can.

[A\* Pathfinding for Beginners](http://www.policyalmanac.org/games/aStarTutorial.htm)

## Network Traffic Capacity

Network Traffic Capacity is exactly what it sounds like. It is the capacity for each network. The capacities are defined in the same fashion as the way the Speeds are where the values are tied in a specific order to which network it refers to:

` Road`  
` Rail`  
` Highway (Elevated)`  
` Street`  
` Pipes`  
` Power Poles`  
` Avenue`  
` Subway`  
` Elevated Rail`  
` Monorail`  
` One Way Road`  
` Dirt Road (ANT/RHW)`  
` Ground Highway`

Capcity is an important property for the simulator though it may not seem like it would be. If you are trying to re-create realistic paths, then a Maximum Capacity is definately required. Every network doesnt restrict the number of cars that are allowed on them, but this value is used to determine the congestion of the network.

For example a Avenue may have a capacity of 2500 cars a day, but it can handle more than 2500 cars before Sims start looking for other ways to get around the congestion. There are other properties that define what the Sim should do if he comes in contact with such congestion. One important one would be 1.5 Congestion vs Speed.

## Congestion vs Speed

This has an infinite number of values defined by the user. In alternating values it defines:

Value A = Congestion % of Network Value B = Speed Multiplier Adjustment

Value organization: A,B,A,B,A,B,A,B

Sample: 0,1.4,0.25,1.3,0.50,1.2,0.75,1.1,1,1,1.25,0.9,1.5,0.75,1.75,0.5,2,0.2

Translation:

<table>

<tr bgcolor="cadetblue">

<th>

<center>

Congestion

</center>

</th>

<th>

vs

</th>

<th>

<center>

Speed

</center>

</th>

</tr>

<tr bgcolor="lightblue">

<td>

<center>

0%

</center>

</td>

<td>

</td>

<td>

<center>

140%

</center>

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

<center>

25%

</center>

</td>

<td>

</td>

<td>

<center>

130%

</center>

</td>

</tr>

<tr bgcolor="lightblue">

<td>

<center>

50%

</center>

</td>

<td>

</td>

<td>

<center>

120%

</center>

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

<center>

75%

</center>

</td>

<td>

</td>

<td>

<center>

110%

</center>

</td>

</tr>

<tr bgcolor="lightblue">

<td>

<center>

100%

</center>

</td>

<td>

</td>

<td>

<center>

100%

</center>

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

<center>

125%

</center>

</td>

<td>

</td>

<td>

<center>

90%

</center>

</td>

</tr>

<tr bgcolor="lightblue">

<td>

<center>

150%

</center>

</td>

<td>

</td>

<td>

<center>

75%

</center>

</td>

</tr>

<tr bgcolor="cadetblue">

<td>

<center>

175%

</center>

</td>

<td>

</td>

<td>

<center>

50%

</center>

</td>

</tr>

<tr bgcolor="lightblue">

<td>

<center>

200%

</center>

</td>

<td>

</td>

<td>

<center>

20%

</center>

</td>

</tr>

</table>

Essentially, this will slow your Sims down for the higher congestion your network may have. If the speed gets too low the Simulator will find a faster way to get around it. Maybe by taking another road or street.

## Intersection and Turn Capacity Effect

This is a properrty that modifies the Capacity of an intersection and the 2 tiles leading upto the intersection. Hence the three values of the property. The first value modifies the capacity of the Intersection itself and the following two values modify the capacity of the two tiles leading upto the intersection.

Example for a Road:

Values = 1.5, 0.8, 0.9

This means that at the Intersection the Capacity is multiplied by 1.5, the tile next to the intersection is multiplied by 0.8 and the tile before that is multiplied by 0.9.

So, if the Capacity for the Road is 2500, then the actual capacities of these tiles are:

` Intersection = 3750 `  
` 1 Tile away  = 2000 `  
` 2 Tiles away = 2250 `

This causes the Simulation to act as if the 2 Immediate Tiles are "slow downs" for the intersection when coupled with a properly designed Congestion vs Speed Property. This setup makes is so that the intersection has a proportionally higher capacity since there are two separate routes. This increase in Capacity at the intersection tile allows for both routes to be used to almost fully and not being hampered by the intersection.

## Travel Type Generates Traffic

This is a value that determines whether or not the Traffic Type will add to congestion. It is a yes (1) or no (0) value. The order of these Traffic Types is:

` Walking`  
` Car`  
` Bus`  
` Passenger Rail`  
` Truck`  
` Frieght Rail`  
` Subway`  
` El-Rail`  
` Monorail`

In the MAXIS Original values Subway is set to not add to congestion. Buses and Pedestrians are also set not to add to congestion. There is no phyisical way for the Simulator to do a simple math calculation for busses such as 20 Bus Trips = 1 Car Trip so, each Sim will always be equal to 1 Bus Trip = 1 Car Trip no matter what. This is the reason Busses do not add to congestion and the reason they are given such a big preference when you have a high population city. This one simple calculation added as another property in the Simulator could have made a big difference.

## Travel Type Can Reach Destination

This is a set of values that does exactly what it says. It is a yes (1) or no (0) value that determines whether the Traffic Type may reach their destination. The order of these Traffic Types is:

` Walking`  
` Car`  
` Bus`  
` Passenger Rail`  
` Truck`  
` Frieght Rail`  
` Subway`  
` El-Rail`  
` Monorail`

The default game has Walking (Pedestrians) and Cars set to (1) and allows these two transit types to reach destination. So, this means your Sims will have to enter a Commercial or Industrial Lot by Car or Pedestrian.

## Travel Strategy Percentage Properties

There are four of these properties: No Wealth, \$, \$\$, \$\$\$; Each instance of this property must have 3 values, each used for a different Strategy Type. The Strategy Types are, in the order they are listed in the property: Car Preferred, Mass Transit Preferred and No Preference; and these represent the percentage chance that that particular strategy will be selected, as a share of 100%.

The Car Preferred strategy will make the Simulator favour routes that do not use Mass Transit by penalising options that use Mass Transit.  
The Mass Transit Preferred Strategy will make the simulator favour routes that use Mass Transit by penalising options that do not involve Public Transport.  
No Preference will not penalise either Strategy and the Simulator will look at both equally, generally choosing the fastest.

The values set for each *must* add up to 100% or the simulator will not function correctly.

For example, you can set Car Preferred to 50%, Mass Transit Preferred to 25% and No Preference to 25% (represented in the property as 50,25,25) but you cannot set them to 75%, 25%, 50%.

The [Commuter Shuttle Service ordinance](/ordinances) will override the values set in the traffic simulator if that ordinance is enabled.

## Trip Starting Cost by Travel Type (Mass Transit or Car Preffered)

These are the two properties that determine the Penalties to the "unprefered" Travel Strategies from 1.9. There are 9 values listed here but only two of them really get used. Walking or Car Traffic.

In the Mass Transit Prefered the second value (Car Traffic) is 1.95 as a Starting Cost for the Car Traffic. This means that when the Simulator is calculating the trip cost any path is searches for with Car Traffic, it will add this value to it. For Car Preffered the first value (Pedestrian Traffic) is given the Starting cost.

The reason none of the other Traffic Types require a Starting Cost is because no Sim generates anything other than Pedestrian or Car Traffic. The other Traffic Types are generated by a TE Lot after the initial path is found.
