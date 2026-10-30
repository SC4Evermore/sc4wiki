---
title: "LUAAdvice"
description: ""
published: true
date: '2019-08-04T05:40:51Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-09T20:17:34Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**Advice LUA's** are an important type of [LUA](/lua). They are composed of 4 blocks total.

## Specification

### Start Block

`Dofile("filename.lua") -- load this file before parsing and executing`

### Helper block

This block contains helper functions. Helper functions do things based on LUA system script and constants from advices such as a.type.

    function create_advice_transportation_with_base(guid_string, base_advice)
       local a =  advices : create_advice(tonumber(guid_string, 16), base_advice)
       a.type = advice_types . TRANSPORTATION
       return a
    end

### Advice Block

The following is an annotated Advice Block for a game advice to build roads upon the start of a new city. It demonstrates the commands used in this block, and potential values for these commands. Any of the following necessary things may be used.

    a = create_advice_transportation('2a355b3b')
          -- Advice ID to create.
    a.trigger  = "game.g_month > 3"
          -- Triggers for this advice. For example, game months over 3.
    a.once = 1
          -- Execute this advice only once per game.
    a.timeout = tuning_constants.ADVICE_TIMEOUT_MEDIUM
          -- How long the advice takes to timeout.
    a.title = [[text@ea50e830  Celebrate City Birth--Roads Make Perfect Gift]]
          -- Text reference for LTEXT in locale.dat to use as the title, otherwise show this title.
    a.message   = [[text @aa50e837  Greetings, Mayor. I'm Glint Wheels, your transit man,
                    here to give you the skinny on moving in the city. You can really put
                    a shine on #city# by placing some roads in good spots. And think of the
                    city's zones--the exchange of goods and services can't go anywhere unless
                    they're connected by roads. You could even zip a road 'round each zone--touring
                    your great city will be easier than ever, and your Sims will be singing with the tops down.]]
          -- Text reference for LTEXT in locale.dat to use as the message, otherwise show this message.
          -- Note the use of the variable #city# in the above text - LTEXTs can support variables and HTML code.
    a.priority = tuning_constants.ADVICE_PRIORITY_MEDIUM
          -- Advice priority on the list.
    a.mood = advice_moods.GREAT_JOB
          -- Advisor S3D model mood.
    a.type = advice_types.TRANSPORTATION
          -- Advice type.
    a.frequency = tuning_constants.ADVICE_FREQUENCY_MEDIUM
          -- Frequency to show advice.
    a.news_only = 1
          -- Show in news ticker only, not with advisers.
    a.event = game_events.NEW_CITY
          -- Execute advice on this event.

### End Block

This will try to execute triggers for all registered advices to make sure they don't have any syntactic errors.

    if (_sys.config_run == 0) -- if the config option is set to 0 in the _sys.lua, then
    then
       advices : run_triggers() -- Activate all triggers
    end

## Section Declaration Table

Here's the section declaration table for all advice.

    base_advice = 
    {
       _base = nil,     -- no base advice for itself
       guid = 0,        -- this will be persisted in saved games and will have to be set to each advice by hand. 
       class_id = hex2dec("8a09f5f4"), -- C++ advice class ID (cSC4Advice class by default) 
       type = advice_types . NULL,     -- NULL types never get triggered 
       mood = advice_moods . NEUTRAL,
       priority = 100,  -- 0 to 100 scale, 100 = highest
       title = "",
       message = "",
       frequency = 720, -- in days, 30 days min.
       timeout = 36000, -- in days, disappear message
       trigger = "0",   -- never trigger this one
       once = 0,        -- show this advice only once
       news_only = 0,   -- set to 1 for news ticker messages only 
       event = 0,       -- this has to be a valid event ID (see constants file for the event table.)
       command = 0,     -- game command to trigger along with the advice message
       persist = 0,     -- if 1, message will remain visible once triggered whether or not trigger condition remains true
                           (useful for random triggers)
       effects = {}     -- Here is the format: a.effects = {effects.POOR_FIRE_COVERAGE, effects.UNHAPPY_SIMS}
    }

These are the things that can be called during an advice. You've seen an actual advice sample above so this should be easy enough to understand.
