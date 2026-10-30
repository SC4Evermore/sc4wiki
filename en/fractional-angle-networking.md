---
title: "Fractional Angle Networking"
description: ""
published: true
date: '2019-08-10T08:44:42Z'
tags: ["NAM/project"]
editor: markdown
dateCreated: '2008-07-30T11:56:51Z'
---

<div class="infobox">
<table>
<tr><th colspan="2">Fractional Angle Networking</th></tr>
<tr><td><strong>Status</strong></td><td>Released</td></tr>
<tr><td><strong>Language</strong></td><td>English</td></tr>
<tr><td><strong>No link</strong></td><td>yes</td></tr>
</table>
</div>

**Fractional Angle Networking** is an effort by several [NAM Team](/nam-team) members to break road and rail networks out of the [orthogonal](https://en.wikipedia.org/wiki/orthogonal)/[diagonal](https://en.wikipedia.org/wiki/diagonal) grid. The road side of the project is called the **FAR** (**Fractional Angle Roads**) and the rail side, not surprisingly, is called the **FARR** (**Fractional Angle Railroads**). The reason these pieces are called "fractional angle" curves is because, even though they are neither orthogonal nor diagonal, they are still constrained by SC4's grid, albeit the additional angle variety loosens the impositions that the grid places on network placement. There are currently two different fractional angles employed: **FA-3** (18.4/71.6 degrees), and more recently, **FA-2** (26.6/63.4 degrees). They are named with respect to how they lay on the SC4 grid: FA-3 is named such because it requires 3 tiles on the x-axis to move 1 tile on the y-axis, and for FA-2, the figures are 2 tiles on the x-axis for 1 tile on the y-axis. Other proposed angles have included FA-4, FA-6, and FA-1.5, though there is no concrete plan with respect to their implementation at present.

The concept originated in the early spring of 2008 with a post in [Three Rivers Region](/three-rivers-region) (3RR) by [dedgren](/people/dedgren) proposing the FAR and developing a set of texture-based road curves . Within a short time, [dedgren](/people/dedgren) and [Tarkus](/people/tarkus), who had worked together the previous year on a similar project that became the [NAM](/nam) wide curves, had a working set of FAR pieces. In the early summer of 2008, [dedgren](/people/dedgren) expanded the concept to dual-rail, and once again he and [Tarkus](/people/tarkus) collaborated on creating the initial set of FARR pieces. [Shadow Assassin](/people/shadow-assassin) later expanded the fractional angle options to include the [RealHighway](/realhighway) system (**FARHW**), with the release of RealHighway Version 4.0 in May 2010 (coincident with NAM 28), and later, he developed Fractional Angle Avenues.

The biggest development with respect to fractional angles came with [memo](/people/memo)'s development of **Draggable Fractional Angle Networking**, which uses [INRUL](/inrul) and [RUL2](/rul2) code to transform draggable patterns into fractional angled networks. As of the NAM 31.x-series releases, the draggable approach is currently only available for Roads, in both FA-3 and FA-2 angles.

## Notes
