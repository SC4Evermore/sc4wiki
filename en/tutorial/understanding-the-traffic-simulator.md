---
title: "Understanding the Traffic Simulator"
description: ""
published: false
date: '2019-08-04T05:46:34Z'
tags: ["Transit Networks", "MOD Tutorials/Transport", "MOD Tutorials/Simulator"]
editor: markdown
dateCreated: '2008-05-28T20:50:11Z'
---

This article, *A Guide to the Operation of the Traffic Simulator*, was written by [z](/people/z), and originally posted at [SC4 Devotion](http://sc4devotion.com/forums/index.php?topic=10261.0).

## A Guide to the Operation of the Traffic Simulator

The **traffic simulator** is one of the least understood components of [SimCity 4](/simcity-4). This is partly because understanding of how it works is not required for modding other parts of the game, and partly because many of its effects are fairly subtle, and are often second- or third-order. This guide will attempt to summarize our current knowledge about the traffic simulator, both in terms of how it works as a whole, and also in terms of what each of its individual properties do. Since it is the properties of the traffic simulator that are accessible to us, and that allow us to tune it in various ways, these properties will form a central part of this description, and will be boldfaced whenever they are used. This post contains some material from other places; I have gathered it all together here for ease of reference, and also to make this description more coherent. There are undoubtedly some errors in here, and some omissions; if people spot these, please post in [this thread](http://sc4devotion.com/forums/index.php?topic=10261.0), and such errors or omissions can then be corrected.

This guide has not been written in isolation, and in fact relies to a very large extent on previous work done in this field. Specifically, much of our current understanding of the traffic simulator has come from work done by [the7trumpets](/people/the7trumpets), [Tropod](/people/tropod), [jplumbley](/people/jplumbley), and [Mott](/people/mott), among others; what I have done has merely been to build upon the excellent work done by these gentlemen, and would not have been possible without their efforts.

Most people are aware that changes in various parameters in the traffic simulator can have a significant effect on their game, but it's often not obvious how significant that effect is. Consider the following Pop & Jobs graph:

<div align="center">

<figure>
<img src="/_files/images/zz20.jpg" title="zz20.jpg" />
<figcaption>zz20.jpg</figcaption>
</figure>

</div>

This is a graph of the Lakeview neighborhood in the city of Chicago. Lakeview was originally built with a pre-alpha version of Simulator Z; it had the large capacities and long commute time of today's *Simulator Z*, but it still had the *pathfinding heuristic (PH)* of its CAM Simulator predecessor. (The pathfinding heuristic will be discussed in detail later.) It was quite stable in this state, which you can see at the beginning of the graph, where all lines are basically flat.

The city in general looked pretty good and seemed to to function rather well. At this point there were just a couple of city blocks where there was a lot of abandonment and rebuilding going on. I eventually realized that I needed to adjust the PH, which I lowered to the value of 0.003, which was thought to be the perfect pathfinding value at the time. This is the point where the R\$\$ starts to rise rapidly and the R\$ begins to fall rapidly; there is also a slight upward movement in the CS\$\$\$. All this represents upgrading; either buildings that were originally R\$\$ but downgraded to R\$ were upgraded back to R\$\$, or new R\$\$ buildings replaced existing R\$ buildings. Throughout all this, total population remains steady at around 835K.

A very important point to note here is that though the population of the city was changing significantly, as evidenced by the graph, I was unaware of the extent of the change at the time. Only since the end of October, when I began doing the PH experiments that are illustrated in the [Traffic Simulator Z Development and Theory](http://sc4devotion.com/forums/index.php?topic=5382.0) thread starting with [this post](http://sc4devotion.com/forums/index.php?topic=5382.msg283986#msg283986), have I even been aware of these population changes. And yet their significance is obviously great; the difference in residential desirability that they represent has a profound effect on the game. But these changes aren't always accompanied by abandonment, and are therefore easily missed. Similarly, if a player uses a traffic simulator that is not properly tuned, there are no changes to see; there is just a general lack of desirability and its attendant effects that are difficult to explain. Rarely is the traffic simulator thought of as the cause of these problems.

Returning to the graph, look at the point where the red arrows are pointing. This is where I switched the city from Simulator Z v1.0 to v1.2. The changes in v1.2 included reducing rapid transit speeds, adjusting the **Customers/Traffic Noise Coefficient**, and strengthening the travel strategy preferences of the [Sims](/sims). The changes in the graph here are more subtle; some take a while to kick in, while others are immediate. The general trend of the R\$ and R\$\$ lines does not change immediately. However, within a decade the trends accelerate until they cross at a point where they are both close to the vertical. Major changes are clearly happening in the city here, yet without seeing this graph, they would not be obvious. At this point, both the PH change and the changes introduced in v1.2 are working together constructively to produce these steep trend lines. From experiments in the thread referenced above, it was shown that a PH change tends to work itself out in about 30 years. In the graph, that's right where the top two trend lines angle sharply toward the horizontal. The R\$\$ remains fairly constant through the remainder of the run, while the R\$ continues to decline; the population as a whole remains steady. From here on out, low-wealth Sims are being replaced by high-wealth Sims.

Meanwhile, the changes in the R\$\$\$ line begin right at the simulator switch; there's an immediate little bump that quickly turns into a steady upward trend that lasts through the remaining 60 years of this graph. The net result of the movement of all three populations is that in just a few years following the change in simulators, the city's overall population jumps by about 7%, from 835K to 894K, a level at which it remains at for the rest of the graph.

There are significant changes in the commercial capacity as well. (The city has no industrial population to speak of.) The third red arrow shows the CO\$\$\$ capacity, which has been flat until now, but immediately increases during the few years after the switch. It settles back a little bit, and then maintains roughly the same level for the remainder of the run. Meanwhile, directly below the red arrow is the CS\$\$\$ line, which has been slowly rising since the introduction of perfect pathfinding. But with the changeover to v1.2, the rise accelerates noticeably for a few years, and then slows down, though it continues to rise through the end of the test.

Changes like these are much easier to see in a small graph like this than by eyeballing the city for a century. Some of the most dramatic changes come with the introduction of v1.2, well after the PH has been lowered, so there are clearly other factors at work here. Later, the perfect pathfinding heuristic was changed to the more accurate value described in [this post](http://sc4devotion.com/forums/index.php?topic=5382.msg297913#msg297913); this caused the previous changes to continue on for a little longer. To understand what these changes are and what their importance is, we have to really understand how the traffic simulator works, and that is the subject of the rest of this article.

First of all, it is important to note that despite its name, the traffic simulator isn't actually the part of the game that simulates traffic, at least as it is visible to the players. Visible traffic is generated by the **automata controller**, which is only loosely influenced by the traffic simulator. Aside from the automata, there is no actual traffic in the game. Instead, the traffic simulator runs about once every four game months, and calculates routes for the Sims to take to and from work. This is why if you use the Route Query Tool on various networks, the numbers will always remain constant for months at a time. No one travels the morning commute routes in the morning, and no one travels the evening commute routes in the evening (other than the automata). These routes are calculated mainly for their side effects, which are used by many other aspects of the game. Most importantly, they are a key factor in determining [desirability](/desirability), which is one of the most important factors in deciding how the growth of cities will proceed. To a very large extent, then, the traffic simulator is actually a desirability generator.

The functionality of the traffic simulator can be divided into six parts:

- The **destination finder**, which locates suitable jobs for working Sims.
- The **pathfinder**, which calculates paths from the Sims' homes to their jobs.
- The **automata support**, which provides data that allows the automata to reflect something of what is happening in the game.
- Properties that affect only the city's budget.
- Properties that are either unused, or serve a purpose that is currently unknown.
- Properties that are known to be nonfunctional.

The first two of these functions are the main reasons for the traffic simulator's existence: to find jobs for the Sims, and to calculate paths to these jobs. As mentioned, these functions run about every four months, with the destination finder first finding all the jobs for Sims who need them, and then the pathfinder calculating the necessary paths. The reason that the destination finder must run first, and not in parallel with the pathfinder, is simply for efficiency reasons. As will become clear as this guide progresses, both of these functions need a large amount of memory to run. The minimum system requirements for SC4 are a Pentium III 500 with 128 MB of memory. It is difficult enough running this game at all in such an environment. If the destination finder and the pathfinder ran in parallel, the amount of memory required would be greatly increased, and a lot of paging would result on minimal systems, resulting in the game's running several times slower, essentially becoming unplayable for all but the smallest cities. For this reason, and because running the two functions in parallel doesn't gain anything, we can assume that they are run sequentially.

### The Destination Finder

In every traffic simulator run, the destination finder systematically goes through all the residences in the city and sees which Sims need new jobs. [RippleJet](/people/ripplejet) [discovered](http://sc4devotion.com/forums/index.php?topic=9638.msg295132#msg295132) the default movement pattern of the destination finder:

> From what I've seen in a couple of my cities, the destination finder works from the west to the east, probably picking the tracts (which are 4×4 tiles) in consecutive order, starting in the northwest corner, going down south, and then up to the next column of tracts.

How the destination finder decides that a Sim needs a new job is somewhat more complex. The [Prima Guide](/prima-guide) claims that as of [Rush Hour](/rush-hour), "the Sims hold their jobs until something forces them to find another." But extensive testing in mature cities seems to show a lot more job changing than this statement would imply. Further research is needed here.

What is known at this point is that there are many different properties that can affect the destination finder's choice of a job for a Sim. Depending on the values of these properties, the destination finder may decide that no suitable job exists for a particular Sim, and the pathfinder won't even be run for that Sim. It has become clear that the destination finder has been tuned aggressively by [Maxis](/maxis) in ways that we cannot access in order to minimize how much the pathfinder must run, since finding paths is one of the most expensive operations (in terms of CPU time and memory) in SC4. The destination finder will make an educated guess as to whether a path is even possible between a Sim's residence and a prospective job. Presumably, if it decides that such a path is not possible, it will look for other open jobs. Ideally, it would check all open jobs until it finds one it thinks would work, but at this point, we don't know if it does that, or if there's a limit on)the number of jobs it checks. We do know that there are various properties that influence where it looks for jobs, and those are discussed below.

The destination finder also knows a little bit about how the pathfinder works, and uses this knowledge to help decide whether or not it thinks a job is reachable from a residence. In determining a more precise value for the perfect pathfinding heuristic, I found out something very interesting: In deciding whether a job is reachable from a residence with the current traffic simulator settings, the destination finder weighs the presence of subways very heavily, especially subways that go very near the residence, and presumably, those that go near the job as well. It's not just subways, though - any rail network will do, and highways will work almost as well. It's just easier to place a large network of subways than any other type of network, since they don't take up surface real estate. At first glance, this whole behavior seems very strange indeed. It seems even stranger when you discover that this holds true even when the traffic simulator uses perfect pathfinding, and even when **Commute Trip Max Time** is set to many times the amount required for a successful trip. Even in such circumstances, buildings can be abandoned due to commute time when perfectly good jobs are available in the city. But add a few subways in the right places, and abandonment disappears.

To understand what's happening here, it's important to remember that in the original Maxis traffic simulator, **Commute Trip Max Time** is set to six minutes. And in the original Maxis simulator, using the subway speed of 150 kph, you can get from one corner of a large tile to the opposite corner in 3.28 minutes via subway. In other words, you can get from anywhere to anywhere else on a large tile via subway in the original Maxis simulator, and still have enough time left over to walk a little ways to and from the stations. I think this helps explain why the six minutes was originally chosen for **Commute Trip Max Time**. It also allows the destination finder to make a quick and dirty test. If there are enough subways around, and the subways go close enough to the businesses and residences, then with perfect pathfinding (or something close to it), the Sims can probably make it to such a job within six minutes, and the destination finder hands off the source/destination pair to the pathfinder. But without enough subways or other high-speed networks, they may not, and further tests have to be done.

This only makes sense if we use the six minute figure. But this behavior persists even when **Commute Trip Max Time** is set much higher - even a hundred times as high. The only way I can think to explain this is that the six minute figure is hardwired into parts of the destination finder.

There's another interesting implication here. Sims can be guaranteed to reach anywhere on a large tile only if perfect pathfinding is used. Without perfect pathfinding, the destination finder will preemptively discard many otherwise valid trips, as has been shown in the experiments mentioned above. This would tend to support the theory that the Maxis programmers originally intended that the traffic simulator be used with perfect pathfinding, and indeed used it themselves; it was likely only the constraints of having to run a Pentium III 500 with 128 MB of memory that resulted in perfect pathfinding being abandoned for the commercial product. This issue is discussed in more detail in the Appendix.

The destination finder also uses a time limit in deciding what trips are feasible. Based on the various properties described below, if it thinks that calculating a valid path is going to take more than a certain amount of time, it declares that path as being invalid. In standard *A\* pathfinding* (described below), values for the heuristic lower than the perfect value should still produce perfect paths; they just take longer. But in SC4, values lower than the perfect value can result in additional abandonment or downgrading. This is due to the time limit imposed by the destination finder.

The properties that are known to affect the operation of the destination finder are as follows, in approximate order of importance. When optimum values for these properties have been through experimentation, these optimum values are noted after the property's description.

#### Pathfinding Heuristic (a.k.a. Nearest Destination Attractiveness)

Even before [Rush Hour](/rush-hour) was released **the7trumpets** and many others recognized this as the most important property in the whole traffic simulator. And even back then, when Maxis was still talking to the SC4 community, they referred to this property by both of its names. Both aspects of this property come into play in the destination finder.

The traffic simulator's pathfinder uses a modified version of the A\* algorithm, which is described very well in [Amit’s A\* Pages](http://theory.stanford.edu/~amitp/GameProgramming/). Basically, the number and complexity of the possible paths between Sims and their jobs grows exponentially with the size of a city. The A\* algorithm is designed so that it will always find a path between its source and destination points if one exists. The pathfinding heuristic is a constant that determines how close to perfect these paths are; i.e., how close they are to the fastest possible path. In perfect pathfinding, the value of the pathfinding heuristic is such that the fastest possible path is always found. In SC4, this number has been experimentally determined to be approximately 0.005797. The behavior of A\* is generally exponential, in that as the pathfinding heuristic approaches the perfect number, the time to compute paths rises exponentially. However, as the pathfinding heuristic gets close to the perfect number, the exponential behavior gradually decreases, and it costs less and less to approach perfection. Below the perfect number, the paths produced are still the fastest, but the time to compute them increases again. In Amit's words:

> So we have an interesting situation in that we can decide what we want to get out of A\*. At exactly the right point, we’ll get shortest paths really quickly. If we’re too low, then we’ll continue to get shortest paths, but it’ll slow down. If we’re too high, then we give up shortest paths, but A\* will run faster.
>
> In a game, this property of A\* can be very useful. For example, you may find that in some situations, you would rather have a “good” path than a “perfect” path...

That's how standard A\* pathfinding works. However, in SC4, much of the destination finder has been designed to cripple the activities of the A\* pathfinder for the sake of efficiency. Whereas the standard A\* algorithm is designed to always find a valid path if one exists, regardless of the value of the pathfinding heuristic, in SC4 the probability of finding a valid path declines as the pathfinding heuristic moves away from its theoretically perfect value, which is approximately 0.005797. So while in standard A\* pathfinding, the worst penalty for not using perfect pathfinding is having longer paths, in SC4 the worst penalty for not using perfect pathfinding is not finding valid paths at all. This is a big difference, and is where most of the "Abandonment due to commute time" comes from. Furthermore, if some residents of a building aren't able to find valid paths to jobs, but others are, the pathfinding failures of the unemployed residents is averaged in with the commute time of the employed residents. This can result in the commute time that is associated with the residence being designated "Long," which reduces the desirability of the residence. This can happen even when all the employed residents of the building have short commutes.

It was mentioned above that in the traffic simulator, the **Pathfinding Heuristic** property is also known as **Nearest Destination Attractiveness**. The reasoning behind this is very simple. Although the distance a Sim can travel during a commute is theoretically limited only by the **Commute Trip Max Time** property, in practice the **Pathfinding Heuristic** plays a big part as well. The higher the **Pathfinding Heuristic**, the more likely it is that the Sims will not take the fastest path, and instead will take the most direct path. In other words, a higher **Pathfinding Heuristic** effectively reduces their range of travel. The destination finder takes this into account, as it figures that there's no point in setting a destination that the Sims can't reach, and the higher the **Pathfinding Heuristic**, the more the destination finder steers the Sims to nearer destinations. Unfortunately, the destination finder appears to be overly conservative in estimating the limiting effects of the **Pathfinding Heuristic**. The result is that the destination finder draws a line beyond which the Sims cannot go in their travels, based on the values of the **Pathfinding Heuristic** and the **Commute Trip Max Time**. This line has been observed by multiple people; for example, in [this post](http://sc4devotion.com/forums/index.php?topic=3508.msg111438#msg111438) by **jplumbley**:

> Although what is intruiging is your roads are not over capacity. There seems to be an invisible "line" that is stopping sims from going further, I have a feeling this is where the maximum distance of the travel is.

That is exactly what was happening. The destination finder figures that the pathfinder will never find a valid path to points beyond that line within the time available, so why spend the extra CPU time and memory letting the pathfinder try to solve what is probably a hopeless task? So the pathfinder *never runs* for those Sims for whom a destination cannot be found on their side of the line.

This entire strategy accomplishes what it sets out to do - it gives a basic implementation of A\* pathfinding while limiting the amount of CPU time and memory spent in these expensive calculations. But it does so at great cost. Instead of having a pathfinder that always finds valid paths, we have one that finds valid paths most of the time, the exact percentage depending on the value of the **Pathfinding Heuristic**, **Commute Trip Max Time**, how close zones are, and the size of the cities in question. Fortunately, if we use perfect pathfinding and follow the guidelines about using high-speed networks, realistic cities of almost any size (along with many not so realistic ones) can be built.

What about traffic simulators that don't use perfect pathfinding? If zones are intermixed closely, than large cities can still be built quite successfully. For smaller cities, the complexity of paths declines exponentially, and the traffic simulators all begin to behave quite similarly in terms of pathfinding. But there is no downside at all to using perfect pathfinding; even the supposed performance disadvantage is minimal at best. For example, SC4 using the Simulator Z v2.2 has been measured to run from 0% to 10% slower than SC4 using the standard Maxis simulator - not a big difference considering the difference in results. This advantage of perfect pathfinding was known to the SC4 community even before the release of the Rush Hour pack; this is documented in the Appendix below.

<span style="color: blue;">Optimum value: 0.005797</span>

#### Customers/Traffic Noise Coefficient

All Sims who travel by bus or car, or simply as pedestrians, count equally toward road traffic volume. So do trucks. For this property, road traffic volume applies to all the road networks except highways. High road traffic volume has a positive effect on desirability for commercial buildings, which shows up in the query as "Customers," and a negative effect on residences, where it shows up in the query as "Traffic noise." Low road traffic volume has the opposite effect in each case. However, the effect of road traffic on residences is far lower than on commercial buildings.

This property is important to the destination finder because only those commercial buildings with sufficient desirability are considered as possible destinations for Sims looking for jobs, regardless of how many job openings they have. Road traffic volume, which translates to customers, plays a large part in computing this desirability, and the way road traffic volume is translated to customers is determined by the **Customers/Traffic Noise Coefficient** property. According to the documentation for this property, "In an area around the lot in question, the traffic on the network tile with the highest morning traffic volume is added to the traffic on the network tile with the highest evening traffic volume, and then multiplied by this coefficient to generate a 0-255 value which is then used as a desirability factor for R and C zones, and shows up in the general query as low, medium, or high under Traffic Noise or Customers."

What is the "area around the lot in question"? Experiments by [Trias](/people/trias) have found the following, which is essentially [this post](http://sc4devotion.com/forums/index.php?topic=10261.msg323912#msg323912) in its entirety:

> "I've done some more testing on the range at which traffic noise is calculated. It appears that the map is divided in a 4 by 4 grid for the purpose of calculation traffic noise. The traffic noise in one such block is determined by listening to the traffic up to half a block away. That is, if you consider the picture below:
>
> <div align="center">
>
> <http://img189.imageshack.us/img189/8263/iah.png>
>
> </div>
>
> "The blue block will listen for traffic in any of the red or blue squares. From these it will supposedly then pick the tile with the highest morning traffic and the tile with the highest evening traffic and add those. (And probably multiply those by the customer/traffic noise coefficient, more on that later.)
>
> "Thus far most my test has been done by using small zones. For 1x1 zones, the zone will get the traffic for the block in which it is located. For larger zones that have tiles in multiple blocks, the traffic appear to be taken as the traffic get for the middle tile of the zone. In the case of even number of tile in the zone, the tile to the south of the middle is taken. (The later part is still a bit speculative, and needs more testing. In particular, I do not know what happens for very large zones of say 8x8 in size.)"

Furthermore, Trias determined that the number of customers for a commercial building is determined by the following formula:

<div align="center">

Customers = coefficient \* (traffic volume)

</div>

The maximum number of customers is capped at 255, while the thresholds for "medium" and "high" customers are 152 and 215, respectively. The following graph of his plots the thresholds for medium and high customers against the inverse of the coefficient:

<div align="center">

`   `[`http://img543.imageshack.us/img543/3134/sc4traffic.png`](http://img543.imageshack.us/img543/3134/sc4traffic.png)

</div>

Residential zones have different thresholds, but these have not yet been determined.

Although at first glance, the relationship between the coefficient and the number of customers appears to be simply linear, a closer examination shows that the actual case is more complex. Specifically, there are strong second-order effects that destroy the linearity of this relationship. The number of customers for a given business is directly proportional to traffic volume, at least until the cap has been reached. The number of customers, in turn, contributes to determining the number of workers employed at that business. But what is the traffic volume, really? It is actually the number of workers traveling to businesses - not customers, as customers are not modeled as part of the traffic flow. So as the number of customers increases, the number of workers increases, which in turn increases the number of customers, and a nonlinear positive feedback loop is created. What this means is that the coefficient has the additional function of determining the strength of this feedback loop, and the simple linear description mentioned above is insufficient to describe what's actually happening.

Furthermore, the actual effect of this coefficient in game play is more difficult to determine. For example, the Traffic Effect property in the developer exemplars shows that traffic volume levels have the biggest effect on desirability for CS\$\$\$. But in actual game play, their biggest effect is on CO\$\$\$. One experiment I did showed that drastically reducing the coefficient had a large negative effect on a city's CO\$\$\$ population, but nowhere else. The reason for this discrepancy can be seen if you look at the Desirability Data View map. In general, desirability for CS\$\$\$ is much higher overall than for CO\$\$\$. That explains why a smaller change in CO\$\$\$ desirability can have a bigger effect in the game than a larger change in CS\$\$\$ desirability.

In the end, my experiments led me to an optimal value of 0.25 for this coefficient. Why is this value so far from the default Maxis value? I think that the main reason is that in the default Maxis simulator, the high **Pathfinding Heuristic** kept Sims from utilizing mass transit anywhere near as much as they do with perfect pathfinding. Perfect pathfinding results in much higher mass transit usage, which means less road traffic in general. The value of **Customers/Traffic Noise Coefficient** needs to be raised substantially to compensate for these factors.

<span style="color: blue;">Optimal value: 0.25</span>

#### \[Travel type\] Speed

The values of the nine travel type speed properties (Walking, Driving, Bus, Train, etc.) have an indirect but important effect on the destination finder. (The meaning of each array of values for each property is explained in more detail in the section on the pathfinder.) Essentially, the speeds need to be balanced so that the lower road speeds when averaged with the higher rail speeds work out to about the same average speed as the Maxis speeds. However, when using perfect pathfinding, the range of speeds needs to be made tighter; the original Maxis speeds needed the wider range in order to give any reasonable bias at all to the faster mass transit when using the very high **Pathfinding Heuristic** of 0.09 present in the original Maxis simulator. The reason that the average speed needs to be about the same except with a tighter range relates directly to the **Customers/Traffic Noise Coefficient**. The rails need to have a high enough speed premium over road traffic so that Sims will prefer them. But if the speed premium is too high, road traffic drops to the point where it has a negative impact on commercial customers. The speeds used in Simulator Z seem to fit well in this range, but I have not done enough experiments to pinpoint a specific optimum speed for each travel type here.

#### Commute Trip Max Time

This property specifies the maximum number of minutes allowed for a Sim's journey during the morning commute. (The evening commute has no time limit; the pathfinder must simply be able to find some valid path between the Sim's job and its home.) The fact that this number represents minutes can be verified not only from Maxis' internal documentation, but also from simple experiments. To find the number of minutes that it takes a particular travel type to cross a particular square, use the experimentally and theoretically verified formula:

<div align="center">

time = 0.96/speed

</div>

where "speed" is the speed of the travel type on the network in question.

As mentioned earlier, this property is used in combination with the **Pathfinding Heuristic** to determine approximately how far the Sims will be able to travel, and this information in turn is used to help determine whether or not a particular destination is suitable for a particular Sim. As was also mentioned, the destination finder is very conservative here; it tends to err on the side of marking destinations as unreachable when they actually are reachable, rather than the other way around. Since this property is used in combination with the **Pathfinding Heuristic** in determining which destinations are reachable, a higher **Commute Trip Max Time** can help make up for the reduced range that results from a higher **Pathfinding Heuristic**, though not completely. The most effective combination of these two properties still requires perfect pathfinding.

The **Commute Trip Max Time** property also has another function, in that when perfect pathfinding is not used, a higher value of**Commute Trip Max Time** will result in a higher probability that Sims will use neighbor connections to cross into an adjoining tile. This probability varies by travel type, with faster travel types reaching their maximum probability at lower values of **Commute Trip Max Time** than slower travel types. At a value around 600, all travel types reach their maximum probability for crossing into neighboring cities.

The above applies only when perfect pathfinding is not used, however. When perfect pathfinding is used, the probability that any travel type will cross into a neighboring city is always at its maximum, regardless of the setting of **Commute Trip Max Time**. For this to occur, the value used for perfect pathfinding must be either 0.005797 or extremely close to it; the value of 0.003 that was previously thought to be the perfect pathfinding value does not produce this effect.

It might appear at first that perfect pathfinding causes a negative effect here - that it results in too much intercity traffic, at the expense of intracity traffic. But paradoxically, as long as the **Commute Trip Max Time** is set high enough, this is not the case. For when this property is set to a high value, all commutes to points within the same city are marked as "Short" (as can be seen by querying the residences), while all commutes to other cities are automatically marked as "Long." As a result, the destination finder ends up picking more of the available jobs in the same city than it would if perfect pathfinding were not used. In such a case, whether or not jobs in the current city are picked over jobs in the adjoining city depends on the desirability of the jobs in the current city.

How high a value should be used? The external documentation for SC4 claims that Sims have 2.5 hours to get to their job, although Maxis had to use a hidden multiplier of 25 to get this number; this multiplier is also present in the default Commute Time Graph. By actually using the specified value (150 minutes) or higher, without the multiplier, the benefits described above can be obtained, and there need be no worry that this property will contribute to abandonment due to commute time. However, higher values than this have the advantage that they influence the destination finder so that it is more likely to deem a destination reachable, and pass it on to the pathfinder.

<span style="color: blue;">Optimal value: At lease 150; higher may still be slightly better.</span>

#### Travel Strategy Percent Wealth

Of these four properties, only the last three are important. Each property represents a Sim wealth level; within that property, the first number is the percent of Sims of that wealth level who prefer to take mass transit, the second number is the percent of Sims who prefer to drive, and the third number is the percent of Sims who simply prefer to take whichever method of travel is fastest. Like the travel type speeds, these properties affect the destination finder only indirectly, and like the travel type speeds, they do so via their effect on commercial customers. However, it is only extreme settings of these properties that cause problems; the standard settings used in the various traffic simulators do not really make a difference in the operation of the destination finder. Furthermore, when perfect pathfinding is used, even extreme settings for these number do not seem to have any negative effect here.

#### Trip Starting Cost by Travel Type for Mass Transit

The function of this property is described in detail in the section of this document describing the pathfinder. It has only a small tertiary effect on the destination finder, as it affects the **Travel Strategy Percent Wealth**, which in turn may affect the number of commercial customers.

<span style="color: blue;" >Optimal value: 0, 1.2, 0, 0, 0, 0, 0, 0, 0</span>

### The Pathfinder

Once the destination finder has finished running, the pathfinder runs. It calculates new routes for Sims who have new jobs, and recalculates routes for Sims at existing jobs. In this way, the effects of network construction, destruction, congestion, etc. are taken into account. The following properties influence the running of the pathfinder; as with the destination finder, they are listed in order of importance.

#### Pathfinding Heuristic (a.k.a. Nearest Destination Attractiveness)

As with the destination finder, the **Pathfinding Heuristic** is the most important property in the pathfinder. A lot of its importance comes from the influence it has on other properties, as described below. This influence is greatest when the **Pathfinding Heuristic** is set to the perfect pathfinding value of 0.005797; in a number of cases, its influence exists only at or extremely close to that particular value. Such cases are noted below when they occur. For the pathfinder, the main direct significance of the **Pathfinding Heuristic** is that when it is set to the perfect pathfinding value, then the pathfinder will also find the fastest route between the Sims' homes and their jobs. However, due to the actions of the destination finder, described above, the pathfinder may not get a chance to run in a specific case, and so abandonment due to commute time is still possible even when perfect pathfinding is used. However, as also mentioned above, such abandonment may be overcome by judicious use of subways, which is only guaranteed to work if the pathfinding heuristic is equal to the perfect value.

#### \[Travel type\] Speed

The speeds of the various travel types have a big effect on the pathfinder, since it always tries to find the fastest route for the Sims. The effect of the speeds, though, is directly related to how close the **Pathfinding Heuristic** is to its perfect value. For example, in the original Maxis traffic simulator, which has a pathfinding heuristic of 0.09, speeds are almost completely ignored, and the pathfinder simply finds the most direct route to its destination. At the other end of the spectrum, when the **Pathfinding Heuristic** is set to its perfect value, the pathfinder always finds the fastest route.

Speeds are measured in kilometers per hour. This can be verified not only from Maxis' internal documentation, but also from simple experiments, based on the observable fact that tiles are exactly 16m on each side.

The value set for **Walking Speed** is especially important. At 15 kph in Simulator Z, it is disproportionately high compared to other speeds. But this is necessary for the success of mass transit in general. In RL, people have to wait for buses and trains, even the fastest ones, and buses and trains make a number of stops along the way to their destination. Neither of these cases occurs in SC4. And whereas people choose mass transit for a variety of reasons in RL, in the end, speed is the only factor that counts in SC4. This speed may be adjusted by various biases, which are discussed below, but the biases cannot be set high enough to overcome large differences in speed without unbalancing the game.

This is the reason that the walking speed is set as high as it is. In RL, people commonly walk several blocks to a bus stop or subway station. If the walking speed is set too low, then only unrealistically short walks would be permitted by the pathfinder, as otherwise the slower speed of walking dominates the pathfinding, and even short walks can distort the value of taking the subway as preferred to the bus or car. A walking speed of 15 kph is high enough to minimize the effect of walking on pathfinding, yet low enough not to compete with other forms of transportation. So Sims may walk a few blocks, but beyond that, other travel types become more efficient.

As for most of the other speeds, with perfect pathfinding, using a set of speeds that has the same proportion as real world speeds works quite well. In setting these speeds, the effect of influences such as traffic lights, mass transit stops, etc. must be taken into account. Furthermore, using exact real world speeds has certain issues associated with it. The problem here is that the game has certain numbers hard-wired into it, and using real world speeds would cause the destination finder to erroneously conclude that the Sims could no longer reach certain destinations, leading to either reduced desirability for residences or outright abandonment. Therefore, it is good to raise these speeds by about 50%, which is what is done in Simulator Z. This is not an exact figure; speeds were also adjusted somewhat to provide a realistic proportion of travel type usage. There is also a problem in making speeds too high on non-road networks; if this is done, Sims flock to the higher-speed networks at the expense of the road networks to the point where lower road traffic begins to affect customer count at commercial buildings adversely. This leads to lower desirability and lower jobs at these buildings. So there is actually a fairly narrow range that works well for travel type speeds - too low or too high has adverse effects.

#### Commute Trip Max Time

As mentioned in the section on the destination finder, this is the maximum time in minutes allowed for a Sim's morning commute. Although this property is used mostly by the destination finder to screen out unreachable or potentially unreachable destinations from the pathfinder, which is very expensive to run in terms of CPU time and memory, it is also used by the pathfinder itself. Sometimes destinations that are only a short distance away from their destinations may require convoluted routes, and this would occur at a level of detail beyond what the destination finder looks for. As a result, the pathfinder must also keep track of the total time used in the morning commute, and make sure that it does not exceed the number specified by this property. In practice, due to the previous actions of the destination finder, this case rarely occurs.

The actual length of the morning commute time is also compared against the value of this property to determine whether a Sim's commute is Short, Medium, or Long; this information is displayed in the query of the Sim's residence. Short commute times add to the desirability of the residence, medium commute times have no effect on its desirability, and long commute times subtract from its desirability. Unfortunately, in order to have a **Commute Trip Max Time** that is long enough to avoid the unrealistic abandonment due to commute time, all intracity commute times end up being Short. All commute times to neighboring cities are automatically classified as Long, however. Sims who are unemployed are considered to have very long commute times, so if a building has a mixture of employed and unemployed Sims, the average commute time for the building may turn out to be Medium or Long, even though none of the destinations of the employed Sims lie outside of the current city.

#### Congestion vs Speed

This property consists of a variable number of pairs of values, and applies to all networks. The first number represents a proportion of the nominal network capacity, while the second number represents a proportion of the travel type speed for any travel type using that network. So as an example, the pair (2, 0.65) would mean that when a network tile reached twice its nominal capacity, the speed of all travel types passing over that network tile would be 0.65 times the nominal speed of the travel type; these speeds were described above. However, this speed modification applies only to those travel types that are affected by traffic; which ones these are is specified in the property **Travel Type Affected by Traffic**, described below.

In general, the main purpose of this property is to provide congestion in the form of speed reductions when networks exceed their capacity. Before the introduction of Simulators A and B, traffic on network tiles that were below their capacity always traveled at the nominal speed of the travel types involved. However, with the introduction of Simulators A and B, the concept of a "speed premium" was introduced. This meant that even for network tiles that were under capacity, the less traffic there was, the higher its speed would be. This had two benefits:

1.  For RHW, this feature was required on wide highways where a single direction of travel takes up multiple tiles. The reason for this is that the speed premium makes it advantageous for the Sims to spread out across all the lanes. Without a speed premium, it would be more efficient for them just to stay in their original lanes, leaving much of the highway empty until the lanes that were used reached full capacity.
2.  The A\* pathfinding routines in the traffic simulator work most quickly when there is an unambiguous fastest route to choose. A speed premium that is based on traffic volume can function as a tie breaker for routes that would otherwise be equivalent.

The number of data pairs, or points, in this property also influences how fast the pathfinder runs. If the number of points is higher than the optimum, then more calculations have to be made by the pathfinder to find the fastest route. If the number of points is lower than the optimum, then again more calculations have to be made by the pathfinder, although this time the extra calculations are required to break ties between routes that take identical times to traverse, at least in their early parts. The optimum number of points provides enough points to assist in tie breaking without providing so many that the tie breaking advantage is overwhelmed by extra route calculations. The optimum number of points is easily determined by testing and seeing which number of points results in the simulator running the fastest; for the Maxis implementation of the traffic simulator engine, this number is six. Also, for best results in tie breaking, no three adjacent points should be on the same line. In other words, an optimal Congestion vs. Speed curve will have five line segments, and no two adjacent ones will have exactly the same slope.

There are further constraints on these six points. Although in most traffic simulators the speed at full capacity is set to one, theoretically it can be set to anything. In the real world, congestion starts to occur (that is, speed starts to drop) before full capacity is reached. However, in SC4 congestion is effectively defined to start when network tiles exceed their nominal capacity. It is at this point in the original Maxis simulator, as well as most of the NAM traffic simulators, that the color of networks starts changing from green to yellow in the Traffic Congestion Data View. It is possible to change the point where congestion starts, but doing so effectively redefines the meaning of network capacity in SC4. Therefore, in order to keep a consistent view across traffic simulators, it is helpful if one of the middle points consists of the pair (1, 1).

The second constraint has to do with the value of the top point, which is the point representing zero volume. Although the speed component of this point in the original Maxis simulator is 1, in order to implement the speed premium mentioned above, it must be greater than 1. It's good not to have it too much greater than 1, both for the sake of realism and so that the attractiveness of different speed networks does not start to overlap. However, if this number is less than 30% above the full capacity speed, the spreading effect does not fully manifest on the RHW. So (1, 1.3) seems to be the optimal value for the top point.

On the other end of the scale, a speed value of around 0.05 would seem to be appropriate, as this corresponds to heavily jammed networks in the real world. Unfortunately, there is a bug in SC4 that manifests whenever a point containing a speed value less than 0.3 is present in this property, regardless if such a point is ever reached in actual play. This bug manifests by distorting the congestion display. Although the transition from green to yellow in the display normally happens right as the speed in this curve drops below 100%, if a speed value below 0.3 is present, the speed value is ignored, and the threshold for displaying a color other than green increases to somewhere above 100% of network capacity. The lower the lowest speed value is, the higher the threshold; if a speed value of zero is present, then the threshold is infinite, and the Traffic Congestion Data View always displays green everywhere, regardless of what the traffic volume is. Therefore, in order to have an accurate Traffic Congestion Data View, the lowest speed value should be 0.3.

Also, the volume number that is associated with a speed of 0.3 determines at what point the Traffic Congestion Data View shows the deepest red for a network. For example, if the lowest data point is (2.5, 0.3), then the Traffic Congestion Data View will turn the deepest red on any tile where the volume is at least 250% of the capacity of the network on that tile. For tiles with multiple networks on them, the Traffic Congestion Data View shows the congestion of the most congested network.

There is a fair amount of latitude for the remaining values in this property that have not been specified. The most important thing here is to use perfect pathfinding; this allows the traffic simulator to make the most use of the data contained in this property, and for the Sims to avoid congested routes in the most intelligent way possible. The end result is that by acting intelligently, the Sims keep congestion to a minimum.

#### Network Traffic Capacity

This property specifies the nominal daily capacities of all of the networks in the following order: Road, Rail, Highway, Street, Water Pipes, Power Poles, Avenue, Subway, Elevated Rail (including GLR), Monorail (including HSR and BTM), One-Way Road, RHW, and Ground Highway. Although Water Pipes and Power Poles appear in this list, these are not full transportation networks, so it is not possible to have Sims traveling by walking over power line wires or by crawling through water pipes. Capacity is specified per tile, which is important to know when considering multi-tile networks such as avenues and highways.

This property is most important when considered in combination with the previous property (**Congestion vs Speed**), as the two together determine when networks become congested, which has a potentially large impact on travel times and routes. The actual numbers for this property are mostly a matter of personal taste, as many players like to set them so that they will have realistic congestion effects in their cities, and different size cities require different capacities for this to occur. However, there is a more or less optimal relationship between the various numbers in this property. In general, the capacity of the road networks should be roughly proportional to their speed. The rail networks function rather differently, and so for the sake of simplicity, all the rail networks tend to have identical capacities. Furthermore, the capacities of the rail networks should be set so that they get congested much more slowly than the road networks. The reason for this is simple; the two types of networks respond to traffic volume quite differently in RL. When roads go above their rated capacity, traffic quickly begins to slow down. But the various types of trains travel at the same speed regardless of the traffic volume. There is a congestion effect due to the longer time spent loading and unloading larger volumes of passengers at stations, but this is much less than the congestion effect experienced by road traffic.

Although the network capacities are floating point numbers and can therefore have any realistic value, there is an important limitation imposed by the Traffic Volume Data View. The volume of traffic that can be displayed during any commute period is limited to an unsigned 16-bit number, or 64K - 1 (65,535). Networks can actually carry more traffic than this, and the additional traffic will show up in the Traffic Congestion Data View, but the traffic volume displayed will never go above 65,535. This should be taken into account when designing network capacities.

#### Travel Strategy Percent Wealth

Of these four properties, only the last three are important. Each property represents a Sim wealth level; within that property, the first number is the percent of Sims of that wealth level who prefer to take mass transit, the second number is the percent of Sims who prefer to drive, and the third number is the percent of Sims who simply prefer to take whichever method of travel is fastest. For all trips, routes for both modes of travel (car and mass transit) are calculated. All mass transit trips begin with walking; some mass transit trips consist only of walking. Some trips are mixed; Sims may start out in their cars, park in a garage or parking lot, and then take mass transit. These are considered to be car trips. Regardless of the preferences expressed in these properties, Sims still always take the faster mode. However, in calculating the travel times for the two different modes, if either "Car" or "Mass Transit" is picked (and not "Fastest"), a time penalty is added to the non-preferred mode according to the properties **Trip Starting Cost by Travel Type for Car Pref** and **Trip Starting Cost by Travel Type for Mass Transit**, which are discussed below. After any time penalty is added, the faster mode is chosen.

#### Trip Starting Cost by Travel Type for Mass Transit

Although this property and the following one each consist of a list of nine numbers - one for each travel type - only the first two numbers are relevant, because all journeys must start out either by walking or by car. (The travel types in these properties are in the same order as they are in the speed properties listed earlier in the exemplar.) In the case of this property, the first number is zero and the second number is a positive number that represents the number of minutes added to all car trips when the preferred travel strategy selected is mass transit. The higher this number is, the more weight the preference will carry. (If this number were zero, a preference for mass transit would have no effect at all on the travel mode selection.) Paradoxically, though, values above 1.2 minutes cause a *reduction* in monorail network usage for reasons that are currently unknown. Fortunately, 1.2 minutes is high enough to give a fairly strong weight to the travel mode preference.

<span style="color: blue;">Optimal value: 1.2</span>

#### Trip Starting Cost by Travel Type for Car Pref

As mentioned above, in this property only the first value is used. This value is the number of minutes added to all mass transit trips when the preferred travel strategy selected is by car. In all traffic simulators published so far, this number has always been 0.1, which means that it has a very modest effect in weighting travel strategies toward car trips. A larger number could be used here for greater effect, but then the **Travel Strategy Percent Wealth** properties would need to be adjusted to reflect this. However, with the current value it is still easy to reduce the Sims' usage of mass transit simply by building less of it, building fewer stations, or closing existing stations.

#### Trip Starting Cost by Travel Type

This property is somewhat similar to the previous two properties, as indicated by the similarity in names. However, unlike the previous two properties, this property always applies to the travel mode selected, and is in no way connected with the **Travel Strategy Percent Wealth** properties. In all currently published versions of the traffic simulator, the value for Car is 0.4, and all other values are zero. What this means is that there is an overhead of 0.4 minutes (24 seconds) added to all car trips; this is in addition to any overhead that might be added by **Trip Starting Cost by Travel Type for Mass Transit**. Essentially, this 24 seconds is meant to cover the time it takes a Sim to walk out of the house, get in the car, back out of the driveway, etc. No overhead is added for mass transit trips, which always start out by walking. The current value seems to be about right, as it helps equalize the advantage that cars have over various forms of mass transit in a realistic way.

<span style="color: blue;">Optimal value: 0.4</span>

#### Travel Type Generates Traffic

This is another property that contains values for each of the nine travel types, in the usual order. When the value is set to True, the travel type contributes to traffic, which means that it can contribute to the network's becoming congested. A value of True also means that the travel type emits pollution. The amount of pollution is constant per Sim, regardless of the travel type.

In the original Maxis simulator, buses and monorails did not contribute to traffic. In the case of buses, the main reason for this was that the original pathfinding heuristic was so high that if buses contributed to traffic, absolutely horrific traffic jams would occur. In fact, perfect pathfinding (or something very close to it) is required in order to allow buses to contribute to traffic without making a real mess of things. But with perfect pathfinding, the simulator actually works better if all travel types other than pedestrians contribute to traffic. On one hand, all travel types in SC4 carry only a single Sim each, so buses and trains don't have the advantage in space and pollution that they do in RL. However, if buses don't contribute to traffic, the simulator behaves in an unbalanced way, since whenever congestion starts to appear, it can simply stuff more Sims in buses with no penalty. In a congested city, bus usage can then outstrip that of every other travel type, including those that are much faster. For this reason, having buses contribute to traffic is the best solution out of a pair of imperfect choices.

<span style="color: blue;">Optimal value: False for pedestrians (the first entry); True for everything else</span>

#### Travel Type Affected by Traffic

This property is in some ways the complement of the previous one. When it is true, it means that the travel type's speed is governed by the **Congestion vs Speed** property. When it is false, the travel type always travels at its nominal speed, regardless of any congestion.

<span style="color: blue;" class="bbc_color">Optimal value: False for pedestrians (the first entry); True for everything else</span>

#### Travel Type Can Reach Destination

Again, there is one entry for each travel type, in the usual order. If this property is True, the travel type can reach the Sim's destination directly. If it is false, the Sim must transfer to another travel type that can reach the Sim's destination somewhere along the route. Normally, this property is True for pedestrians, cars, and the two freight travel types. The Park & Ride variations of the traffic simulators are constructed by setting the second entry to False, so that cars can no longer directly reach the Sims' destinations, and the Sims are forced to transfer to mass transit along the way. This requires parking their cars somewhere. If the Park & Ride variation is used without enough suitable parking facilities, many Sims will never be able to get to work, and there will be a lot of abandonment due to commute time.

#### Intersection and Turn Capacity Effect

This property consists of three values that affect the capacity of networks as they approach intersections. (Not all networks are affected; this property is generally intended for road networks.) The values are multipliers that are applied to squares surrounding an intersection. The first value is applied to the capacity of the intersection itself, the second value is applied to the square directly adjacent to the intersection containing traffic approaching it, and the third value is applied to the square one square beyond the second square.

It was discovered by [ldog](/people/ldog) that more than three values can be specified for this property, and they affect squares that are successively further from the intersection. However, there is a bug in the Maxis congestion display that sometimes results in the wrong congestion color being displayed for a network tile. Adding additional values to this property apparently exacerbates that bug. For this reason, adding additional values is not recommended.

In various roadways in the NWM network, all roadway tiles behave as intersections. For this reason, in order to maintain compatibility with NWM, the first value in this property should always be 1. The other values of this property do not affect NWM, as the primary intersection attribute overrides the secondary and tertiary attributes.

#### Damaged Road Extra Step Cost

If funding for roads is decreased below 100%, potholes will start appearing in some road tiles. The number of tiles with potholes is proportional to the reduction in funding; if road funding is cut to zero, eventually all road tiles develop potholes. Tiles with potholes take extra time to traverse; this property specifies how much extra time in minutes. By default, it is 0.1, or twelve seconds. This penalty is about the time it takes to travel five undamaged road tiles.

#### Max Roads Funding Percent

This property determines the maximum percentage of funding allowed for roads. If the actual funding percentage is above 100%, then repair of damaged road tiles takes place more quickly, proportionate to the funding rate.

#### Transit Switch Entry Cost vs. Budget

If funding for mass transit is decreased below 100%, the Transit Switch Entry Cost - the time it takes to enter a transit-enabled lot - is increased. This property determines how much the increase is. It consists of pairs of numbers, where the first number in each pair is the percent of funding, and the second number is a multiplier to be used on the Transit Switch Entry Cost. By default, the Transit Switch Entry Cost is unaffected at full funding or higher, and at zero funding it is doubled. Between full funding and zero funding, it is increased proportionately.

#### Max Roads Funding Percent

This property determines the maximum percentage of funding allowed for mass transit. Increasing the actual funding percentage above 100% has no effect.

#### Freight Traffic Scaling Factor

This property determines how many freight trips are generated by industrial buildings. The number of workers in an industrial building is multiplied by the value of this property to determine the number of freight trips, which occur either by truck or freight train, and are enumerated in the same way as passengers for commuting trips.

### Automata Settings

The following properties affect the behavior of the automata.

#### Congestion to Accident Probability

This property maps congestion to the probability of accidents. It consists of a series of pairs of values, the first of which is a number specifying traffic volume in terms of a fraction of network capacity, while the second number is the probability of an accident at that volume. Intermediate values are interpolated.

#### Accident Duration

This property represents the time in seconds (real time, not Sim time) that an accident lasts.

#### Accident Check Period

This property is the period (in real time seconds) between checks for accidents by the automata controller.

#### Funding to Damage Acceleration Curve

This property maps funding (as a percentage) to road/rail damage acceleration. It consists of pairs of values, the first of which is the funding percentage, and the second of which is the road or rail damage acceleration. Intermediate values are interpolated.

#### Rail Damage Accident Factor

This property is the probability (between 0 and 1.0) that a train going over a rail pothole will cause a derailment.

### City Budget Settings

The following properties affect the city budget, but nothing else.

#### Monthly Cost for Network Tile

This property consists of a list of values, each of which is the monthly cost in simoleons of maintaining a particular type of network tile. The networks are listed in the same order as in the **Network Traffic Capacity** property. Changes to this property affect all network tiles, existing as well as new. The dirt road network, which has become the RHW network, was incompletely implemented by Maxis, and one of the results of this is that setting this property for the RHW has no effect; the monthly cost for RHW tiles is always zero.

#### Income per Tile by Travel Type

This property consists of a list of values, each of which is the income that the city receives each month when a particular travel type crosses a network tile. The travel types are listed in the same order as the travel type speed properties. The value of this property becomes embedded in network tiles when they are built, so changing this property affects only newly-built network tiles.

#### Ferry Fare

This property is similar to the previous **Income per Tile by Travel Type**, except that it applies only to ferries. Since ferries don't travel on networks, fare changes here are immediate and cover all ferry routes.

### Unknown Properties

The function of the following properties is unknown. Many or even all of them of them may do nothing at all, but this has not been verified. These properties are: \*Monthly Traffic Density Reduction

- Traffic Volume per Population
- Travel strategy percent WealthNone
- Capacity to Accident Probability
- Job Scaling Constant
- Population Background Traffic

### Nonfunctional Properties

The following properties appear to do nothing at all. They definitely do not do what the documentation claims. These properties are:

- Mass Transit Usage Chance
- Maximum Distance from Origin to Network
- Trip Length to Minutes Display Multiplier

## APPENDIX

### Software Archeology: Excavating Sim City

As with other parts of SC4, the more we examine the data available to us, the clearer it becomes what actual mechanisms exist and how they work. Sometimes we discover mechanisms that are not present in the game, but are available for our use. One of the things that makes the traffic simulator so interesting is that the original simulator designed and implemented by the Maxis programmers differs greatly from the one that was originally shipped. The traffic simulator present in the game is tremendously over-engineered for the job it needs to do, and has many capabilities that were not used in the shipping version of the game. The reason for this is the same reason that many design decisions in this game were made; it had to run on a Pentium III 500 MHz computer with 128 MB of memory. The original pathfinder as built by Maxis, and which is still present in the game, is actually rather good; the NAM traffic simulators that do an especially good job of pathfinding simply tune the existing pathfinder so that it runs more to its original specs. However, in order to meet the design goal of running on a Pentium III 500, 128 MB, the pathfinder had to be dumbed down beyond recognition. This caused no end of frustration to the early knowledgeable players of this game, and the legendary modder **[the7trumpets](/people/the7trumpets)** came up with the first modified traffic simulator in August, 2003 - well before [Rush Hour](/rush-hour) came out. This traffic simulator differed from the original in only one parameter - the pathfinding heuristic. This was before anyone knew what algorithm Maxis was using for pathfinding, so it appears that **the7trumpets** found it by experimentation. His value for perfect pathfinding was 0.00625 - very close to the value of 0.005797 that has since been determined to be optimal. This value obtained by **the7trumpets** is especially impressive considering that the more recent value was obtained by testing on scales (i.e., city sizes) not available to **the7trumpets** then, since this was also before the release of the BAT. An entire collection of traffic simulators was put together by **the7trumpets**; it still exists [on the STEX](http://community.simtropolis.com/files/file/21279-pathfinding-modd/). Yet it's clear that **the7trumpets** saw the overwhelming importance of the pathfinding heuristic; here's a quote from the Readme file from his STEX upload:

> Please note that this modd will be less and less effective as your zoning is more and more mixed. For best results, think realistically in your zoning practices, and don't be afraid to zone vast areas of residential. If you're not seeing much highway usage after this modd, it's almost certainly because the majority of your residential zones are not separated from the majority of your jobs. We have played SimCity too long by learning to deal with the necessity to zone everything mixed in an unrealistic way. This modd frees us of that limitation.

And later:

> As we all know, commute time effects desirability enormously, and desirability is one of the key factors in determining abandonment and development. Because of this, in cities built without the modd, it is fairly common to see a redistribution of wealth classes for a year or two until things settle down. Simply let the simulator run for a couple of years and things will even out again.

Here **the7trumpets** ties the pathfinding heuristic to commute time, desirability, abandonment, and development, just as was done earlier in this guide - except he did it more than six years ago. He also did it with much less data; notice how he mentions that things will even out in a couple of years. In recent tests, it often took 20 or 30 years for things to settle down; in the graph at the beginning of this guide, it takes almost a century. It's these much larger periods of change that made it possible to get a more precise value for perfect pathfinding.

Over at simcity.ea.com, there was an entire thread entitled, **[Something Maxis Should Read](http://simcity.ea.com/bbs/messages.php?&openItemID=&threadID=0f9d1749cdef413a65f10da4ebbd5044&directoryID=261&startRow=1#49308a9b642b1988479cb0a79a33c5cb)**. (Many thanks to **catty** for rediscovering this thread.) It contains what are quite possibly the last communications between the SC4 community (including the [Modd Squad](/modd-squad), the predecessor to the NAM Team) and Maxis. Many people will find the entire thread useful to read, especially in light of some more recent discussions about traffic simulators. But the thread is long, so I'll quote a few of the most relevant parts here. From **the7trumpets**:

> I am one of the people who did a lot of work testing the commute engine, and compiled the work of simtropolis members in the 'commute time and pathfinding report' which described many issues in the commute engine. I just recently created a modd available at simtropolis which fixes the pathfinding engine so that it does find the fastest routes. Enough of the credits, I'm not trying to be conceited at all, I just want you to know I've done my homework.
>
> After four months of testing gameplay and reading about pathfinding programming, I have the following suggestions for the pathfinding in Rush Hour. I have no way of knowing which, if any of them, are included, but please consider these suggestions very seriously. They have the potential to make gameplay much better if they are implemented, or kill the fun simcity fans have with the game if they are not.
>
> Suggestions:
>
> - Implement a more efficient pathfinding algorithm
>
> I have not been able to definitively prove which algorithm the sims are using, but from what I have read, it seems plainly obvious that an intersection (node) based A\* algorithm would be by far the most effective and most efficient processor wise.

Here it's clear that no one outside of Maxis knows what the pathfinding algorithm being used in the game is. Yet **the7trumpets** has already managed to come up with a pathfinding heuristic that is extremely close to perfect. The lack of knowledge of the underlying algorithm makes this accomplishment even more impressive.

All of the posts so far in the quoted thread were designed to get a response from Maxis, and so far they haven't. With understandable frustration, **the7trumpets** says:

> Hello? Am I talking to a wall? Should I just stop fixing this game altogether out of annoyance that maxis doesn't care? Or does maxis admit these issues and plan to fix them?

The very next post is from **MaxisFrank**, who posts in this thread for the first time:

> Some response below, I know these are not ideal answers, but we did get the programmers together and go over each of the areas you raised. We do appreciate the challenge (as long as you all understand that there are limitations to any system that is trying to do over 10,000 calculations a second).

Ten thousand calculations a second? I think a typical cell phone can do a lot better than that. But that's a sign of how things have changed since the game was written.

> More efficient pathfinding. We're already using a modified version of A\*.

This is the first official word the community got from Maxis that A\* was being used for pathfinding in SC4. But it's modified. We've seen many of the details of these modifications earlier in this guide, and how they have a profound effect on the workings of the traffic simulator.

The following post is from **[phungus420](/people/phungus420)**:

> MaxisFrank, I can understand the reasoning in most of your statements. In fact I agree with alot of them. The thing we are most clamoring for is a more rational heuristic (.005 instead of .09 so sims actually use highways and such)...

As you can see if you read the entire thread, no one is happy with the current pathfinder, and the single objection they all have is that the PH is way too high. Here the value of 0.005 is mentioned; although lower than **the7trumpets**' value, the two values happen to bracket the recently discovered 0.005797 rather well. **MaxisFrank** responds:

> By the way, the reason why the heuristic is set at 0.09 instead of lower is for performance reasons. The lower you make this the smarter the traffic sim gets, but the longer it takes to complete a traffic cycle. If you've got a buff machine, drop it and be happy. If your machine is emitting smoke and screaming at you to make it stop, turn it up a bit <http://sc4devotion.com/forums/Smileys/JasonSmilies/smiley.gif>

This is an extremely important point; **even Maxis is recommending a lower PH, and by implication a perfect PH, if your machine can handle it.** And between the fact that almost seven years have passed since the initial release of the game, and that tweaks to the traffic simulator have made perfect pathfinding run almost as fast as Maxis' 0.09 figure, it's a very safe bet that all those machines out there running SC4 can handle perfect pathfinding.

Immediately following is a post by **[toroca](/people/toroca)**:

> I can understand the pathfinding heuristic being set higher to speed up performance, but surely you could find a middle ground that allows for both good pathfinding and good performance? As it is now, that value is so high that pathfinding virtually doesn't exist. Sims do NOT take the fastest route to work in almost any situation; rather, they take the most direct, in terms of shortest possible distance. this results in ridiculously overused streets, crowded roads, empty highways, and underused mass transit systems.
>
> Surely there's a better way to improve performance than by crippling the pathfinder? the7trumpets' pathfinding modd doesn't have THAT much of an impact on performance... I think the worst was a 45% slowdown, and that was only with the PERFECT pathfinding mod. In my case, the slowdown was MAYBE 15%, which is MORE than tolerable since it means sims actually look for the fastest way to work instead of the most direct. Few of my streets are overcrowded, and my highways are heavily used, for the first time since I bought the game.
>
> That's what we're asking for. A fix that doesn't have to cripple the pathfinder, and allows the game to work as it was advertised by the developers (sims looking for the FASTEST route was specifically mentioned in the networks article, if I'm not mistaken).

I have since found additional ways of reducing this penalty, so that Simulator Z now runs very close in speed to the original Maxis traffic simulator. Speed is no longer a reason for not using perfect pathfinding.

So from this old thread, we see that even before Rush Hour was released, the more active parts of the community were very much concerned with what's recently been discussed in this thread. The main difference is that six years ago, no one questioned the importance of perfect pathfinding; no one ever suggested that it had negative effects on game performance. (The only exception to this last point is a slight loss in performance, which has been minimized, and no longer makes much of a difference as Pentium III 500's have become rather scarce over the years.)

The last sentence in the last quote by **toroca** is actually rather intriguing, where he says, "Sims looking for the FASTEST route was specifically mentioned in the networks article, if I'm not mistaken." But the fastest route is, by definition, perfect pathfinding. Yet as **toroca** mentions earlier, and many of us can confirm through experience, the standard Maxis simulator simply looks for the most direct route - that is, the route that has the shortest distance. How is this contradiction resolved?

If the Maxis programming team simply wanted a pathfinder that found the most direct route, they wouldn't have had to bother with A\*; there are much simpler algorithms for accomplishing such a task. The fact that they chose A\*, which is capable of always finding the fastest route, and then apparently advertised that that was what they were doing seems to imply that that was their original intention - to implement A\* with perfect pathfinding. In early 2002, a year before SC4's first release, Pentium 4's running at 2 GHz and with 2 GB of memory were already available, and it's not unreasonable to think that the SC4 programmers had access to these. An A\* implementation with perfect pathfinding would run quite nicely on such a machine, especially since they didn't have to deal with the custom content that makes cities with millions of Sims possible today. So my guess is that that's exactly what they built. And then Marketing came in and said, "No, we can't sell this, there are still people out there running Pentium III 500's," even though such machines would be four years old at the game's initial release. So the development team had to dumb down the traffic simulator for the final product, even though the performance gain wasn't all that great.

Fortunately, it's no longer 2003, and even though we don't have the source code, we can now run the traffic simulator pretty much as designed. Most importantly, we can use perfect pathfinding; there's absolutely no reason not to. And even better, your Sims will thank you for it. <http://sc4devotion.com/forums/Smileys/JasonSmilies/smiley.gif>

## FAQ

Finally, I'd like to conclude this guide by answering a few questions about perfect pathfinding that occasionally come up.

**Q: Doesn't Simulator E use perfect pathfinding? After all, "Perfect Pathfinding" is in its name.**

**A:** Unfortunately, it does not. It uses a PH that was thought to be the perfect pathfinding heuristic at the time. And in reality, it is very difficult in most circumstances to see the difference between a PH of 0.003 and a PH of 0.005797. It took me over a year to figure out how to experimentally determine the latter figure. But there are important differences; the 0.003 figure exhibits none of the special qualities of perfect pathfinding described earlier in this guide. In certain cities, this difference can be crucial, as has been observed by multiple players. Furthermore, the game always runs faster with a PH of 0.005797 than with a PH of 0.003.

**Q: But doesn't perfect pathfinding make the Sims' routes too predictable?**

**A:** To the contrary, perfect pathfinding effectively produces the least predictable routes. The reason for this is that the fastest routes may be rather convoluted, and not at all obvious. On the other hand, the more the PH differs from the perfect value, the simpler and more predictable the Sims' routes become, as they gradually shift toward paths that represent the shortest distance between their homes and their jobs.

**Q: But what if I want a more realistic simulation where the Sims don't always take the fastest route. For example, on the way home from work, they might want to do some errands.**

**A:** They are perfectly free to do so! Perfect pathfinding applies only to the morning commute; for the evening commute, any route that succeeds in getting them home will do. For this reason, the routes in the two commute periods often are not identical.

**Q: Are there any disadvantages in applying this perfect PH to existing traffic simulators?**

**A:** Essentially, no; contrary to the belief of many, it will actually speed up almost all traffic simulators.

**Q: Is there any reason not to use perfect pathfinding in a traffic simulator?**

**A:** Not really.

[.](/tutorial/understanding-the-traffic-simulator/old-tutorial)
