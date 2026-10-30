---
title: "Cohort"
description: ""
published: false
date: '2019-08-04T05:40:33Z'
tags: ["Modding"]
editor: markdown
dateCreated: '2012-08-03T03:44:51Z'
---

A **Cohort** is very similar to an [Exemplar](/exemplar), and the two file types share the same [format](/exmp). All cohorts have the [Type ID](/type-id) 0x05342861. Like an exemplar, a cohort contains a series of properties. Unlike an exemplar, a cohort can pass these properties down to other cohorts and exemplars that have been grouped as "children" to this "parent" cohort. A cohort family tree can be at least three generations deep, that is containing two levels of cohorts and one of exemplars, as shown below.

Cohort tree, showing three "generations":

`         Cohort`  
`        /      \`  
`    Cohort    Cohort`  
`       |        |`  
`   Exemplar   Exemplar`  
`   Exemplar   Exemplar`  
`   Exemplar   Exemplar`  
`   Exemplar   Exemplar`  
`   Exemplar   Exemplar`  
`     ...        ...`

A parent cohort value of 0x00000000 0x00000000 0x00000000 indicates that a particular cohort or exemplar is at the "top" of its cohort tree, and has no parent.
