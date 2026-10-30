---
title: "Model Exemplar"
description: ""
published: true
date: '2023-01-29T15:49:41Z'
tags: ["Transit Networks", "Transit Modding"]
editor: markdown
dateCreated: '2008-05-29T07:11:12Z'
---

**Model Exemplars** are exemplars which relate [transit models](/transit-modeling) to the various [RUL Files](/rul-file). There are two different types of Model Exemplars, **Puzzle Piece Model Exemplars** and **Draggable Network Model Exemplars**. Both types of exemplars generally use [RTK0](/resource-key-type) or [RTK3](/resource-key-type) to reference the models. RKT3 is more commonly used on the Rail-type networks.

**Puzzle Piece Model Exemplars** specify models for use as puzzle pieces, relating them to [RUL 0x10000000](/rul-0x10000000). They always have the [Group ID](/group-id) (GID) *0xA8434037*.

**Draggable Network Model Exemplars** relate the models to the RULs which deal with draggable networks, including the [Individual Network RULs](/individual-network-ruls), [RUL 0x10000001](/rul-0x10000001) and [RUL 0x10000002](/rul-0x10000002). They are referenced in the RULs in much the same manner as textures, using the [Instance ID](/instance-id) (IID) for the exemplar.

**Underground Network Models**(Subway/Water pipes) do not use exemplars.

## Group IDs

The GID for the Draggable Network Model Exemplar varies based on the network for which the model is to be used, sometimes known as a **Network-Specific GID** (NSGID). A listing of all known NSGIDs is shown below.

    0x2821ED93    Road
    0xA92A02EA    Street
    0xCBE084CB    One-Way Road
    0xCB730FAC    Avenue
    0xA8434037    Elevated Highway
    0xEBE084D1    Ground Highway
    0x6BE08658    RHW
    0xE8347989    Heavy Rail
    0x2B79DFFB    Light Rail
    0xEBE084C2    Monorail
    0x8A15F3F2    Subway
    0x088E1962    Powerline
