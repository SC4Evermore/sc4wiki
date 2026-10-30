---
title: "Colossus Addon Mod"
description: ""
published: true
date: '2019-08-09T01:17:43Z'
tags: ["Mods and Modding"]
editor: markdown
dateCreated: '2008-07-28T11:47:15Z'
---

The **Colossus Addon Mod (CAM)** is a plugin for [SimCity 4](/simcity-4) that changes the game by adding additional growth stages to all of the development types found in the game.

## CAM Developers

People credited with aiding the development of CAM include (in the order acknowledged in the Manual):

- [Indisguise](/people/indisguise)
- [BarbyW](/people/barbyw)
- [Wouanagaine](/people/wouanagaine)
- [JMyers2043](/people/jmyers2043)
- [Shoreman905](/people/shoreman905)
- [Rayden](/people/rayden)
- [MAS71](/people/mas71)
- [Jplumbley](/people/jplumbley)
- [Andreas](/people/andreas)
- [Callagrafx](/people/callagrafx)
- [Tropod](/people/tropod)
- [RippleJet](/people/ripplejet)
- [Tag one](/people/tag-one)

## Early Development

Inspired by [this post](http://community.simtropolis.com/topic/3930-stage8-buildings-possible/) from Tropod at [Simtropolis](/simtropolis) in 2005, RippleJet began testing what would become CAM, first posting his findings at [BSC](/bsc)'s private site before making them public. These posts can be found [here](/cam/posts).

## How CAM Affects the Game

Development of [growable](/growable) (RCI) lots in SimCity 4 is based on a property called growth stage. In SimCity 4 (Vanilla and Rush Hour) residential and commercial lots are available in growth stages 1 through 8, while industrial (including agricultural) lots grow in stages 1 through 3.

The Colossus Addon Mod extends these growth stages to:

- Residential: 1 through 15 (9 through 15 are exclusive to CAM)
- Commercial: 1 through 15 (9 through 15 are exclusive to CAM)
- Industrial: 1 through 10 (4 through 10 are exclusive to CAM)
- Agricultural: 1 through 7 (4 through 7 are exclusive to CAM)

Summarized in a table:

| Type | Residential | Commercial | Industrial | Agricultural |
|----|----|----|----|----|
|  | (R\$, R\$\$, R\$\$\$) | (C\$, C\$\$, C\$\$\$) | (I-D, I-M, I-HT) | (I-R) |
| *SC4*: | 1-8 | 1-8 | 1-3 | 1-3 |
| *SC4+CAM*: | 1-15 | 1-15 | 1-10 | 1-7 |

This might sound like CAM merely allows for additional buildings in the game - which it does. However, CAM does not simply append to the relevant exemplars the ability to use higher growth stages, it completely replaces the growth tables. What this means is that CAM completely rewrites how cities and regions grow. The effect this has on the game is commonly referred to as being more realistic, in that cities are required to build out before building up more so than in the unmodified version of the game. Additionally, CAM has the effect of creating a more even distribution of growth stages present at any given time.

CAM also revises the RCI Demand Ranges. Because CAM allows for much higher growth stages, and thus much higher populations, the game default of +/- 6,000 is insufficient.

Another impact of CAM is to revise what wealth levels of [sims](/sims) work in what wealth levels of jobs, particularly allowing for some portion of R\$\$ sims to be employed in CS\$, I-D, and I-R jobs.

CAM also changes Workforce Drives, [Development CAPs](/cam/posts/5), [Desirability](/desirability), [Crime](/crime) Attenuation, and a fix for the Grand Railroad Station. More information about these can be found in the CAM Manual.

## CAMeLots and CAMpatibile Lots

Because CAM adds several new growth stages to the game, it is necessary to create [lots](/lot) for these growth stages. Lots that only grow at stages exclusive to CAM (9-15 for residential and commercial, 4-10 for industrial, 4-7 for agricultural) are called **CAMeLots**. A list of all available CAMeLots can be found [here](http://sc4devotion.com/forums/index.php?topic=2039.0). Many CAMeLots are large lots that were designed prior to the release of CAM and placed in Stage 8 (or Stage 3 for industrial), but contain far more residents or workers than would be appropriate for buildings of those stages. Relotting these buildings into higher stage lots allows them to grow at a time that would be more appropriate for their development based on city and region size. *CAMeLots can only be used with CAM*.

**CAMpatible** lots are those that grow at stages available in the unmodified game, but have had their occupants (residents or workers, depending on type) set so that they match the growth curves used by CAM. These lots can be used *with or without* CAM.

Additional Notes:

- Because of the widespread changes that CAM makes to the game, a number of high stage buildings that come with the game are revised by CAM into the appropriate growth stage for use in CAM. This change is reversible with the uninstallation of CAM.
  - A comprehensive list of the Maxis Growable lots that have been rebalanced can be found at [:Category:Buildings Rebalanced in the CAM](/category/buildings-rebalanced-in-the-cam).
- Civic buildings are not affected by CAM. You may find yourself suddenly needing much larger schools, hospitals, etc. when playing with the higher populations easily reached with CAM.
- CAM has some interesting effects on farms (I-R lots), especially at higher stages. This allows for what are effectively high-stage farms, while maintaining some realism as to what you might find in a larger metropolis - including nature preserves, historic sites, and so on.
- CAMeLots can be counted using the CAMeLot Counter, a plugin that allows you to get detailed information about the CAMeLots present in a city.

## InCAMpatible Mods

Because of the widespread impact on growth that CAM has on the game, a number of mods developed throughout the years are incompatible with CAM, and can cause problems when used in conjunction with CAM. For the most part, these are mods related to altering growth stages, jobs, abandonment, and Maxis lot blocking or replacement. A list of mods known to conflict with CAM can be found [here](http://sc4devotion.com/forums/index.php?topic=1925.0), as well as in the Manual.

## Impact on Transportation

CAM allows much higher densities than would normally be encountered in the game, and consequently many more commuters. All this extra density has a large impact on traffic, and the unprepared mayor can quickly find themselves in quite the jam. To resolve this, CAM includes an optional pathfinding mod that improves traffic flow in CAM cities and regions.

*Note: The pathfinding addon included in CAM is deprecated and should only be used if you are not using NAM.*

### NAM + CAM

As of 2008, all new versions of the [Network Addon Mod](/network-addon-mod) (NAM) include and supersede the pathfinding included with CAM. What this means is that if you are installing CAM today, you should select the "no traffic simulator" option during installation. If you already have CAM installed, you should delete the z_CAM folder from your plugins. In place of this, you should install the latest version of NAM to handle your pathfinding needs. More information and discussion on this topic can be found [here](http://sc4devotion.com/forums/index.php?topic=4859.0).

### Eternal Commuters

**Eternal Commuters** is a situation caused by sims thinking that the nearest job is always in a neighboring city, and consequently getting trapped in an endless loop. The easiest visualization of this is to imagine four cities sharing a common corner. If each city is connected to each of its neighbors near that corner, residents in that part of a city (City A) may find that the edge of the city is closer than any job within the city. Because sims always assume that the neighboring city's jobs are always at the edge, they will cross to the neighboring city in search of work, commuting to the neighbor (City B). The sims get to City B, and find that in fact, the jobs are not at the edge, and the edge of a third city (City C) is closer than any of the jobs in City B. These sims make the decision then to commute to City C, along with all of City B's sims that are also headed there for work. The sims get to City C, find the same situation as before, and along with City C's unemployed, commute en masse to City D. City D is no better than Cities B & C, and so the entire horde commutes into City A from City D. Upon arrival in City A, they see that City B is closer than any of the jobs in City A, and the cycle repeats. In each one of these cities, the commuting horde picks up new commuters, but never loses any, including when it passes back through the same cities again. The end result is a stream of sims, eternally commuting around the corners of a city, never finding work - and creating tremendous traffic jams in the process.

Eternal commuters is not unique to or caused by CAM, but the higher densities allowed by CAM are known to amplify the effect. Several solutions to this exist, such as:

- Carefully planning your neighbor connections near corners, to avoid creating a loop.
- Creating high capacity loops in your corners, so the eternal commuters can drive around forever without disrupting traffic flow on the "real" traffic network.
- Placing lots of industry at the borders of your cities.

## Installation and Use

CAM can be downloaded from the SC4D LEX in English versions for both Windows and Mac, and versions in other languages are available from several other sites. Full downloading and installation information can be found [here](http://sc4devotion.com/forums/index.php?topic=1877.0). Installation instructions can also be found in the CAM Manual, available at the page linked above.

Because of the complex nature of CAM, it is *strongly* advised that people read the installation information before installing the mod to avoid errors, inCAMpatibilities, [Brown Boxes](/brown-box), and other problems.

As described above, CAM uses CAMeLots, which generally come as separate plugins to be installed in addition to the main CAM installation. CAM modifies some of the default Maxis buildings to function as CAMeLots so that you can start playing with CAM without additional downloads, however this provides a very limited selection. To help with this, there are **CAM Starter Packs** available that provide CAM users with an assortment of CAMeLots in a relatively easy to use package. Note, however, that these starter packs can each have several dependencies, and attempting to install them all at once is recommended only for those with a lot of time and patience to spare. A number of additional CAMeLots are available as individual downloads. More information can be found [here](http://sc4devotion.com/forums/index.php?topic=2039.0).

**Note Regarding CAM as a Torrent:** There are versions of CAM that have been packaged into torrents or alternate downloads that are often advertised as including extra CAMeLots or other bonuses. These are unofficial and illegal downloads and are not supported by the developers of CAM. Using these downloads is known to cause technical problems.

*"The only official source to download the CAM and most CAMeLots is the BSC LEX and the official support is given on \[SC4 Devotion\]." - RippleJet, 9 December 2007*

More information can be found [here](http://sc4devotion.com/forums/index.php?topic=3178.0).

## Old Region Integration

> **Note:** This article needs expanding.

## CAM Workforce Bug

There is a known bug in CAM that can cause distortions to the workforce. Information about this bug and the fix for it can be found [here](http://sc4devotion.com/forums/index.php?topic=14574.0).

## FAQs

> **Note:** This article needs expanding.

## Sources

- CAM Board at SC4D [1](http://sc4devotion.com/forums/index.php?board=185.0)
- CAM Manual 1.0 [2](http://sc4devotion.com/forums/index.php?action=dlattach;topic=1877.0;attach=1106)
- [Posts donated by ](/cam/posts)[xxdita](/people/xxdita)
