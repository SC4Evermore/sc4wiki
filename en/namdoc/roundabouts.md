---
title: "Roundabouts"
description: ""
published: true
date: '2020-02-17T02:48:51Z'
tags: ["NAM/doc", "NAM User Guide pages updated to NAM 36"]
editor: markdown
dateCreated: '2015-08-22T13:01:27Z'
---

Roundabouts are a component of the [NAM](/nam), which are used to reduce traffic congestion for intersections. Different variations exist for Roads (2x2), Streets (2x2), One-Way Roads (3x3) and Avenues (4x4) which can be selected individually in the installer.

## Road Roundabouts

To trigger the initial Road roundabout, you must draw a Road circle in a 2x2 tile area using the Road network tool. It interfaces with up to 4 entrances, one on each corner:

- Street
- Road (RD-2)
- One Way Road (OWR-2)

Road (RD-2) entrances can be orthogonal or diagonal, but Streets only interface cleanly with an orthogonal entrance, in [NAM 36](/category/nam-user-guide-pages-updated-to-nam-36).

One Way Roads (OWR-2) interface cleanly on a diagonal if you first draw a single-tile One Way Road stub, and then draw the diagonal One Way Road through the stub to the roundabout.

  
  
<figure>
<img src="/_files/images/road-roundabout.jpg" title="Road_Roundabout.jpg" />
<figcaption>Road_Roundabout.jpg</figcaption>
</figure>

If there are four entrances used, there must be a maximum of only 2 One Way Roads.

## Street Roundabouts

Street roundabouts are triggered in the same way as Road roundabouts, but using the Street network tool to draw a 2x2 circle. It interfaces with up to 4 entrances, one on each corner, either orthogonal or diagonal:

- Street
- Road (RD-2)
- One Way Road (OWR-2)

If there are four entrances, at least one of them must be a Street, in [NAM 36](/category/nam-user-guide-pages-updated-to-nam-36).

  
  
<figure>
<img src="/_files/images/street-roundabout.jpg" title="Street_Roundabout.jpg" />
<figcaption>Street_Roundabout.jpg</figcaption>
</figure>

## One-Way Road Roundabouts

To trigger the initial One-Way Road roundabout, you must draw a One-Way Road circle in a 3x3 tile area. This 3x3 roundabout handles higher traffic volumes than the 2x2 Road and Street roundabouts. It interfaces with one, two, three or four entrances on either orthogonal or diagonal entry:

- Street (orthogonal only)
- Road (RD-2)
- One Way Road (OWR-2)
- 2-lane Highway (RHW-2)
- Single lane Highway (MIS)

Notice in the screenshot below, that highway grade entrances (RHW-2 and MIS) display no pedestrian crossing. Under some circumstances, you may be able to interface a fifth entrance.

  
  
<figure>
<img src="/_files/images/onewayroad-roundabout.jpg" title="OneWayRoad_Roundabout.jpg" />
<figcaption>OneWayRoad_Roundabout.jpg</figcaption>
</figure>

To interface this 3x3 roundabout with the NWM additional road types, you will need a single tile stub of Road (RD-2) or One Way Road (OWR-2).

## Avenue Roundabouts

Avenue roundabouts are [FLEX](/flex) puzzle pieces which can be found under the *Avenue Roundabouts and Interchanges* button. Each type of Avenue roundabout can be accessed using Tab and Shift-Tab keys while in preview, in [NAM 36](/category/nam-user-guide-pages-updated-to-nam-36) as follows:

- Roundabout Avenue 4x4
- Roundabout Avenue 4x4 with offset diagonal avenue
- Highway over Avenue Roundabout
- Avenue Roundabout with GLR
- GLR-Avenue roundabout - curve
- GLR-Avenue roundabout - T-junction
- GLR-Avenue roundabout - 4way-junction
- Highway above GLR-Avenue roundabout
- Avenue Y-Stack
- Freeway Exit - Straight
- Turbo Roundabout, AVE-4 (Home/End for variations)
- Turbo Roundabout, RD-4 (Home/End for variations)
- Turbo Roundabout, RD-6 (Home/End for variations)
- Roundabout, AVE-4 x ARD-3 (Home/End for variations)
- Roundabout, RD-4 x ARD-3 (Home/End for variations)
- Roundabout, RD-6 x ARD-3 (Home/End for variations)

As you can see, there is an extraordinary range of Avenue roundabout types and features to explore!

After placing down one of these puzzle pieces, you can drag orthogonal and diagonal Avenues into the roundabout in order to connect it with the rest of your network. By default, the Roundabout Avenue 4x4 comes with [FLUP](/flup) support. If this functionality is not required, you can bulldoze the inner 2x2 tile fountain prop after building the roundabout and replace it by any other items. There are also a few Avenue roundabout variations including crossings with Elevated Highway and [GLR](/glr).

<figure>
<img src="/_files/images/elevated-highway-and-flup-roundabouts-nam36.jpg" title="Elevated_Highway_and_FLUP_Roundabouts_(NAM36).jpg" />
<figcaption>Elevated_Highway_and_FLUP_Roundabouts_(NAM36).jpg</figcaption>
</figure>

Note that the same button also contains the Avenue Y-Stack interchange and turbo roundabouts.

## Turbo Roundabouts

Turbo roundabouts are static puzzle pieces that can be found under the *Avenue Roundabouts and Interchanges* button and serve as circular intersections between a double-tile and a single-tile network, such as Avenue/RD-4/RD-6 and ARD-3/[TuLEPs](/tuleps). In order to make sure they can be properly connected to your network, it is advisable to bulldoze a 2x1 tile intersection between two suitable networks and plop the turbo roundabout onto the resulting gap.
