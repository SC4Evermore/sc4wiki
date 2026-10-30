---
title: "Savegame"
description: ""
published: false
date: '2025-01-13T17:50:05Z'
tags: ["Savegame", "Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-22T04:03:01Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**Savegame (.sc4)** files are [DBPF](/dbpf) files, containing a number of files specific to the city. They can be opened with [Reader](/reader) and the [SC4 Savegame Explorer](/sc4-savegame-explorer).

It was long thought that it was impossible to modify savegames because the files within it are protected with a CRC checksum. The game refuses to load certain files if it detects the checksum of the file is invalid. This means that every modification to a file in the Savegame requires the checksum to be recalculated as well.

The algorithm used for the checksum was discovered by during his work on the Prop Pox Fix and was picked up by to build a proof of concept that Savegames could in fact be edited which led to an experimental fix for ploppable residentials.

A JavaScript library is available with implementations of various subfiles on GitHub: **https://github.com/sebamarynissen/sc4** It automatically recalculates the checksums upon saving, so it can be used to modify savegames.

## Files Within Savegames

A file within a Savegame may consist of multiple *records*. Almost every record in the Savegame files has the following structure:

    DWORD   Size
    DWORD   CRC
    DWORD   Memory
    BYTES   All the rest

where

- Size is the length of the record in bytes
- CRC is the CRC Checksum of the record. This is calculated by running the entire record (with a maximum of 250,000 bytes) through the Checksum algorithm, ''except' for the first 8 bytes (which is the Size and the CRC itself).
- Memory is a unique identifier of the record. The game probably simply uses the numerical value of the pointer to the record for this. Never set this to 0x00000000 or you'll crash the game. Records are often referenced in other record using pointers. Those are always stored in the Subfiles as two conesecutive DWORDs: Address and TypeID. Hence, if you are decoding a subfile and find a seemingly random sequence of 4 bytes, check if the next 4 bytes (read as a 32 bit **LE** integer) correspond to a know Type ID. In that case, you're dealing with a pointer.

Below follows a list of all files that can appear within a Savegame. Note that most can be identified by [Type Id](/type-id) alone. Not every file has been fully decoded yet, although the most important ones such as the [Lot Subfile](/lot-subfile) and the [Building Subfile](/building-subfile) have been more or less fully decoded.

| Type ID | Group ID | Instance ID | Name | C++ Class | Status |
|----|----|----|----|----|----|
| ead4ba36 | 299b2d1b |  |  | cSC4CityDetailManager |  |
| eac937b4 |  |  | [Environmental Advisor/Fluffy News Advisor](/advisor-subfiles#environmental-eac937b4) | cSC4Advisor |  |
| ea863423 |  |  |  | cSC4GetawayVan |  |
| ea3ff4f5 | ea3ff506 | ea3ff4f5 | Separator File | SC4ReadAppLoadSaveVersion | Done |
| ea230a28 |  |  |  | cSC4SeaportDeveloper |  |
| ea19e825 |  |  | [Public Safety Advisor](/advisor-subfiles#public-safety-ea19e825) | cSC4AdvisorSafety |  |
| ea0a5acf |  |  |  | cSC4PipeConnectionOccupant |  |
| ea09d4ae |  |  |  | cSC4LandfillDeveloper |  |
| e9c622d8 |  |  |  | cSC43DRender |  |
| e9a6cd3b |  |  |  | cSC4NetworkLotManager |  |
| e990c18e |  |  |  | cSC4LandValueSimulator |  |
| e990c045 |  |  |  | cSC4FlammabilitySimulator |  |
| e990bffc |  |  | [Budget Subfile](/budget-subfile) | cSC4DepartmentBudget | Partially Decoded |
| e990be01 |  |  | [Budget Subfile](/budget-subfile) | cSC4BudgetSimulator | Partially Decoded |
| e98f9525 |  |  | [Terrain subfiles](/terrain-subfiles) | cSTETerrain |  |
| e86b1eef | e86b1eef | 286b1f03 | [Directory File](/dir) | cGZDBSegmentPackedFile | Done |
| e0d07233 |  |  | [Pro-Reading Ordinance](/ordinance-subfiles) | cSC4OrdinanceProReadingCampaign | Mostly Decoded |
| e0d0722e |  |  | [Nuclear-Free Ordinance](/ordinance-subfiles) | cSC4OrdinanceNuclearFreeZone | Mostly Decoded |
| cbeb4f62 |  |  | Advisor? | cSC4Airplane |  |
| cbc14674 |  |  |  | cSC4MySimDispatch |  |
| cbb32b0a |  |  |  | cSC4CarjackedVehicle |  |
| ca2c2a2f |  |  | [Utilities Advisor](/advisor-subfiles#utilities-ca2c2a2f) | cSC4AdvisorUtility |  |
| ca16374f |  |  | [Network Subfile 2](/network-subfiles#network-subfile-2-ca16374f) | cSC4SubwayOccupant | Done |
| ca15ed6b |  |  |  | cSC4SubwayConnectionOccupant |  |
| ca14ca03 |  |  |  | cSC4AutomataControllerManager |  |
| ca09f543 |  |  | Advisor? (The template for the other advisors?) | cSC4AdvisorBase |  |
| ca027edb | ca027ee1 |  | [Region View City Data](/region-view-subfiles) | SC4ReadRegionalCity | Partially Decoded |
| c9efb016 |  |  |  | cSC4PropOccupantBurntBuilding |  |
| c9c628ec |  |  |  | cSC4CameraControl |  |
| c9c05c6e |  |  | [Network Subfile 1](/network-subfiles#network-subfile-1-c9c05c6e) | cSC4NetworkOccupant | Done |
| c9c05c5d |  |  |  | cSC4PowerLineOccupant |  |
| c9bd5d4a |  |  | [Lot Subfile](/lot-subfile) | cSC4Lot |  |
| c9b84e10 |  |  | [Terrain subfiles](/terrain-subfiles) | cSTETerrainView3D |  |
| c990c0a4 |  |  |  | cSC4NeighborsSimulator |  |
| c990c034 |  |  |  | cSC4FloraSimulator |  |
| c990bd46 |  |  | \|[Network Manager Subfile](/network-subfiles#network-manager-subfile-0xc990bd46) | cSC4NetworkManager | Fully decoded |
| c98f9d4a |  |  |  | cSC4AircraftManager |  |
| c98f9d17 |  |  |  | cSC4PedestrianManager |  |
| c97f987c |  |  | [Texture Subfile](/texture-subfile) | cSC4LotBaseTextureOccupant | Mostly Decoded |
| c2f6e81f |  |  | [Tire Recycling Ordinance](/ordinance-subfiles) | cSC4OrdinanceTireRecycling | Mostly Decoded |
| c2bf1e04 |  |  | [Auto Emission Ordinance](/ordinance-subfiles) | cSC4OrdinanceVehicleEmissionStandard | Mostly Decoded |
| c2bf1dc5 |  |  | [Youth Curfew Ordinance](/ordinance-subfiles) | cSC4OrdinanceYouthCurfew | Mostly Decoded |
| ab72fbb3 |  |  | Signs | cSC4SignpostOccupant |  |
| aa9f4a3d |  |  | Automata | cSC4Bus |  |
| aa5292d7 |  |  | [Finance Advisor](/advisor-subfiles#finances-aa5292d7) | cSC4AdvisorFinance |  |
| aa3fe6bc |  |  |  | cSC4ParkManager |  |
| aa3836fb |  |  | [Tutorial Subfile](/tutorial-subfile) | cSC4TutorialSystem |  |
| aa371c32 |  |  | [Reward Advice Subfile](/advice-subfiles#reward-aa371c32) | cSC4RewardAdvice |  |
| aa313c9f |  |  | [Budget Subfile](/budget-subfile) | cSC4LineItem | Mostly Decoded |
| aa2049a1 |  |  |  | cSC4AirportDeveloper |  |
| aa09dc28 |  |  |  | cSC4PedestrianOneShot |  |
| a9dd6ff4 | e98f9525 | 00000067 | Reconcile Map South Side | cSTETerrain::SaveEdgeAltitudes | Almost Complete |
| a9dd6ff4 | e98f9525 | 00000066 | Reconcile Map East Side | cSTETerrain::SaveEdgeAltitudes | Almost Complete |
| a9dd6ff4 | e98f9525 | 00000065 | Reconcile Map North Side | cSTETerrain::SaveEdgeAltitudes | Almost Complete |
| a9dd6ff4 | e98f9525 | 00000064 | Reconcile Map West Side | cSTETerrain::SaveEdgeAltitudes | Almost Complete |
| a9dd6ff4 | e98f9525 | 00000001 | [Terrain Map](/terrain-subfiles) | cSTETerrain::SaveAltitudes | Done |
| a9c8647c | e9c8647e | 00000001 |  | cSC4View3DWin |  |
| a9c741b3 |  |  |  | cSC4ModelMaker |  |
| a9c05c85 |  |  | [Flora Subfile](/flora-subfile) | cSC4FloraOccupant |  |
| a9bd882d |  |  | [Building Subfile](/building-subfile) | cSC4BuildingOccupant | Basic Overlay Done |
| a9bc9ab6 |  |  |  | cSC4Occupant |  |
| a990c08e |  |  |  | cSC4OrdinanceSimulator |  |
| a990c022 |  |  |  | cSC4IndustrialSimulator |  |
| a990bfe0 |  |  | [Lot Developer Subfile](/lot-developer-subfile) | cSC4LotDeveloper | Done |
| a990bd10 |  |  |  | cSC4PropManager |  |
| a98f9d3b |  |  |  | cSC4VehicleManager |  |
| a98f9d28 |  |  |  | cSC4WatercraftManager |  |
| a97f909e |  |  |  | cSC4ConstructionOccupant |  |
| a7e7f929 |  |  |  | cSC424HourClock |  |
| a2bf1e43 |  |  | [Clean Air Ordinance](/ordinance-subfiles) | cSC4OrdinanceCleanAir | Mostly Decoded |
| a2bf1de5 |  |  | [Commuter Shuttle Ordinance](/ordinance-subfiles) | cSC4OrdinanceShuttleService | Mostly Decoded |
| a2bf1ddc |  |  | [Carpool Ordinance](/ordinance-subfiles) | cSC4OrdinanceCarpoolIncentive | Mostly Decoded |
| a0d07129 |  |  | [Legal Gambling Ordinance](/ordinance-subfiles) | cSC4OrdinanceLegalizeGambling | Mostly Decoded |
| 8be3753b |  |  | [City Situations Advice Subfile](/advice-subfiles#city-situations-8be3753b) | cSC4CitySituationAdvice |  |
| 8ba98eda |  |  |  | cSC4Helicopter |  |
| 8b79c707 |  |  | Painted Labels | cSC4TextDecalOccupant |  |
| 8a91e7e3 | e98f9525 | 00000003 | [Terrain Subfiles](/terrain-subfiles#terrain-bounding-box-0x8a91e7e3) | cSTETerrain::SaveMiscTerrainData |  |
| 8a91e7e0 | e98f9525 | 00000002 | [Terrain Subfiles](/terrain-subfiles#terrain-flags-0x8a91e7e0) | cSTETerrain::SaveVertexProperties |  |
| 8a4bd52b |  |  | \|[Network Tunnel Subfile](/network-subfiles#network-tunnel-subfile-0x8a4bd52b) | cSC4NetworkTunnelOccupant |  |
| 8a41625a |  |  |  | cSC4Train |  |
| 8a2482b9 | 4a2492bb | 00000006 | [PNG](/png) File | cSC4City::WriteRegionViewThumbnail | Done |
| 8a2482b9 | 4a2492bb | 00000004 | [PNG](/png) File | cSC4City::WriteRegionViewThumbnail | Done |
| 8a2482b9 | 4a2492bb | 00000002 | [PNG](/png) File | cSC4City::WriteRegionViewThumbnail | Done |
| 8a2482b9 | 4a2492bb | 00000000 | [PNG](/png) File | cSC4City::WriteRegionViewThumbnail | Done |
| 8a22bebe |  |  |  | cSC4LandfillOccupant |  |
| 8a09f5f4 |  |  | [Advice Subfiles](/advice-subfiles) | cSC4Advice |  |
| 89efa536 |  |  | [Historical Data of City/Graph Data](/historical-graphs-subfiles) | cSC4HistoryWarehouse | Mostly Decoded |
| 89d9b9ee | 69d9b9f1 |  |  | cSC4AutoSaveRecord | Stores cGZCheatCodeManager::GetCheatCodeSaveData |
| 89c49986 |  |  |  | cSC4WealthRequester |  |
| 89c48f47 |  |  |  | cSC4PropDeveloper |  |
| 8990c372 |  |  | Mayor View City Data | cSC4City |  |
| 8990c12d |  |  |  | cSC4Demand |  |
| 8990c09a |  |  |  | cSC4CrimeSimulator |  |
| 8990c080 |  |  |  | cSC4CommercialSimulator |  |
| 8990c065 |  |  | Water Pollution | cSC4PollutionSimulator |  |
| 8990be7a |  |  |  | cSC4BuildingDevelopmentSimulator |  |
| 896e75af |  |  |  | cSC4Pedestrian |  |
| 896e714a |  |  | [Vehicle Automata](/automata-subfiles#vehicle-automata-subfile-0x896e714a) | cSC4Vehicle |  |
| 82b9999b |  |  | [Power Conservation Ordinance](/ordinance-subfiles) | cSC4OrdinancePowerConservation | Mostly Decoded |
| 815b4cef |  |  | [Junior Sports Ordinance](/ordinance-subfiles) | cSC4OrdinanceJuniorSportsLeague | Mostly Decoded |
| 6c1acde1 |  |  |  | cSC4Ambulance |  |
| 6b70efad |  |  |  | cSC4MySimBalloonAdvice |  |
| 6a9335de |  |  | [MySim Advice Subfile](/advice-subfiles#mysim-6a9335de) | cSC4MySimAdvice |  |
| 6a5f8755 |  |  | [Health &amp; Education Advisor](/advisor-subfiles#health-and-education-6a5f8755) | cSC4AdvisorHQ |  |
| 6a3848db |  |  | [Advice Subfiles](/advice-subfiles) | cSC4AdviceNeghborDeal |  |
| 6a26d049 |  |  |  | cSC4AdviceSubject |  |
| 6a1628ba |  |  |  | cSC4AutomataAttractor |  |
| 6a0f82b2 |  |  | [Network Index Subfile](/network-subfiles#network-index-subfile-6a0f82b2) | cSC4TrafficNetworkMap | Decoded |
| 6990c1aa |  |  | Sims to Jobs Match | cSC4TrafficSimulator |  |
| 6990c04f |  |  |  | cSC4PoliceSimulator |  |
| 6534284a |  |  | [Type 10 Exemplars](/exemplar) |  | Decoded. |
| 62f6e7cf |  |  | [Tourism Ordinance](/ordinance-subfiles) | cSC4OrdinanceTouristPromotion | Mostly Decoded |
| 62bf1db9 |  |  | [Neighborhood Watch Ordinance](/ordinance-subfiles) | cSC4OrdinanceNeighborhoodWatch | Mostly Decoded |
| 62bf1daa |  |  | [Smoke Detector Ordinance](/ordinance-subfiles) | cSC4OrdinanceMandatorySmokeDetectors | Mostly Decoded |
| 4c22ae53 |  |  | [El Train and Monorail Automata](/automata-subfiles#mass-transit-train-subfile-0x4c22ae53) | cSC4MassTransitTrain |  |
| 4c0dd224 |  |  |  | cSC4MayorLimo |  |
| 4c0ae114 |  |  |  | cSC4FirePlaneDispatchSource |  |
| 4be372cd |  |  | [Situation Manager](/advisor-subfiles#city-situations-4be372cd) | cSC4AdvisorCitySituations |  |
| 4a5b69ed |  |  | Automata | cSC4TrailerVehicle |  |
| 4a416254 |  |  | Automata | cSC4TrainCar |  |
| 4a3ad3e1 |  |  | [Transportation Advisor](/advisor-subfiles#transportation-4a3ad3e1) | cSC4AdvisorTraffic |  |
| 4a232da8 |  |  | [Industry Subfile](/industry-subfile) | cSC4BusinessUnit |  |
| 4a222b98 |  |  | Automata | cSC4PatrolCar |  |
| 4a1dbbbf |  |  | [MySim Advisors](/advisor-subfiles#mysim-4a1dbbbf) | cSC4MySim |  |
| 4a1b664e |  |  |  | cSC4AutomataScriptSystem |  |
| 4a1628c5 |  |  | Wildlife Generator | cSC4AutomataGenerator |  |
| 4a0dd616 |  |  |  | cSC4AdvisorSystem |  |
| 49dd6f4c | 49dd6f4e | 00000001 | [City Pointer](/city-pointer) |  | Contains a single pointer to the cSC4City |
| 49cc1bcd |  |  | \|[Network Bridge Subfile](/network-subfiles#network-bridge-subfile-0x49cc1bcd) | cSC4NetworkBridgeOccupant |  |
| 49c1a034 |  |  | \|[Prebuilt Network Subfile](/network-subfiles#prebuilt-network-subfile-0x49c1a034) | cSC4NetworkOccupantWithPreBuiltModel | Mostly done |
| 49c05c9f |  |  | Lot Retaining Walls | cSC4LotRetainingWallOccupant |  |
| 49c05c8f |  |  | Props | cSC4FoundationOccupant |  |
| 49c05b9f |  |  | [Pipe Occupant Subfile](/pipe-occupant-subfile) | cSC4PipeOccupant | Done |
| 49b9e60a |  |  | [SimGrid](/simgrid) | cSC4SimGridFloat32 | Mostly decoded |
| 49b9e606 |  |  | [SimGrid](/simgrid) | cSC4SimGridUint32 | Mostly decoded |
| 49b9e605 |  |  | [SimGrid](/simgrid) | cSC4SimGridSint16 | Mostly decoded |
| 49b9e604 |  |  | [SimGrid](/simgrid) | cSC4SimGridUint16 | Mostly decoded |
| 49b9e603 |  |  | [SimGrid](/simgrid) | cSC4SimGridSint8 | Mostly decoded |
| 49b9e602 |  |  | [SimGrid](/simgrid) | cSC4SimGridUint8 | Mostly decoded |
| 499b23fe |  |  |  | cSC4COMSerializer::SaveClassObjects |  |
| 4990c013 |  |  |  | cSC4ResidentialSimulator |  |
| 4990bd93 |  |  |  | cSC4DispatchManager |  |
| 498f9b01 |  |  | [Zone Developer Subfile](/zone-developer-subfile) | cSC4ZoneDeveloper | Done |
| 42bf1e18 |  |  | [Trash Presort Ordinance](/ordinance-subfiles) | cSC4OrdinanceTrashPresort | Mostly Decoded |
| 40d07236 |  |  | [Free Clinic Ordinance](/ordinance-subfiles) | cSC4OrdinanceFreeClinics | Mostly Decoded |
| 2b689130 |  |  | Deals |  |  |
| 2a5f877d |  |  | [City Planner Advisor](/advisor-subfiles#city-planner-2a5f877d) | cSC4AdvisorCityPlanning |  |
| 2a134f42 |  |  |  | cSC4NeighborDeal |  |
| 2990c1e5 |  |  | [Date Subfile](/date-subfile) | cSC4Simulator | Partially Decoded |
| 2990c1bc |  |  | Terrain Arrays | cSC4WeatherSimulator | Basic Overlay Completed |
| 2990c142 |  |  |  | cSC4TractDeveloper |  |
| 2990c05a |  |  |  | cSC4FireProtectionSimulator |  |
| 2990bff2 |  |  |  | cSC4DemandSimulator |  |
| 299062c0 |  |  |  | cSC4LotConfigurationManager |  |
| 2977aa48 |  |  | Prop Terrain Decal | cSC4PropOccupantTerrainDecal |  |
| 298f9b2d |  |  | [Zone Manager](/zone-manager) | cSC4ZoneManager | Partially decoded |
| 2977aa49 |  |  | Prop Visual Effect | cSC4PropOccupantVisualEffect |  |
| 2977aa47 |  |  | [Prop Subfile](/prop-subfile) | cSC4PropOccupant |  |
| 22f6e81b |  |  | [Paper Waste Ordinance](/ordinance-subfiles) | cSC4OrdinancePaperReductionAct | Mostly Decoded |
| 22f6e80c |  |  | [Landfill Gas Ordinance](/ordinance-subfiles) | cSC4OrdinanceLandfillGasRecovery | Mostly Decoded |
| 2026960b | 4a2482bb | 00000007 | Temp.[PNG](/png) file | cSC4City::WriteRegionViewThumbnail | Done |
| 2026960b | 4a2482bb | 00000005 | Temp.[PNG](/png) file | cSC4City::WriteRegionViewThumbnail | Done |
| 2026960b | 4a2482bb | 00000003 | Temp.[PNG](/png) file | cSC4City::WriteRegionViewThumbnail | Done |
| 2026960b | 4a2482bb | 00000001 | Temp.[PNG](/png) file | cSC4City::WriteRegionViewThumbnail | Done |
| 0c0b06e8 |  |  |  | cSC4PoliceHelicopterDispatchSource |  |
| 0bf606a5 |  |  | [My Street Sim](/advisor-subfiles#my-street-sim-0bf606a5) | cSC4MyStreetSim |  |
| 0bb14381 |  |  |  | cSC4CitySituationManager |  |
| 0b7d45e0 | 0b7d45e1 | 0b7d45e2 |  |  |  |
| 0a413481 |  |  | Reward Requirements | cSC4CivicBuildingSimulator |  |
| 0a134f24 |  |  |  | cSC4NeighborConnection |  |
| 09c05c6a |  |  |  | cSC4PowerPoleOccupant |  |
| 0990c38a |  |  |  | cSC4Demolition |  |
| 0990c138 |  |  |  | cSC4GrowthDeveloper |  |
| 0990c075 |  |  | [Plumbing Simulator](/plumbing-simulator) | cSC4PlumbingSimulator | Done |
| 0990c005 |  |  | [Power Simulator Subfile](/power-simulator-subfile) | cSC4PowerSimulator | Basic Overlay Completed |
| 0990bdd8 |  |  |  | cSC4AuraSimulator |  |
| 098f964d |  |  | [Item Index Subfile](/item-index-subfile) | cSC4OccupantManager |  |
| 096e75f5 |  |  |  | cSC4Watercraft |  |
| 02bf1dfa |  |  | [Water Conservation Ordinance](/ordinance-subfiles) | cSC4OrdinanceWaterConservation | Mostly Decoded |
| 00d0723d |  |  | [Community CPR Ordinance](/ordinance-subfiles) | cSC4OrdinanceCommunityCPRTraining | Mostly Decoded |

## Source code

Here's a link to the **CRC algorithm on GitHub**, the algorithm used for the savegame file checksum. It's useful to know that only the first 250,000 bytes need to run through the algorithm. This is probably done to speed up the saving process.

  
  
**https://github.com/sebamarynissen/SC4/blob/ee7bee8173ec46d155ceaa316eaab074404dff87/src/crc.cpp**
