---
title: "City Pointer"
description: ""
published: false
date: '2025-01-13T18:52:05Z'
tags: []
editor: markdown
dateCreated: '2025-01-13T17:52:45Z'
---

This file has TGI 0x49dd6f4c-0x49dd6f4e-0x00000001, is always 12 bytes long, and just contains a pointer to the cSC4City. If this file is not present, the city is not shown in the region view.

    WORD    Major version (0x0001)
    WORD    Minor version (0x0002)
    DWORD   Pointer to cSC4City
    DWORD   TypeID of cSC4City (0x8990c372)
