---
title: "FLEX Turn Lanes"
description: ""
published: true
date: '2019-08-04T22:57:04Z'
tags: ["NAM/doc"]
editor: markdown
dateCreated: '2016-07-11T06:01:52Z'
---

<!-- unconverted template: current -->

**FLEX Turn Lanes** (**FTLs**) are a new implementation of turn lane functionality, designed by [memo](/people/memo) and [Tarkus](/people/tarkus), due to come online in an upcoming NAM release. The FTL system is a draggable/starter piece-based refinement of the earlier **Turn Lane Extension Pieces** (**TuLEPs**).

## Using FLEX Turn Lanes

## FLEX Turn Lane Types and Nomenclature

The nomenclature for FTL types is identical to the later system for TuLEPs, and involves a three-digit number. The first digit is a representation of the number of *inner turn lanes* (left turn lanes in Right-Hand Traffic, right for Left-Hand Traffic), while the second indicates the number of *through lanes* on the network, and the third digit indicates the number of *outer turn lanes* (right turn lanes in Right-Hand Traffic, left for Left-Hand Traffic). For instance, adding a single inner turn lane to a Road would generate a Type 110 setup, as there is one inner turn lane, one through lane, and zero outer turn lanes. Adding an outer turn lane would make it a Type 111 (which is not presently available). Below is a listing of all current types and related networks:

- **Type 110** - Road, TLA-3, AVE-2, ARD-3
- **Type 120** - Avenue, TLA-5
- **Type 220** - Avenue, TLA-5
- **Type 130** - TLA-7, AVE-6

In addition to these types, as discussed in the usage section, the FTL system also includes single slip lanes.

## FLEX Turn Lane Options

> **Note:** This article needs expanding.
