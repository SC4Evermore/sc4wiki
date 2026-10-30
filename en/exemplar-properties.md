---
title: "Exemplar properties"
description: ""
published: true
date: '2024-02-21T05:17:34Z'
tags: ["Modding", "MTS2"]
editor: markdown
dateCreated: '2012-09-07T21:53:20Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

The following list contains all known **[Exemplar](/exemplar) properties**, and relevant information about each as known. The list can also be [found here](/exemplar-properties-xml) in the original XML format.

## Common Properties

These properties can be found in all, or nearly all, exemplars.

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0x00000010 | Uint32 | fixed | 1 | 0x00000000 | Exemplar Type | Used by property editors to group exemplars and filter properties |
| 0x00000011 | Uint32 | fixed | 1 | 0x00000000 | Exemplar Interface ID | A GZGUID that identifies a class interface |
| 0x00000012 | Uint32 | fixed | 1 | 0x00000000 | Exemplar Class ID | A GZCLSID that identifies a class implementation |
| 0x00000020 | String | fixed | 1 |  | Exemplar Name | Identifies this exemplar in property editors |
| 0x00000021 | Uint32 | fixed | 1 | 0x00000000 | Exemplar ID | Identifies this exemplar so that C++ code and other exemplars can refer to it |
| 0x6a871b82 | Uint32 | fixed | 1 | 1 | PluginPackID | ID of the plugin pack to which the data belongs |
| 0x8a416a99 | Uint32 | fixed | 3 | 0,0,0 | User Visible Name Key | Resource key of the name of what this exemplar represents |
| 0xcaa9ab92 | Bool | fixed | 1 | True | Hover Query Only | If present, the occupant will respond to hover queries but not to click-queries |
| 0x2c8f8746 | Uint32 | fixed | 1 | 0x00000000 | Exemplar Category | Categorizes this exemplar; for debug and exemplar editors use only |

## Resource Key Type

> Main article: [Resource Key Type](/resource-key-type)

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0x27812820 | Uint32 | fixed | 3 | 0,0,0 | Resource Key Type 0 | Specifies 1 model key for all Z/R |
| 0x27812821 | Uint32 | fixed | 3 | 0,0,0 | Resource Key Type 1 | Specifies 1 model key for each Z/R |
| 0x27812822 | Uint32 | fixed | 20 | 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0 | Resource Key Type 2 | A unique instance ID for each zoom and rotation. |
| 0x27812823 | Uint32 | fixed | 7 | 0,0,0,0,0,0,0 | Resource Key Type 3 | A unique instance ID for each zoom |
| 0x27812824 | Uint32 | variable | 8 | 0,0,0,0,0,0,0,0 | Resource Key Type 4 | Multi-model, multi state (see tuning docs) |
| 0x27812825 | Uint32 | fixed | 3 | 0,0,0 | Resource Key Type 5 | Specifies 1 model key for each Z/R/state |
| 0x27812921 | Uint32 | fixed | 3 | 0,0,0 | Resource Key Type 1xm | Specifies 1 model key for each Z/R |
| 0x27812922 | Uint32 | fixed | 20 | 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0 | Resource Key Type 2xm | A unique instance ID for each zoom and rotation. |
| 0x27812923 | Uint32 | fixed | 7 | 0,0,0,0,0,0,0 | Resource Key Type 3xm | A unique instance ID for each zoom |
| 0x27812924 | Uint32 | variable | 8 | 0,0,0,0,0,0,0,0 | Resource Key Type 4xm | Multi-model, multi state (see tuning docs) |
| 0x27812925 | Uint32 | fixed | 3 | 0,0,0 | Resource Key Type 5xm | Specifies 1 model key for each Z/R/state |

## Weather Properties

### Weather Tuning

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0xa7607d70 | Sint32 | fixed | 1 | 1 | mnWeeksForCompleteTemperatureSimulation | mnWeeksForCompleteTemperatureSimulation |
| 0xa7607d71 | Sint32 | fixed | 1 | 1 | mnWeeksForCompleteMoistureSimulation | mnWeeksForCompleteMoistureSimulation |
| 0xa7607d72 | Sint32 | fixed | 1 | 1 | mnSimulationSpreadWritingRadius | mnSimulationSpreadWritingRadius |
| 0xa7607d73 | Float32 | fixed | 1 | 65 | mfYearlyAmbientTemperature | mfYearlyAmbientTemperature |
| 0xa7607d74 | Float32 | fixed | 1 | 0.5 | mfYearlyAmbientTemperatureVariation | mfYearlyAmbientTemperatureVariation |
| 0xa7607d75 | Float32 | fixed | 1 | 0.5 | mfYearlyAmbientTemperatureVariationFactor | mfYearlyAmbientTemperatureVariationFactor |
| 0xa7607d76 | Sint32 | fixed | 1 | 10 | mnSeaModerationRadius | mnSeaModerationRadius |
| 0xa7607d77 | Float32 | fixed | 1 | 0.9 | mfSeaModerationFactor | mfSeaModerationFactor |
| 0xa7607d78 | Float32 | fixed | 1 | 0.082 | mfAltitudeTemperatureFactor | mfAltitudeTemperatureFactor |
| 0xa7607d79 | Float32 | fixed | 1 | 0.25 | mfWindChillTemperatureFactor | mfWindChillTemperatureFactor |
| 0xa7607d86 | Float32 | fixed | 1 | 3 | mfYearlyAmbientWindSpeed | mfYearlyAmbientWindSpeed |
| 0xa7607d87 | Float32 | fixed | 1 | 1 | mfYearlyAmbientWindDirection\[0\] | mfYearlyAmbientWindDirection\[0\] |
| 0xa7607d88 | Float32 | fixed | 1 | 0 | mfYearlyAmbientWindDirection\[1\] | mfYearlyAmbientWindDirection\[1\] |
| 0xa7607d89 | Float32 | fixed | 1 | 60 | mfWindPerturbationRange | Angular window for periodic variation of ambient wind direction (0-90 degrees) |
| 0xa7607d7a | Float32 | fixed | 1 | 0.5 | mfYearlyAmbientMoisture | mfYearlyAmbientMoisture |
| 0xa7607d7b | Float32 | fixed | 1 | 0.2 | mfYearlyAmbientMoistureVariation | mfYearlyAmbientMoistureVariation |
| 0xa7607d7c | Float32 | fixed | 1 | 0.2 | mfYearlyAmbientMoistureVariationFactor | mfYearlyAmbientMoistureVariationFactor |
| 0xa7607d7d | Float32 | fixed | 1 | 0.50 | mfMoistureHillFactor | Wind effect on hill moisture (H20 fractional units per m/s of perpendicular wind penetration) |
| 0xa7607d7e | Float32 | fixed | 1 | 0.12 | mfValleyMoistureBoost | Moisture boost for areas detected as valleys (0-1) |
| 0xa7607d7f | Float32 | fixed | 1 | 4.0 | mfMoistureValleySlopeThreshold | Minimum concavity required to detect area as valley (linear height deviation in meters) |
| 0xa7607d80 | Uint32 | fixed | 1 | 64 | mMoistureVariationScale | Amplitude of plasma-based noise in moisture map (map creation only) |
| 0xa7607d81 | Uint32 | fixed | 1 | 15 | mMoistureDitherScale | Amplitude of high-freq. dithering noise in moisture map (map creation only) |

### Fog Effects Tuning

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0x09b00b2b | Float32 | fixed | 1 | 30000.0 | Particle Life | Total lifetime of fog particle (ms) |
| 0x09b00b2c | Float32 | fixed | 1 | 0.12 | Wind Factor | Wind power coefficient (v = wind \* c) |
| 0x09b00b2d | Float32 | fixed | 1 | 0.30 | Terrain Factor | Terrain gradient coefficient (effect of hills) |
| 0x09b00b2e | Float32 | fixed | 1 | 13.3 | Max Particle Rate | Max fog creation rate (particles/sec) |
| 0x09b00b2f | Float32 | fixed | 1 | 57.0 | Particle FOV | Angular window centered around anti-wind direction in which fog appears (degrees) |
| 0x09b00b30 | Float32 | fixed | 1 | 50.0 | Float Altitude | Floating distance of fog above terrain |
| 0x09b00b31 | Float32 | fixed | 1 | 128.0 | Max Opacity | Maximum alpha value for particles (0-255) |
| 0x09b00b32 | Float32 | fixed | 1 | 5000.0 | Fade-in Time | Initial portion of particle life for fade-in (ms) |
| 0x09b00b33 | Float32 | fixed | 1 | 5000.0 | Fade-out Time | Terminal portion of particle life for fade-out (ms) |
| 0x09b00b34 | Uint32 | fixed | 1 | 200 | Particle Count | Maximum number of fog particles |
| 0x09b00b35 | Float32 | variable | 2 | 0.0,1.0 | Fog Rate by Hour | Fraction (0-1) of maximum particle rate by hour of the clock |

### Cloud Effects Tuning

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0x66fbf7a9 | Float32 | fixed | 1 | 500.0 | MtnCloudsHeight | Height that clouds float at |
| 0x66fbf7aa | Float32 | fixed | 1 | 200.0 | MtnCloudsFormHeight | Lowest terrain height that clouds form over |
| 0x66fbf7ab | Float32 | fixed | 1 | 250.0 | MtnCloudsFadeInHeight | Lowest terrain height that clouds have max opacity |
| 0x66fbf7ac | Float32 | fixed | 1 | 425.0 | MtnCloudsFadeOutHeight | Terrain height above which clouds begin to fade |
| 0x66fbf7ad | Float32 | fixed | 1 | 450.0 | MtnCloudsDisperseHeight | Terrain height above which clouds fade completely |
| 0x66fbf7ae | Float32 | fixed | 1 | 425.0 | MtnCloudsSlowDownHeight | Terrain height above which clouds begin to slow |
| 0x66fbf7af | Float32 | fixed | 1 | 445.0 | MtnCloudsStopHeight | Terrain height above which clouds stop completely |
| 0x66fbf7b0 | Float32 | fixed | 2 | 80.0,200.0 | MtnCloudsSizeRange | Min and Max of cloud size variation (meters) |
| 0x66fbf7b1 | Float32 | fixed | 2 | 0.8,1.0 | MtnCloudsAspectRange | Min and Max of cloud aspect ratio variation (0-1) |
| 0x66fbf7b2 | Float32 | fixed | 2 | 0.7,0.9 | MtnCloudsOpacityRange | Min and Max of cloud opacity variation (0-1) |
| 0x66fbf7b3 | Float32 | fixed | 2 | 0.9,1.0 | MtnCloudsIntensityRange | Min and Max of cloud intensity variation (0-1) |
| 0x66fbf7b4 | Float32 | fixed | 2 | 0.015,0.025 | MtnCloudsSpeedRange | Min and Max of cloud speed variation (meters/msec) |
| 0x66fbf7b5 | Float32 | fixed | 2 | 0.8,1.2 | MtnCloudsShadeOffsetRange | Min and Max scale factors for ShadeOffsetDir |
| 0x66fbf7b6 | Float32 | fixed | 2 | 300.0,650.0 | MtnCloudsCursorHideRange | Min and Max radii in world units where clouds are hidden by cursor. |
| 0x66fbf7b8 | Float32 | fixed | 1 | 0.35 | MtnCloudsShadeIntensity | Brightness of shadow quad as % of highlight (0-1) |
| 0x66fbf7ba | Float32 | fixed | 4 | 1,1,1,1 | MtnCloudsSimSpeedFactor | Multiplier for cloud speed based on sim speed. Slow Med Fast Paused |
| 0x66fbf7bb | Float32 | fixed | 2 | 0.25,-0.125 | MtnCloudsShadeOffsetDir | X and Y(Z) offset of shade quad as a ratio of particle size (0-1) |
| 0x66fbf7bc | Uint32 | fixed | 1 | 1 | MtnCloudsMaxParticles | Max \# of cloud particles that can exist at once |
| 0x66fbf7bd | Float32 | fixed | 1 | 1500.0 | MtnCloudsMinFadeInTime | Min time for particles to fade in when they spawn visible, or to fade out when they die due to age. (Milliseconds) |
| 0x66fbf7be | Float32 | fixed | 1 | 45000.0 | MtnCloudsParticleMaxAge | Max particle lifetime (Milliseconds) |
| 0x66fbf7bf | Float32 | fixed | 1 | 45000.0 | MtnCloudsParticleGenRate | Particle spawning rate (Particles per second) |
| 0x66fbf7c0 | Bool | fixed | 1 | true | MtnCloudsAllowHiddenParticles | If true, particles are still simulated outside of regions where clouds are visible. |
| 0x66fbf7c1 | Float32 | fixed | 5 | 1,1,1,1,1 | MtnCloudsZoomFade | Percent of normal opacity by zoom level. Set to 0 to disable a particular zoom. Top is zoom 1 bottom is zoom 5. |

## Neighbor Deal Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xca46931f | Float32 | NDa_MinTermToSustainSellDealCost (months) | Min term required for the neighbor to be able to sustain sell deal cost |
| 0xea46932c | Float32 | NDb_MinDealAmountPower | Min deal amount for power deal |
| 0xea46934f | Float32 | NDd_MaxDealTerm (years) | Max term a deal can be had before renewal. |
| 0x6a469337 | Float32 | NDb_MinDealAmountWater | Min deal amount for water deal |
| 0x6a469342 | Float32 | NDc_MinDealProfitFactor | Min deal profit factor (1 + NDc_MinDealProfitFactor) |
| 0x8a46933d | Float32 | NDb_MinDealAmountGarbage | Min deal amount for garbage deal |
| 0xca469346 | Float32 | NDc_MaxDealProfitFactor | Max deal profit factor (1 + NDc_MinDealProfitFactor) |
| 0xaa46934b | Float32 | NDd_MinDealTerm (years) | Min term a deal can be had before renewal. |
| 0x0a469353 | Float32 | NDe_ProfitResponseCurve | Maps supply-over-demand to profit factor |
| 0xea4ad2ff | Float32 | NDa_MaxOverDemandFactorForBuyer | buyer_demand \* NDa_MaxOverDemandFactorForBuyer is the maximum amount the buyer can buy. |
| 0xea4ae9ef | Float32 | NDa_MinBudgetForBuyDeals | Budget level below which new buy deals become prohibited. |
| 0x6b588fad | Float32 | NDd_SuspensionPeriod | Defaulted deals get suspended for this number of days. |
| 0x8b58c59e | Float32 | NDd_UnsuspensionPeriod | If after suspension period the deal's at default during this number of days it will get killed without being re-suspended. |
| 0x4b61ffc9 | Float32 | NDe_MaxUnitCostForGarbageDealsRCurve | Maps true simulation cost to synthetic cost value used by garbage deals. |

## Background Loader Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x0b579c21 | Uint32 | MicroSecsPerTimeSlice | uSecs of active time for background thread |
| 0x0b579c22 | Uint32 | SleepMicroSecsAfterTimeSlice | uSecs of sleep time for background thread |
| 0x0b579c23 | Uint32 | ProcessCellsMaxTimeSliceMicroSecs | uSec budget for processing cells in main thread |
| 0x0b579c24 | Float32 | mOperationQuantaForOccupiedCell |  |
| 0x0b579c25 | Float32 | mOperationQuantaForEmptyCell |  |
| 0x0b579c26 | Float32 | mOperationQuantaBeforeTimerCall |  |
| 0x0b579c27 | Bool | DisableBackgroundLoader | If true, background loader is disabled |
| 0x0b579c28 | Uint32 | MinLoadRadius | Mininum extra radius to load (by zoom level) |
| 0x0b579c29 | Float32 | ExtraLoadRadiusPerMeg | Extra radius to load per free meg (by zoom level) |

## Flora Tuning

### Flora Occupant

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x083dc35b | Float32 | kSC4FloraParametersProperty | kSC4FloraParametersProperty |
| 0x083dc487 | Float32 | kSC4FloraPreferencesProperty | kSC4FloraPreferencesProperty |
| 0x083de16f | Uint32 | kSC4FloraCursorProperty | kSC4FloraCursorProperty |
| 0xa8f149c5 | Uint32 | kSC4FloraFamilyProperty | kSC4FloraFamilyProperty |
| 0x2a0348ba | Uint32 | Flora: Cluster type | Flora type that results when combining this type and one of equal or lesser value. |
| 0x2a0348bb | Float32 | Flora: Cluster max radius | Maximum plane distance for this flora to cluster with others. |
| 0x2a0348bc | Float32 | Flora: Cluster max height | Maximum altitude differential for this flora to cluster with others. |
| 0xea346888 | Bool | kPropertyID_WaterFlora | If this property is present, then the given flora is a water flora and its elevation preference table entries are interpreted as depth below sea level instead of altitude above sea level |
| 0x6a37ebb6 | Bool | Flora: Wild | Controls whether the flora appears in landscape mode (wild) or mayor mode (domestic). |

### Other

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8761abd0 | Uint32 | mnMonthsBetweenCellCoverage | mnMonthsBetweenCellCoverage |
| 0x085489c7 | Uint32 | mnRandomSeedingCellsPerMonth | mnRandomSeedingCellsPerMonth |
| 0xc9dbdd00 | Float32 | Flora: burnt sweep interval | Days between sweeps for burnt stumps (may be fractional) |
| 0xc9dbdd01 | Float32 | Flora: burnt sweep size | Maximum number of burnt stumps removed per sweep (may be fractional) |
| 0xc9dbdd02 | Float32 | Flora: elevation scale range | Meters from sea level over which to distribute the 16 elevation rows |

## Lot Configuration

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a4a88f0 | UInt8 | LotConfigPropertyRoadRequirement | The road corner requirements of the lot. Values: 0C = right corner, 09 = left corner, 08 = normal |
| 0x88edc789 | Uint8 | LotConfigPropertyVersion | Lot Config Property Version |
| 0x88edc790 | Uint8 | LotConfigPropertySize | LotConfigPropertySize |
| 0x88edc791 | Uint32 | LotConfigPropertyFamily | LotConfigPropertyFamily |
| 0x88edc792 | Float32 | LotConfigPropertyMaxSlopeBeforeLotFoundation | The slope at which it switches to using a Lot foundation |
| 0x88edc793 | Uint8 | LotConfigPropertyZoneTypes | 0x00=None, 0x01=Low Density R, 0x02=Medium Density R, 0x03=High Density R, 0x04=Low Density C, 0x05=Medium Density C, 0x06=High Density C, 0x07=Agriculture/Farming, 0x08=Medium Density I, 0x09=High Density I, 0x0A=Military, 0x0B=Airport, 0x0C=Seaport, 0x0D=Spaceport, 0x0E=Landmark, 0x0F=Civic/Plopped |
| 0x88edc794 | Uint8 | LotConfigPropertyZoneDensityTypes | LotConfigPropertyZoneDensityTypes |
| 0x88edc795 | Uint8 | LotConfigPropertyWealthTypes | 0x00=None, 0x01=Low, 0x02=Medium, 0x03=High |
| 0x88edc796 | Uint8 | LotConfigPropertyPurposeTypes | 0x00=None, 0x01=Residential, 0x02=Commercial Service, 0x03=Commerical Office, 0x05=Agriculture/Farming, 0x06=Dirty Industry, 0x07=Manufacturing, 0x08=High Tech |
| 0x88edc797 | Uint32 | LotConfigPropertyFenceDefinition | LotConfigPropertyFenceDefinition |
| 0x88edc798 | Uint32 | LotConfigPropertyRetainingWallTypes | LotConfigPropertyRetainingWallTypes |
| 0x88edc900 | Uint32 | [LotConfigPropertyLotObject](/lotconfigpropertylotobject) | LotConfigPropertyLotObject |
| 0x88EDCDFF | Uint32 | LotConfigPropertyLotObject | LotConfigPropertyLotObject |
| 0x89136440 | Uint8 | LotConfigPropertyWaterCompatibility | LotConfigPropertyWaterCompatibility |
| 0xe99b068c | Float32 | LotConfigPropertyMaxSlopeAllowed | The Max slope this lot will develop on |
| 0xe99b068d | Uint8 | LotConfigPropertyDoConstruction | If non-zero, buildings on the lot will construct, otherwise they will be fully constructed when plopped. |
| 0x699b08a4 | Float32 | LotConfigPropertyMinSlopeAllowed | The Min slope this lot will develop on |
| 0x27812837 | Uint8 | [Growth Stage](/growth-stage) | Similar to density, but with more granularity. The smallest (1) is the first to appear. |

## Advice Properties

| Property No. | Type   | Name                 | Description                     |
|--------------|--------|----------------------|---------------------------------|
| 0xc918a80e   | String | Advice Title Text    | An advice title text            |
| 0x8918aa96   | String | Advice Body Text     | An advice body text             |
| 0xe918aba5   | String | Advice Ticker Text   | An advice ticker text           |
| 0xa918ac75   | Bool   | Is ticker clickable? | Is the ticker line a hyper-link |

## Props

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xe82b68eb | Uint32 | PropType | If assigned to an occupant, this property denotes it as a prop. Must use a valid prop ID as a property value. See SC4PropOccupant.h |
| 0x49a1e05a | Uint32 | Requester Satisfaction | What prop requester this prop satisfies. |
| 0xe9a316eb | Uint8 | Prop Wealth | What wealth level this prop will appear at |
| 0x49c9c93c | Uint8 | Nighttime State Change | How this prop reacts to night |
| 0xc98204b8 | String | Visual effect name | If present, indicates an effect by string name. If not present, then 'kExemplarPropertyID_ExemplarName' is used. |
| 0xa977a86b | Uint32 | Prop occupant class ID | Uint32: The class ID of the prop occupant to create. If not present, then 'kGZCLSID_cSC4PropOccupant' is used. |
| 0x09f00e59 | Bool | Ignore lot state effects | If set to true, specifies that the prop should ignore lot state effects (distressed, abandoned, etc.). |
| 0xe9f0fa86 | Bool | Self-illuminated | If set to true, specifies that the prop should be treated as self-lit" |
| 0x4a149631 | Float32 | Prop Time of Day | Range of hours on 24-hour clock (0-23) when prop will be at state 0 (visible). If start and end times are both 0, always visible. |
| 0x6a3fcc37 | Uint32 | Global Effect Trigger | Trigger ID for script-defined global effect that turns this prop on (state 0) and off (state 1). |
| 0x6a5e0727 | Uint8 | Active Lot State | What lot state this prop is active in. Don't add the property if the prop is active in all lot states. |
| 0x8a5e5db8 | Bool | Is Ground Model | Present if this prop is a ground-based model suitable for demolish fx, shadows, and collision avoidance |
| 0x4a70d491 | Bool | States as Frames | Add this property only if prop states are visually depicted by different frames in an animated model instance |
| 0xca7515cc | Uint8 | Simulator Date Start | Simulator MONTH (1-12) and DAY (1-31) to start this prop's date interval |
| 0x0a751675 | Uint32 | Simulator Date Interval | How often this prop becomes active, in days. |
| 0x4a751ad5 | Uint8 | Prop Random Chance | Random chance (0-100) of this prop appearing according to time-of-day and simulator date |
| 0x4a764564 | Uint32 | Simulator Date Duration | How long in simulator days the prop will stay active once triggered |
| 0x2a89b677 | Bool | Prop Destroys Lot | Whether or not prop destroys entire lot when it burns down. Default is true for flammable props. |
| 0x4a89fcf3 | Bool | Previewable | If set to true, the prop will appear in the building plop preview" |
| 0x6a95e503 | Bool | Query as main building | If set to true, when the prop is hover queried it will highlight both itself and the main building (and give the same hover data) |
| 0x6a959e71 | Bool | Requires Power to Appear | Prop only appears if lot is powered |
| 0x69f14d33 | Bool | Orient To Slope | Prop rotates x/z to match slope |
| 0x4a9f188b | Bool | Light | Set if prop has a light mask and should light up at night with the lot building. |
| 0x6a9edd07 | Uint8 | Animated Prop Play Mode | Whether animated props should be looped, ping-pong, or one-shot. If not present, the default is Loop. |
| 0x8aa864d5 | Uint32 | Crime Incident ID | Which crime simulator incident this prop represents, or 0 if it's a generic crime prop. |
| 0xabb90e58 | Uint8 | Helipad Type | Indicate what kind of helicopter should appear on this helipad |
| 0x0bfa15a5 | Uint8 | Airplane Hanger Type | Indicate what kind of airplane should appear at this point |
| 0x8bfb1072 | Uint8 | Runway End Number | Indicate the location of the end of a runway. Must come in pairs. |
| 0x699b327e | Float32 | GarbageFilterResponse | (Deprecated) Response for GarbageFilter |
| 0xe999cc32 | Float32 | WealthFilterResponse | (Deprecated) Response for WealthFilter |
| 0xe99af514 | Float32 | CrimeFilterResponse | (Deprecated) Response for CrimeFilter |
| 0xc82b6cb7 | Float32 | PropPlacement | (Obs) Intended to control Z/R-dependent prop placement. Not implemented yet. |
| 0x6a91b499 | Bool | Removable Stoplight Prop | (Obs) This is an intersection stoplight prop that can be removed by the engine if necessary. |

## Occupant

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x29244db5 | Uint8 | Flammability | Flammability rating of this occupant |
| 0x49beda31 | Uint8 | MaxFireStage | (0-5) highest fire stage this occupant can reach |
| 0xe9d117c3 | Bool | Special case only | If set, occupant is never chosen based on user action or normal simulation. |
| 0x8a1c3e72 | Sint64 | Worth | If e.g., the occupant gets destroyed by a disaster, this is the reported damage amount |
| 0xea5393ed | Bool | Requires power to animate | Set this to true if the occupant requires power to animate |
| 0x8a5f88e3 | Uint32 | MinForPurposeFundingPercentageToAnimate | (Purpose Id, funding)The occupant needs to be funded by at least this much for the specified purpose, for it to animate |

## User Interface (UI) Properties

### Catalog View

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x899afbad | String | Item Name | The item name that will be visible to the player |
| 0x8a2602a9 | String | Item Description | Human-readable description of this item |
| 0x8a2602b8 | Uint32 | Item Icon | Resource instance ID of Menu Icon for this item |
| 0x8a2602b9 | Uint32 | Item Order | Controls position in menu |
| 0x8a2602ba | Uint32 | Item Submenu | If needed: which sub menu this item belongs to |
| 0x8a2602bb | Uint32 | [Item Button ID](/item-button-id) | If needed: the button ID this item corresponds to |
| 0x6ad54804 | Sint32 | Catalog Monthly Cost | Value for displaying monthly cost in the catalog - not simulated |
| 0x8a94eee0 | Float32 | Catalog Monthly Cost | Float value for displaying monthly cost in the catalog - not simulated |
| 0x4aa60ebc | Uint32 | Catalog Capacity | Value for displaying capacity in the catalog - not simulated |
| 0xca416ab5 | Uint32 | Item Description Key | Resource key of the string resource of the description |

### UI Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xe90f5de4 | Uint32 | IntelliScrollInnerRadiusPixels | When right-click scrolling, this is the number of pixels away from the anchor that the user must move before scrolling begins. |
| 0xa90f5dec | Uint32 | IntelliScrollOuterRadiusPixels | When right-click scrolling, this is the number of pixels away from the anchor at which the scrolling speed maxes out. |
| 0x4975dd20 | Float32 | ScrollingDeceleration | Amount to decelerate scrolling speed per GZPaint tick. Use with ScrollingDecelerationIsPercentage. |
| 0x4975dd25 | Bool | ScrollingDecelerationIsPercentage | True if ScrollingDeceleration should be the percentage (0.0-1.0) to decelerate per GZPaint tick. False if that amount should be the absolute amount to decrement the speed per tick. |
| 0x49e5522f | Float32 | AutoScrollSpeed | Speed of scrolling when cursor hits screen edge. |
| 0xa9e581fb | Float32 | KeyboardScrollSpeed | Speed of scrolling when arrow key is held down. |

### Region UI Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xca383ca2 | Float32 | ScrollingDeceleration | Percent amount to decelerate scrolling speed per GZPaint tick. |
| 0xca383ca3 | Uint32 | IntelliScrollOuterRadiusPixels | When right-click scrolling, this is the number of pixels away from the anchor at which the scrolling speed maxes out. |
| 0xca383ca4 | Uint32 | IntelliScrollInnerRadiusPixels | When right-click scrolling, this is the number of pixels away from the anchor that the user must move before scrolling begins. |
| 0xca383ca5 | Uint32 | HullHorizontal | Horizontal scroll hull edge in pixels. |
| 0xca383ca6 | Uint32 | HullVertical | Vertical scroll hull edge in pixels. |
| 0xca383ca7 | Float32 | ScrollGradient | \# of pixels per speed increase (higher is slower). |
| 0xca383ca8 | Uint32 | WaterErosionIterations | Auto gen region: water erosion steps. |
| 0xca383ca9 | Uint32 | FlowStepsForWaterErosion | Auto gen region: water erosion flow steps. |
| 0xca383caa | Uint32 | SmoothingStepsForWindErosion | Auto gen region: wind erosion steps. |
| 0xca383cab | Uint32 | RegionUI: Grid color | Color of regional grid, in 0xRRGGBB form. |
| 0xca383cac | Uint32 | RegionUI: Highlight | Color of regional highlight, in 0xRRGGBB form. |
| 0xca383cad | Uint8 | RegionUI: Plains map level | Height map fill value for new cities in plains regions (0-255). |
| 0xca383cae | Uint8 | RegionUI: Water map level | Height map fill value for new cities in water regions (0-255). |
| 0xca383cb1 | Uint8 | RegionUI: Cloud opacity range | Range of opacity values for clouds (min,max; 0-255). |

### Regional Transport Map

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xab9ec143 | Uint32 | DV/RegionalTransport: Color table | Color table for regional transport map: street, rail, road, 1way road, avenue, monorail, elrail, highway, elhighway, airport, seaport, park, rail station, default zone. |

### MiniMap

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xea3573af | Uint32 | MiniMap: Terrain ramp | Color progression to use for terrain. |
| 0x6b733233 | Uint32 | MiniMap: Water ramp | Color progression to use for water. |

## Buildings

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xaa230baf | Uint8 | Industrial Building Type | Which type of Industrial (Anchor/Out/Mech) |
| 0x499afa38 | Uint8 | Construction Time | Construction time in Sim-days |
| 0x099afacd | Sint64 | Bulldoze Cost | Bulldoze cost to delete the building, in Simoleans |
| 0x49cac341 | Sint64 | Plop Cost | Cost to plop this building, in Simoleans |
| 0x27812810 | Float32 | Occupant Size | In meters: Width Height Depth |
| 0x27812832 | Uint8 | Wealth | Wealth represented by the building |
| 0x27812833 | Uint8 | Purpose | Function of building |
| 0x27812834 | Uint32 | Capacity Satisfied | Paired values-developer ID, and how much capacity this building offers to that developer |
| 0x27812836 | Bool | Allow Joint Occupancy | If true, different types can occupy the building simultaneously |
| 0x2781283f | Bool | Monopoly Piece | If true, this building is for debug and tuning use only |
| 0x27812840 | Uint32 | Demand Satisfied | Paired values-demand ID, and how much plopping this building supplies the resource |
| 0x27812841 | Uint32 | Demand Created | Paired values-demand ID, and how much plopping this building increases the demand for the resource |
| 0x27812842 | Float32 | Demand Satisfied | IDs from Demand Satisfied are associated to these values instead of the Uint32 values |
| 0x27812843 | Float32 | Demand Created | IDs from Demand Created are associated to these values instead of the Uint32 values |
| 0x27812844 | Bool | Demand Is Variable | If true, the demand simulator ignores demand created and demand satisfied until instructed |
| 0x2781284f | Sint32 | Landmark Effect | magnitude, radius in cells |
| 0x27812850 | Sint32 | Park Effect | magnitude, radius in cells |
| 0x27812851 | Sint32 | Pollution at center | Pollution generated: air, water, garbage, radiation (at center of the area of effect) |
| 0x0abfc024 | Uint32 | AppearanceZoomsFlag | Flag specifying the zooms in which the model should appear |
| 0xca5b9305 | Sint32 | Mayor Rating Effect | Mayor rating effect: magnitude, radius in cells |
| 0xca5b9306 | Uint8 | Crime Effect | Crime effect: magnitude, radius in cells. Doesn't increase overall crime, but can negate effects of police stations |
| 0xaa5832f3 | Sint32 | Pollution at outer edge of circle | Pollution generated: air, water, garbage, radiation (at outer radius of area of effect) |
| 0x68ee9764 | Float32 | Pollution radii | Radii in cells for pollution generated: air, water, garbage, radiation |
| 0x27812852 | Uint32 | Power Generated | Amount of power generated |
| 0x27812853 | Uint32 | Power Plant Type | Type of power plant |
| 0x27812854 | Uint32 | Power Consumed | Amount of power consumed |
| 0x6a43150f | Uint32 | Hard Failure Type | Explosion type at end of life |
| 0x09132de8 | Sint64 | Power pole monthly upkeep | Cost of maintaining this power pole |
| 0xa9132ef9 | Float32 | Power line monthly upkeep | Cost of maintaining each cell of wire connected to this power pole |
| 0xc8ebd131 | Uint32 | Water Treatment monthly capacity | Amount of water treated per month |
| 0xa8ebcf0c | Uint32 | Incinerator monthly capacity | Amount of trash burned per month |
| 0x48ebd0b1 | Uint32 | Waste to energy monthly Capacity | Amount of trash converted to energy per month |
| 0x88ed1059 | Uint32 | Recycling center percent reduction | Percentage by which recycling center reduces trash |
| 0x68ed1736 | Uint32 | Recycling center population served | Number of people that can be served by this recycling center |
| 0xc8ed2d84 | Uint32 | Water Consumed | Amount of water consumed |
| 0x88ed3303 | Uint32 | Water Produced | Amount of water produced |
| 0x48ee7a44 | Uint32 | Garbage Capacity | Amount of garbage the building can store in a month |
| 0x48f23a7e | Uint8 | Water Source | Where this water producer gets its water |
| 0x27812870 | Uint32 | Building/prop Family | The family that this building or prop is a member of |
| 0xe90e25a1 | Uint8 | Transit Switch Point | Paired entries indicating this building allows a travelling Sim to switch between transit types |
| 0xe90e25a2 | Float32 | Transit Switch Entry Cost | Step cost to enter this transit switch |
| 0xe90e25a3 | Float32 | Transit Switch Traffic Capacity | Amount of traffic the switch can handle without increasing travel time |
| 0x0bfc0a4c | Float32 | Transit Switch Fare | Simoleon charge per traveller to enter the switch |
| 0x4bfc47b0 | Bool | Transit Switch Capacity Effect | If true, this building radiates capacity reduction like intersections |
| 0xe91a0b5f | Sint64 | Building value | Base value in Simoleons of this building |
| 0xc910b4ce | Float32 | Power plant energy conversion cost | Cost to produce one unit of electricity, not including infrastructure maintenance |
| 0xea1cf220 | Float32 | Age degradation rate | How fast this plant degrades over time |
| 0xea1cf221 | Float32 | Soft failure threshold | Threshold at which soft failure occurs |
| 0xea1cf222 | Float32 | Hard failure threshold | Threshold at which hard failure occurs |
| 0x0911e2e7 | Float32 | Age to maintenance cost multiplier response curve | Converts the current age degradation of the plant to a multiplier for maintenance cost |
| 0x8a1e07ee | Float32 | Age to output level response curve | Converts the current age degradation of the plant to a multiplier for production level |
| 0xea1e3c53 | Float32 | Water building pumping cost | Cost to produce one unit of water, not including infrastructure maintenance |
| 0xea260589 | Uint32 | Lot Resource Key | For ploppable buildings: Resource instance ID of lot exemplar for this building |
| 0x6a19f6b5 | Float32 | Health effect radius | Radius of generic health effect of this building |
| 0xaa19f6ea | Float32 | Health effect strength | Strength of generic health effect of this building (positive or negative) |
| 0xea2e078b | Uint32 | City Exclusion Group | For ploppable buildings: No more than one building within the specified group can be built in a single city. |
| 0xea2e078c | Uint32 | Regional Exclusion Group | For ploppable buildings: No more than one building within the specified group can be built in a single region. |
| 0xea3209f8 | Bool | Conditional Building | If true, building will appear ghosted in the menu until triggered by a script condition |
| 0xaa5c04c5 | Float32 | Radiation Spew Intensity | Intensity of radiation spew when power plant blows up |
| 0xaa5c04c8 | Float32 | Radiation Spew Radius | Radius of radiation spew when power plant blows up, in meters |
| 0x091b42a2 | Float32 | Hospital Coverage Radius | Radius of this hospital's coverage, in meters |
| 0x69220415 | Uint32 | Hospital Patient Capacity | Maximum number of patients served by this hospital |
| 0x2921a9cc | Float32 | Hospital Population vs. Distance | Maps distance from hospital to a % of population covered |
| 0xc9299659 | Float32 | Hospital HQ boost | Inherent HQ boost of this hospital |
| 0xa92ae3bd | Float32 | Hospital Effectiveness vs. Average Age | Maps Average age of a tract to the % HQ boost the hospital gives the tract |
| 0xa92d9fcd | Float32 | Hosptial Effectiveness vs. Wealth | Maps wealth level to HQ boost % |
| 0x292d8f9b | Uint32 | Hospital Type ID List | Variable length list of type IDs for this hospital |
| 0x691b42b3 | Float32 | School Coverage Radius | Radius of a school's coverage, in meters |
| 0x8922041b | Uint32 | School Student Capacity | Maximum number of students served by this school |
| 0xe921a936 | Float32 | School Population vs. Distance | Maps distance from school to a % of population covered |
| 0xa92ae446 | Float32 | School EQ boost | The EQ boost the school gives at it's origin |
| 0xc9299662 | Float32 | School Effectiveness vs. Average Age | Maps Average age of a tract to the % EQ boost the school gives the tract |
| 0xc92d7ec0 | Float32 | School Effectiveness vs. Wealth | Maps wealth level to EQ boost % |
| 0xa92d8e40 | Uint32 | School Type ID List | Variable length list of type IDs for this school |
| 0x0bd86fd3 | Uint8 | Ferry Terminal Type | Type of ferry terminal |
| 0x88fcd877 | Uint32 | Building foundation | Foundation type ID for this building or lot. Absent for none. |
| 0xe83a081d | Bool | kSC4BuildingModelRotationProperty | If property is present (regardless of value), then the model can be rotated and contains 'full geometry'. |
| 0xe9822d62 | Bool | kSC4BuildingNoModelProperty | If present, then there are no building-style models for this building and if there are any, they should be ignored. |
| 0xea123cef | Uint32 | kSC4BuildingModelClassProperty | If present, specifies a GZCLSID (class id) for the model class to use. Otherwise, just use the default kGZCLSID_cS3DModelInstance. |
| 0xea3209f9 | Bool | No Shadows | If true, building will not draw shadows |
| 0xe9aee3da | Uint32 | Response vehicle type | Group(s) of vehicle automata that will be created when this building is constructed or plopped. |
| 0xe9aee3db | Uint8 | Response vehicle count | How many of each type (in Response Vehicle Type property) will be created when building is constructed or plopped. |
| 0xe9aee3dc | Uint32 | Response pedestrian type | Group(s) of pedestrian automata that will be created when this building is constructed or plopped. |
| 0xe9aee3dd | Uint8 | Response pedestrian count | How many of each type (in Response Pedestrian Type property) will be created when building is constructed or plopped. |
| 0x29b55f73 | Uint32 | Field Lots | A list of IDs of 1x1 lots that describe a field tile associated with this building (will choose 1 randomly) |
| 0x8a0b4103 | Uint32 | Freight Receiving Capacity | Freight traffic that can arrive at this building |
| 0xc9b93a5 | Uint32 | SFX:Default Plop Sound | GUID of sound played when building is plopped |
| 0xca19d7ca | Uint32 | SFX:Ambience Good Sound | GUID of sound played when building is around and in good working order |
| 0x0a4c13cb | Uint32 | SFX:Ambience Decayed Sound | GUID of sound played when building is around and damaged or decayed |
| 0x4a4c132e | Uint32 | SFX:Activate Sound | GUID of sound played when building goes online |
| 0x0a36afa2 | Uint32 | SFX:AlarmSoundId | GUID of sound played when alarm goes off |
| 0x6a36afab | Float32 | SFX:AlarmTime | 24hour times i.e. 15.5 |
| 0x6a36afac | Uint32 | SFX:Occupant Instance Sound | GUID of sound played for the occupant. There will be one instance per occupant. |
| 0x2a53be13 | Uint32 | SFX:Alarm Ambience Sound | GUID of sound. Plays between alarm times. |
| 0xaa1dd397 | Uint32 | SFX:Query Sound | GUID of the sound to play when the occupant is clicked on with query tool |
| 0x0a902434 | Uint32 | SFX:Query Sound Abandoned | GUID of the sound to play when the occupant is clicked on with query tool and is abandoned. |
| 0xaa905ab9 | Uint32 | SFX:Query Sound decayed | GUID of the sound to play when the occupant is clicked on with query tool and is decayed. |
| 0xaa87817a | Uint32 | SFX:Intersection Sound | GUID of the sound to play when the occupant approaches an intersection |
| 0x0a93036f | Uint32 | SFX:Demolition Sound | GUID of the sound to play when an occupant is demolished |
| 0x6c044bb5 | Uint32 | SFX:ActiveSound | GUID array of sounds to play (per zoom) when occupant is 'active' |
| 0xea54d283 | Uint32 | Budget Item: Department | GUID(s) of department ID for this budget item |
| 0xea54d284 | Uint32 | Budget Item: Line | GUID(s) of line item ID for this budget item |
| 0xea54d285 | Uint32 | Budget Item: Purpose | GUID(s) of purpose ID for this budget item |
| 0xea54d286 | Sint64 | Budget Item: Cost | Cost(s) in Simoleans for this budget item |
| 0x2a499f85 | Uint32 | Query exemplar GUID | GUID for this building's Query exemplar |
| 0xaa5c23fa | Uint32 | Landmark Homage Key | Resource key of string to be displayed in the landmark's query dialog |
| 0x4a5f7c4b | Uint32 | Desirability Effect IDs | Growth Developer IDs to go with next property |
| 0x4a5f7315 | Float32 | Desirability Effect Values | Radius in cells, Max effect, and min effect for each developer |
| 0xaa60e745 | Float32 | Goofy Stat Response Curve | Response curve for the Goofy Stat field in query dialogs |
| 0xaa83558f | Uint8 | Crane Hints | What kind of crane to use |
| 0x68e94a50 | Sint32 | (Obs) kSC4BuildingPropertyCrimeEffectCenterStrength | Strength of the crime in the area near the building. This number is in some imaginary units. |
| 0x68e94a51 | Sint32 | (Obs) kSC4BuildingPropertyCrimeEffectExteriorStrength | Strength of the police in the area at the radius of effect. This number is in some imaginary units. |
| 0x68e94a52 | Float32 | (Obs) kSC4BuildingPropertyCrimeEffectRadius | A measurement of the radius, in meters, of the effect of this building. |
| 0x68e94a53 | Float32 | (Obs) kSC4BuildingPropertyCrimeEffectFactor | A dynamic property which is normally 1.0, but can be roughly -2.0 to +2.0. |
| 0x2921e147 | Sint64 | (Obs) Mass Transit monthly upkeep | Cost of maintaining this building to mass transit budget |
| 0x27812830 | Uint8 | (Obs) Supported Zones | Specifies zones compatible with building |
| 0x27812831 | Uint8 | (Obs) Density | Density of population represented by the building |
| 0x27812835 | Uint32 | (Obs) Capacity (secondary) | Paired values-developer ID, and how much capacity this building offers to that developer |
| 0xc910b4cd | Sint64 | (Obs) Utility building monthly upkeep | Cost of maintaining this utility building |
| 0x2a4174aa | Sint64 | (Obs) Landmark Monthly Maintenance | Cost of maintaining this to the landmark budget |
| 0x499afb52 | String | (Obs) Style | Building Art Style (Chicago, Houston, NY, Euro) |
| 0xe918a73f | Sint64 | (Obs) Hospital Staff Budget | Cost of paying the staff for this hospital |
| 0x2921f718 | Sint64 | (Obs) Hospital Ambulance Budget | Cost of operating ambulances for this hospital |
| 0xc921c9c7 | Sint64 | (Obs) School Staff Budget | Cost of paying the staff for this school |
| 0xa921c9d3 | Sint64 | (Obs) School Bus Budget | Cost of operating buses for this hospital |
| 0xc7e16a90 | Bool | (Obs) kSC4BuildingFoundationDisabledProperty | If property is present (regardless of value), then no foundation is ever made for the building. |
| 0xc7e16a91 | Bool | (Obs) kSC4BuildingBuiltInFoundationProperty | If property is present (regardless of value), then the building has a built-in foundation. If so, then the kSC4BuildingBaseAltitudeProperty should usually (always?) be present. |
| 0xc7e16a92 | Float32 | (Obs) kSC4BuildingBaseAltitudeProperty | If present, then the building's coordinate origin is above the base by this many units and you'll need to calculate bounding boxes a little differently. Usually found with kSC4BuildingBuiltInFoundationProperty. |
| 0x891b42ab | Float32 | (Obs) Hospital Effectiveness vs. Distance | Maps % of coverage distance from a hospital to HQ boost % |
| 0x491b42af | Float32 | (Obs) Hospital Population vs. Average Age | Maps average age to a % of population covered |
| 0x491b42b9 | Float32 | (Obs) School Effectiveness vs. Distance | Maps % of coverage distance from a school to EQ boost % |
| 0xe91b42bd | Float32 | (Obs) School Population vs. Average Age | Maps average age to a % of population covered |
| 0x883a0724 | Bool | (Obs) kSC4BuildingNoOrientationProperty | If property is present (regardless of value), then the building cannot be oriented (e.g. to face a road). |

## Foundation

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x68fcff37 | Uint32 | kSC4FoundationPropertySideTextures | Texture IDs for each zoom level. Mutally exclusive with building model properties. |
| 0x68fcff38 | Uint32 | kSC4FoundationPropertyTopTextures | Texture IDs for each zoom level. Mutally exclusive with building model properties. |
| 0xc911eda0 | Float32 | kSC4FoundationPropertySideTextureSize | Size of a texture in meters. Defaults to standard city cell size. |
| 0xc911eda1 | Float32 | kSC4FoundationPropertyTopTextureSize | Size of a texture in meters. Defaults to standard city cell size. |
| 0x88fcc3e3 | Float32 | kSC4FoundationPropertyMaxHeight | The height a foundation can lift an occupant (usually a building or lot). |

## Lot Retaining Wall

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x295961f2 | Uint32 | kSC4RetainingWallPropertyWallTextures | Texture IDs for each zoom level. |
| 0x295961f3 | Float32 | kSC4RetainingWallPropertyWallTextureSize | Size of a texture in meters. Defaults to standard city cell size. |

## RCI

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x47bb3f10 | Sint32 | Minimum Value | Minimum active demand, use 0x80000000 for none |
| 0x47bb3f11 | Sint32 | Maximum Value | Maximum active demand, use 0x7fffffff for none |
| 0x47bb3f20 | Sint32 | Initial Supply | Initial supply of this resource, \[min, max\] |
| 0x47bb3f21 | Sint32 | Initial Demand | Initial demand for this resource, \[min, max\] |
| 0x47bb3f30 | Uint32 | Drives | Demands increased by this resource (demandID, percentage) |
| 0x47bb3f31 | Uint32 | Satisfies | Resources created by this resource (demandID, percentage) |
| 0x47bb3f32 | Uint32 | Contributes | Demands increased by this demand (demandID, percentage) |
| 0x47bb3f41 | Uint32 | Caps demand | Demand IDs capped by this resource, based on % depleted |
| 0x47bb3f50 | Uint32 | Sums | List of demand IDs summed by this one |
| 0x47bb3f60 | Uint8 | Region Use | Which part of the regional index is added to the local index |
| 0x47bb3f40 | Uint32 | Limits growth | Supply limited by this resource (demandID, percentage) |

## Growth Developer

### Landfill Developer

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a280510 | Float32 | Landfill: Garbage Decay Rate | The rate at which garbage decays in units per month |
| 0x4a280513 | Float32 | Landfill: Level Tolerance Threshold | The altitude variance of the landfill zone before levelling will take place |
| 0x4a677e5b | Uint32 | Landfill: Total Max Garbage Monthly | The max total amount of garbage units taken in by landfills monthly |
| 0x4a677e5c | Uint32 | Landfill: Monthly Max Garbage per Landfill | The max amount of garbage units taken in by each landfill monthly |
| 0x4a677e5d | Bool | Landfill: Move Landfill Tiles with Terrain | Flag indicating whether or not to move landfill tiles with terrain |
| 0x4a677e5e | Uint32 | Landfill: Monthly Max Garbage Decayed per Landfill | The max amount of garbage units to decay in each landfill monthly |
| 0x4a677e5f | Sint64 | Landfill: Default Landfill Cell Maintenance Cost | Monthly maintenance cost of a landfill cell (can be overridden by the model budget cost property) |
| 0x2aa00fe7 | Sint64 | Landfill: Cost for Altitude Change | When zoning, the additional cost per cell for each meter of altitude changed |

### Port Developer

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8a270fc3 | Uint32 | Port Type Exemplar IDs | List of instance IDs for exemplars containing the properties for each distinct airport/seaport type |
| 0xca271780 | Uint32 | Num Growth Stages | Number of growth stages (i.e. number of lots) for this particular airport type |
| 0xca271781 | Uint32 | Lot stage template IDs | List of template IDs for each growth stage |
| 0xca271782 | Float32 | (Obs) Demand Thresholds List | List of demand thresholds for each growth stage. What this value refers to is zone type specific. |
| 0xca271783 | Sint64 | Budget Requirements List | List of budget requirements for each growth stage - in Simoleans (tm) |
| 0xca271784 | Uint32 | Trip Capacity List | List of trip capacities for each growth stage for airport or seaport |
| 0xca271785 | Float32 | Efficiency Distress Threshold | Efficiency percentage under which the port lot distresses |
| 0xca271786 | Sint64 | Stage Upgrade Cost | List of costs in Simoleans (tm) associated with each growth stage |
| 0xca271787 | Uint8 | Port Size | Port Size identifier. 1=small, 2=medium, 3=large |
| 0xca271788 | Uint8 | Port Width | Width of the port lot (in North rotation) |
| 0xca271789 | Uint8 | Port Height | Height of the port lot (in North rotation) |
| 0xca271800 | Float32 | Height Map | Optional list of vertex altitude values corresponding to each cell in the lot for airport or seaport |

### Park Manager

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xca480830 | Float32 | Efficiency Distress Threshold | Efficiency value under which the lot begins to distress |
| 0x4a6676ad | Float32 | Zoo Escape Chance Curve | Input: park efficiency (0-100) Output: Chance of zoo escape each month (0-100) |

### General

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x87cd6300 | Uint8 | Target Zone | The type of zone that is developed |
| 0x87cd6301 | Uint32 | Demand Source Index | Demand comes from this index OR source zone |
| 0x87cd6310 | Uint8 | Tract Size | Power of 2; determines the size of the demand grid |
| 0x87cd6330 | Uint8 | Wealth Type | Specifies (source and target) wealth type |
| 0x87cd6332 | Uint8 | Purpose Type | Specifies type of building created by this developer |
| 0x87cd6333 | Uint8 | Land Value Range | Specifies acceptable land values (0, 0 disables) |
| 0x87cd633f | Bool | Land Value Use Intrinsic | True means use total land value |
| 0x87cd6340 | Float32 | Land Value Effect | How much land value is a factor in desirability |
| 0x87cd6341 | Float32 | Park Effect | How much park proximity affects desirability |
| 0x87cd6343 | Float32 | R\$ Proximity Effect | How much proximity to R\$ is a factor in desirability |
| 0x87cd6344 | Float32 | R\$\$ Proximity Effect | How much proximity to R\$\$ is a factor in desirability |
| 0x87cd6345 | Float32 | R\$\$\$ Proximity Effect | How much proximity to R\$\$\$ is a factor in desirability |
| 0x87cd6346 | Float32 | Traffic Effect | How much traffic volume is a factor in desirability |
| 0x87cd6347 | Float32 | Trip Length Effect | How much travel time is a factor in desirability |
| 0x87cd6348 | Float32 | School Effect | How much school grade is a factor in desirability |
| 0x87cd6349 | Float32 | Hospital Effect | How much hospital grade is a factor in desirability |
| 0x87cd634a | Float32 | Crime Effect | How much crime is a factor in desirability |
| 0x87cd634b | Float32 | Pollution Effect Air | How much air pollution proximity affects desirability |
| 0x87cd634c | Float32 | Pollution Effect Water | How much water pollution proximity affects desirability |
| 0x87cd634d | Float32 | Pollution Effect Garbage | How much garbage pollution proximity affects desirability |
| 0x87cd634e | Float32 | Pollution Effect Radiation | How much radiation pollution proximity affects desirability |
| 0x87cd6354 | Sint32 | Desirability Threshold Decline | Tracts with desirability greater than this value never abandon. |
| 0x87cd6355 | Sint32 | Desirability Threshold Growth | Tracts with desirability less than this value never develop. Tested before pruning. |
| 0x87cd6356 | Bool | Phantom Demand | If true, unhappy sims will create a demand for new growth, which results in migration |
| 0x87cd6357 | Sint32 | Baseline Desirability | Value for desirability, if no other effects are applicable |
| 0x87cd6360 | Uint8 | Stage Count | Number of growth stages |
| 0x87cd6361 | Float32 | Stage 1 vs. Size | Percentage of growth which should be of type 1, as a function of the population of the city |
| 0x87cd6362 | Float32 | Stage 2 vs. Size | Percentage of growth which should be of type 2, as a function of the population of the city |
| 0x87cd6363 | Float32 | Stage 3 vs. Size | Percentage of growth which should be of type 3, as a function of the population of the city |
| 0x87cd6364 | Float32 | Stage 4 vs. Size | Percentage of growth which should be of type 4, as a function of the population of the city |
| 0x87cd6365 | Float32 | Stage 5 vs. Size | Percentage of growth which should be of type 5, as a function of the population of the city |
| 0x87cd6366 | Float32 | Stage 6 vs. Size | Percentage of growth which should be of type 6, as a function of the population of the city |
| 0x87cd6367 | Float32 | Stage 7 vs. Size | Percentage of growth which should be of type 7, as a function of the population of the city |
| 0x87cd6368 | Float32 | Stage 8 vs. Size | Percentage of growth which should be of type 8, as a function of the population of the city |
| 0x87cd6370 | Uint8 | Water Supply Cap | Maximum density allowed without water service |
| 0x87cd6371 | Uint8 | Fire Coverage Cap | Maximum density allowed without fire protection |
| 0x87cd6372 | Uint8 | Park Cap | Maximum density allowed without a nearby park |
| 0x87cd6373 | Uint8 | Power Supply Cap | Maximum density allowed without power service |
| 0x87cd6381 | Uint8 | Use Monopoly Pieces | Specifies building selection mode |
| 0x87cd6391 | Float32 | Co\$\$ Proximity Effect | How much proximity to Co\$\$ is a factor in desirability |
| 0x87cd6392 | Float32 | Co\$\$\$ Proximity Effect | How much proximity to Co\$\$\$ is a factor in desirability |
| 0x87cd6397 | Float32 | Transient Aura Effect | How much transient aura effects (-128, 127) affect desirability |
| 0x87cd6398 | Float32 | Slope Effect | How much slope is a factor in desirability |
| 0x87cd6399 | Float32 | Landmark Effect | How much landmark proximity affects desirability |
| 0x87cd63a0 | Uint32 | Style Percentages | Pairs of occupant group IDs and percentages showing how often they should be used |
| 0x87cd6331 | Uint8 | (Obs) Density Type | Specifies density |
| 0x87cd6342 | Float32 | (Obs) Pollution Effect | How much (air, water, garbage, radiation) pollution proximity affects desirability |
| 0x87cd6380 | Float32 | (Obs) Abandonment Thresholds | Min occupancy rate \[0,1\]: low, medium, high density |

## Simulators

### Main Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x89590e6d | Uint32 | Simulator Speeds | Milliseconds per day for slow, medium, fast |
| 0x897e709f | Float32 | 24 Hour Clock speed (time magnification) | Specifies a multiplier from real time to the 24 hour clock's time. |
| 0x09b73421 | Uint32 | k24HourClockNightBeginProperty | Specifies the time (0-23) that night time graphically begins. |
| 0x09b73422 | Uint32 | k24HourClockNightEndProperty | Specifies the time (0-23) that night time graphically ends. |
| 0x89590e6e | Float32 | kAnimationTimeDilationProperty | Time dilation factor to apply to animations based on sim speed (paused,slow,med,fast,emergency/drive) |

### Land Value Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x47e2c300 | Uint8 | Land Value Intrinsic Min/Max | Minimum \> 0, Maximum |
| 0x47e2c301 | Uint8 | Land Value Wealth Boundaries | Low/Medium boundary, Medium/High boundary |
| 0x47e2c310 | Uint8 | Land Value Water Effect | Effect of water on land value: size, radius |
| 0x47e2c320 | Float32 | Land Value Altitude Effect | Maps altitude to land value |
| 0x47e2c330 | Uint32 | Land Value Desirability IDs | Growth Developer IDs (see Effects) |
| 0x47e2c331 | Float32 | Land Value Desirability Factors | Size of effects (see IDs) |
| 0x47e2c332 | Float32 | Land Value Desirability Curve | Maps desirability to land value |

### Building Development Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x47e2c380 | Uint32 | Construction Resources Min/Max | Amount of capacity that can be under construction at any one time |
| 0x47e2c381 | Float32 | Construction Resources per Resident | Factor applied to population to calculate construction resources |
| 0x47e2c382 | Uint32 | Construction Type Selection Bias | Improves that chance that low-demand types will have opportunity to build |
| 0x47e2c383 | Float32 | Stage Popluation Multiplier | Values \> 1 allow big stage buildings sooner. Indexed by difficulty level |
| 0x47e2c400 | Uint32 | Lot Developer Stay New Time | Number of days before a building can distress |
| 0x47e2c401 | Float32 | Lot Developer Occupancy Thresholds | When to abandon, distress, and renew. Values 0-1 |
| 0x47e2c500 | Float32 | Tract Developer Overbuild | Factor applied to desired capacity when growing buildings in a tract |
| 0x47e2c501 | Float32 | Tract Developer Reoccupy Thresholds | Start and Stop percentage of desired capacity that can be fulfilled by abandoned buildings |
| 0x47e2c502 | Float32 | Tract Developer Redevelop Size Threshold | What percentage of the existing capacity must be demanded before we redevelop |
| 0x47e2c510 | Float32 | Tract Developer Demolition Costs | For occupied/abandoned buildings" |
| 0x47e2c511 | Float32 | Tract Developer New Lot Costs | Fictional cost to aggregate a lot/subdivide a lot |
| 0x47e2c530 | Float32 | Tract Developer Occupancy Variation | Building occupancy rate +/- variation from tract rate |
| 0x47e2c531 | Float32 | Tract Developer Min Vacancy Range | When 100% full, subtract a little from the occupancy rate |
| 0x47e2c540 | Bool | Tract Developer Kick Out Lower Wealth | If true, higher wealth buildings can replace non-empty lower wealth buildings |
| 0x47e2c550 | Uint32 | Tract Developer Available Styles | List of available (R and C) building styles |
| 0x47e2c551 | Sint32 | Tract Developer Years Between Styles | How often to change (R and C) building styles |
| 0xe900ea24 | Float32 | kMaxCellAltitudeDeltaForFlatnessProperty | kMaxCellAltitudeDeltaForFlatnessProperty |
| 0xe900ea25 | Float32 | kMaxSlopeForFlatnessProperty | kMaxSlopeForFlatnessProperty |
| 0xe900ea26 | Uint32 | kDefaultLotFoundationTypeProperty | kDefaultLotFoundationTypeProperty |
| 0xe900ea27 | Uint32 | kShouldAttemptLotLevellingProperty | kShouldAttemptLotLevellingProperty |
| 0xe900ea28 | Uint32 | kShouldAttemptInternalLotLevellingProperty | kShouldAttemptInternalLotLevellingProperty |
| 0xe900ea29 | Float32 | kLotAutoLevelInternalAltitudeDeltaProperty | kLotAutoLevelInternalAltitudeDeltaProperty |
| 0xe900ea2a | Float32 | MaxAreaSlopeAllowedForLevellingProperty | MaxAreaSlopeAllowedForLevellingProperty |
| 0xe900ea2b | Uint32 | Lot Developer: Night Update Interval | Update interval in milliseconds for toggling building lights. |
| 0xe900ea2c | Uint32 | Lot Developer: Night Update Count | Number of buildings to toggle lights on per update interval (integer). |
| 0x2a2d7824 | Float32 | Lot Developer: Cost Multiplier vs lot slope | Cost to plop a lot is building + area x this response curve |
| 0x2ab845e7 | Uint32 | Lot Developer: Cost to Demolish Destroyed Tile | Cost to demolish a tile on a lot that has been destroyed |

### Demand Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a1f38b5 | Float32 | Demand: Neutral Tax Rate vs. Population | What is the highest tax rate you can set before demand suffers? |
| 0x4a1f38b6 | Float32 | Demand: Tax Modifier vs. Rate Variance | How much is demand impacted by tax rates above or below neutral? |
| 0x4a1f38b7 | Uint32 | Demand: Days of Tax Penalty | How long a high tax rate depresses demand (even after it is lowered) |
| 0x4a1f38c5 | Float32 | Demand: Commercical Cap Relief for Connections | Relief for first connection (more have diminishing returns) |
| 0x4a1f38c6 | Float32 | Demand: Commercical Cap Relief for Airports | Relief per connected Co population |
| 0x4a1f38c7 | Float32 | Demand: Commercical Cap Relief for Seaports | Relief per industrial trip |
| 0x4a1f38c8 | Float32 | Demand: Industrial Cap Relief for Trips | Relief per neighbor trip |
| 0x4a1f38c9 | Float32 | Demand: Industrial Cap Relief for Airports | Relief per connected Co population |
| 0x4a1f38ca | Float32 | Demand: Industrial Cap Relief for Seaports | Relief per industrial trip |
| 0x8a63f2a1 | Uint32 | Average Salary for Demographic | The average salary for each of the three wealth levels and four education levels (12 total) |

### National Economy Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a1f629f | Uint32 | Nation: Demand ID list | List of IDs corresponding to Demand Modifiers |
| 0x4a1f62a0 | Float32 | Nation: Default Demand Modifier vs. Month | Demand boost over time |
| 0x4a1f62a1 | Float32 | Nation: Demand Modifier 1 vs. Month | Demand boost over time |
| 0x4a1f62a2 | Float32 | Nation: Demand Modifier 2 vs. Month | Demand boost over time |
| 0x4a1f62a3 | Float32 | Nation: Demand Modifier 3 vs. Month | Demand boost over time |
| 0x4a1f62a4 | Float32 | Nation: Demand Modifier 4 vs. Month | Demand boost over time |
| 0x4a1f62a5 | Float32 | Nation: Demand Modifier 5 vs. Month | Demand boost over time |
| 0x4a1f62a6 | Float32 | Nation: Demand Modifier 6 vs. Month | Demand boost over time |
| 0x4a1f62a7 | Float32 | Nation: Demand Modifier 7 vs. Month | Demand boost over time |
| 0x4a1f62a8 | Float32 | Nation: Demand Modifier 8 vs. Month | Demand boost over time |
| 0x4a1f62a9 | Float32 | Nation: Demand Modifier 9 vs. Month | Demand boost over time |
| 0x4a1f62b0 | Float32 | Nation: Demand Modifier 10 vs. Month | Demand boost over time |
| 0x4a1f62b1 | Float32 | Nation: Demand Modifier 11 vs. Month | Demand boost over time |
| 0x4a1f62b2 | Float32 | Nation: Demand Modifier 12 vs. Month | Demand boost over time |
| 0x4a1f6300 | Float32 | Nation: Difficulty Demand Modifier | Demand boost, indexed by difficulty |

### Utility Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x6911e2df | Float32 | Power Funding To Efficiency Curve | Maps difference between actual % funding and % ideal funding to % of a utility output |
| 0x0911e2e6 | Float32 | Utility Strike Response Curve | Maps difference between actual % funding and % ideal funding to % chance of a utility strike |
| 0x29121e8b | Float32 | Power Min Acceptable Funding % | Minimum acceptable percentage for Utility department funding |
| 0x09122027 | Float32 | Utility Strike Efficiency % | Efficiency of utility buildings will drop to this % during a strike |
| 0x2912202e | Uint32 | Utility Strike Duration | Maximum duration of a Utility strike, in months |
| 0x49122036 | Float32 | Utility Min Funding to End Strike | Minimum funding percentage that must be restored to end a utility strike |
| 0xe911e2d1 | Float32 | Power max allowed funding | Maximum allowed funding percentage for utilities |
| 0xa911e2f1 | Uint32 | Power radiation radius | Number of cells surrounding buildings and zones that will also be powered |
| 0xe911e2fc | Float32 | Power plant max production ratio | Maximum allowed percentage for power plant production |
| 0x49134bd4 | Uint32 | Max garbage value for UI | Maximum number of garbage units reported to the UI, must be less than 32767 |
| 0x49134bdd | Uint32 | Max air pollution value for UI | Maximum air pollution value reported to the UI, must be less than 32767 |
| 0x09134be2 | Uint32 | Max water pollution value for UI | Maximum water pollution value reported to the UI, must be less than 32767 |
| 0x89135044 | Uint32 | Max radiation pollution value for UI | Maximum radiaiton pollution value reported to the UI, must be less than 32767 |
| 0x0913519b | Uint32 | Garbage Pollution Threshold | When a cell has this much garbage, it's considered polluted |
| 0xa91351a6 | Uint32 | Air Pollution Threshold | When a cell has this much air pollution, it's considered polluted |
| 0x091351ae | Uint32 | Water Pollution Threshold | When a cell has this much water pollution, it's considered polluted |
| 0x291351b5 | Uint32 | Radiation Pollution Threshold | When a cell has this much radiation, it's considered polluted |
| 0x09135479 | Uint32 | Garbage decompostion amount | Number of garbage units that decompose (i.e., disappear) each month |
| 0x09135482 | Float32 | Garbage UI scaling factor | Scaling factor to convert simulator garbage units to whatever units the UI displays (tons, Kgs) |
| 0x68f5436a | Uint32 | Water pipe effect radius | Number of cells surrounding water pipes that will also be watered |
| 0xaa161f81 | Uint32 | Max acceptable pumped water pollution level | Water pumps will not function if water pollution higher than this level |
| 0x68f5436b | Uint32 | Fresh water pump reach | Number of cells away from fresh water a water pump can be placed |
| 0x68f5436c | Uint32 | Salt water pump reach | Number of cells away from salt water a water pump can be placed |
| 0x68f5436d | Uint32 | Fresh water distance loss | Percentace by which water production is reduced when not within range of fresh water source |
| 0x69501944 | Float32 | Traffic air pollution factor | Affects how traffic density equates to air pollution |
| 0x098b25c8 | Uint32 | Max cells between power poles | The maximum number of cells allowed between power poles |
| 0x098b27d0 | Float32 | Minimum power line height | The minimum distance allowed between a power line and the terrain |
| 0xe9a18d3f | Float32 | Power line control max horiz. distance | Max horizontal distance from the center of the line at which the control points are placed |
| 0x49a1e8c4 | Float32 | Power line control horiz. % | Percent of line length at which to place control points, horizontally |
| 0x89a18fc4 | Float32 | Power line control max vertical distance | Max vertical distance from the center of the line at which the control points are placed |
| 0xe9a1e8d4 | Float32 | Power line control vertical % | Percent of line length at which to place control points, vertically |
| 0x49a195c0 | Float32 | Power line curve distance between points | Distance between the points generated for power line curves |
| 0x4a5f5953 | Uint32 | Power pole placement cost | Cost to place a power pole using the power line tool |
| 0x0a5f596b | Float32 | Power line placement cost | Cost of placing each cell of wire |
| 0x89a1e8fb | Uint32 | Minimum number of curve points | Minimum number of points to generate on power line Bezier curve |
| 0x69a437f6 | Float32 | Garbage Prop Request Curve | Shares of garbage props requested vs. garbage percentage of max |
| 0x0a10c772 | Float32 | Water Pollution Effect Strength Curve | Water Pollution Average Level to Water Pollution Decal Alpha curve |
| 0x0a10c773 | Float32 | Air Pollution Effect Strength Curve | Air Pollution Average Level to Air Pollution Particle Emission Rage curve |
| 0x0a10c774 | Float32 | Radiation Pollution Effect Strength Curve | Radiation Pollution Average Level to Radiation Effect Strength curve |
| 0x0a10c775 | Float32 | Garbage Pollution Effect Strength Curve | Radiation Pollution Average Level to Radiation Effect Strength curve |
| 0xe9ac43e7 | Float32 | Power line scaling factor | Array of scaling factors for the width of the power lines, one per zoom level. |
| 0x0911e2e8 | Float32 | Funding percentage to decay rate multiplier response curve | Multiples the rate of aging based on funding level |
| 0x0911e2e9 | Float32 | Usage percentage to decay rate multiplier response curve | Multiples the rate of aging based on usage level |
| 0xaa1f8ab7 | Float32 | Garbage service cost per unit of garbage | Cost per unit of garbage sent to landfill, incinerator or waste-to-energy |
| 0x8a235c56 | Float32 | Pipe burst probability | Likelihood per month that a distressed pipe will burst |
| 0x0a2eced8 | Float32 | Power Pole Demolition Cost | Cost to demolish a power pole. Lines are ignored |
| 0x6a406201 | Uint32 | Air Pollution Delta | Maximum amount of air pollution that can be added to/subtracted from each cell per month. |
| 0x8a40620b | Uint32 | Water Pollution Delta | Maximum amount of water pollution that can be added to/subtracted from each cell per month. |
| 0xea4025a9 | Float32 | Water Department Max Funding | Max funding percentage for the water department |
| 0x6a410bf2 | Float32 | Water Funding To Efficiency Curve | Maps difference between actual % funding and % ideal funding to % of a utility output |
| 0x4a652679 | Uint32 | Max Garbage on Valve | Maximum amount of garbage units the valve can hold |
| 0x4a65267a | Uint32 | Landfill Tile Capacity | Amount of garbage units each landfill tile can hold |
| 0x8c19c3e9 | Float32 | Garbage Transport Versus Landfill Tiles | How much garbage can be delivered to the landfill each month |
| 0xaa713782 | Float32 | Funding percentage to power pole decay/repair | Converts a funding level (percentage) into a decay rate (negative numbers) or repair rate (positive numbers) |
| 0xca7138c4 | Float32 | Funding percentage to pipe decay/repair | Converts a funding level (percentage) into a decay rate (negative numbers) or repair rate (positive numbers) |
| 0x8a84778f | Float32 | Monthly Cost Per Pipe | Maintenance cost for each pipe occupant |

### Traffic Simulator

> Main article: [Traffic Simulator](/traffic-simulator)

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x491332e6 | Float32 | Traffic Volume Per Population | Traffic volume generated per point of population in a building |
| 0x491332e7 | Float32 | Max speed by Network for walking | Speed to walk through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332e8 | Float32 | Max speed by Network for driving | Speed to drive through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332e9 | Float32 | Max speed by Network for a bus | Speed to bus travel through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332ea | Float32 | Max speed by Network for a train | Speed to train travel through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332eb | Float32 | Max speed by Network for a truck | Speed to truck travel through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332ec | Float32 | Max speed by Network for a freight train | Speed to train travel through rd, rl, hwy, st, x, x, ave, sub, lr, mo, ow, dr, gh |
| 0x491332ed | Float32 | Max speed by Network for subways | Speed to subway travel. Set the eighth value. |
| 0x491332ee | Float32 | Max speed by Network for el train | Speed to ride el train. Set the eighth value. |
| 0x491332ef | Float32 | Max speed by Network for monorail | Speed to ride monorail. Set the ninth value. |
| 0x29136788 | Float32 | Monthly Traffic Density Reduction | Traffic density multiplied by this each month |
| 0x6a84493e | Float32 | Monthly cost for network tile | Upkeep cost per tile of each network type (rd, rl, hwy, st, x, x, ave, sub, lr) |
| 0xa92356ae | Float32 | Max roads funding percent | Maximum allowed funding percentage for roads |
| 0xa92356af | Float32 | Max mass transit funding percent | Maximum allowed funding percentage for mass transit |
| 0xa92356b0 | Float32 | Damaged road extra step cost | Additional cost to travel on a damaged road tile |
| 0xa92356b1 | Float32 | Income per tile by travel type | Income gained for each tile: walk, car, bus, rail, freight truck, freight train, subway, lt rl |
| 0xa92356b2 | Uint8 | Mass Transit Usage Chance | Percent chance an RCI trip will allow use of mass transit |
| 0xa92356b3 | Float32 | Network Traffic Capacity | Level at which traffic volume becomes uncomfortable to sims (rd, rl, hwy, st, x, x, ave, sub, lr) |
| 0xa92356b4 | Bool | Travel type generates traffic | Order: walk, car, bus, train, subway, lt rl |
| 0xa92356b5 | Bool | Travel type can reach destination | Order: walk, car, bus, train, subway, lt rl |
| 0xa92356b8 | Uint32 | Maximum distance from origin to network | How far a trip can jump from its starting zone to a road/rail/etc |
| 0xa92356b9 | Float32 | Congestion vs Speed | Maps speed multiplier as a function of congestion |
| 0xa92356ba | Float32 | Commute trip max time | Maximum time for a commute trip in minutes |
| 0xa92356bb | Float32 | Intersection and Turn Capacity Effect | Diminishing effect of an intersection or turn on capacity |
| 0xa92356bc | Float32 | Trip Starting Cost by travel type | Starting overhead cost in time for each travel type |
| 0xa92356bd | Float32 | Job Scaling Constant | Multiplies building capacity to determine number of jobs there |
| 0xa92356be | Float32 | Population Background Traffic | Amount of background (non-trip) traffic volume generated per population point for R, C, and I zones |
| 0xa92356bf | Bool | Travel type affected by traffic | Order: walk, car, bus, train, freight truck, freight train, subway, lt rl |
| 0xea8c3cdb | Float32 | Trip Starting Cost by travel type for Mass Transit | Starting overhead cost in time for each travel type for mass transit preferred trips |
| 0xcad64136 | Float32 | Trip Starting Cost by travel type for Car Pref | Starting overhead cost in time for each travel type for car preferred trips |
| 0x4953e8a3 | Uint8 | Travel strategy percent WealthNone | Odds of selecting each travel strategy: Mass Transit, Car, Fastest |
| 0x4953e8a4 | Uint8 | Travel strategy percent Wealth\$ | Odds of selecting each travel strategy: Mass Transit, Car, Fastest |
| 0x4953e8a5 | Uint8 | Travel strategy percent Wealth\$\$ | Odds of selecting each travel strategy: Mass Transit, Car, Fastest |
| 0x4953e8a6 | Uint8 | Travel strategy percent Wealth\$\$\$ | Odds of selecting each travel strategy: Mass Transit, Car, Fastest |
| 0x49a2e8be | Float32 | Freight traffic scaling factor | Percentage of industrial bldg. population that will generate freight trips |
| 0xca5f7821 | Float32 | Transit Switch Entry Cost vs. Budget | Maps the budget percent (0-100) to a multiplier on the time cost of using a transit switch |
| 0x4a678060 | Float32 | Nearest Destination Attractiveness | Lower scores means more side explorations but also more CPU time (Pathfinding Heuristic) |
| 0xca76013b | Float32 | Trip Length to Minutes Display Multiplier | Multiply the trip length map values (0-255, 255 = Max Commute Time) by this value to get a time in minutes for display purposes" |
| 0xea7b5f06 | Float32 | Max Mass Transit Strategy Trip Length | Max time in raw trip length that the mass transit preferred strategy will go using mass transit |
| 0x8c3caef5 | Float32 | Ferry Fare | Income per traveller from a ferry trip |
| 0x4be09ec9 | Float32 | Congestion to Accident Probability | Maps congestion to accident probablity |
| 0x4be09eca | Float32 | Capacity to Accident Probability | Maps capacity to accident probablity |
| 0x4be09ecb | Float32 | Accident Duration | Time (in seconds) that a traffic accident lasts |
| 0x4be09ecc | Float32 | Accident Check Period | Period (in seconds) that the traffic sim tests for accidents |
| 0x0bd86fd4 | Float32 | Funding to Damage Acceleration Curve | Maps funding (as percentage) to road/rail damage acceleration |
| 0x0bd86fd5 | Float32 | Rail Damage Accident Factor | Probability (0 to 1.0) that a train going over a rail pothole will cause derailment |

### Residential Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x2918949e | Float32 | Health Funding To Efficiency Curve | Maps difference between actual % funding and % ideal funding to % of Health output |
| 0x691894a4 | Float32 | Health Strike Response Curve | Maps difference between actual % funding and % ideal funding to % chance of a Health strike |
| 0x0a53b2f9 | Float32 | Health Funding to Coverage Curve | Maps difference between actual % funding and % ideal funding to % coverage |
| 0xe918946f | Float32 | (OBS) Health Min Acceptable Funding % | Minimum acceptable percentage for Health department funding |
| 0xa9189479 | Float32 | Health Init/Max Allowed Funding | Initial and Maximum allowed funding percentage for health department |
| 0x89189482 | Float32 | Health Strike Efficiency % | Efficiency of Health buildings will drop to this % during a strike |
| 0x8918948b | Uint32 | Health Strike Duration | Maximum duration of a Health strike, in months |
| 0x89189495 | Float32 | Health Min Grade to End Strike | Minimum grade that all health buildings must have to end a Health strike |
| 0x691894c6 | Float32 | School Funding To Efficiency Curve | Maps difference between actual % funding and % ideal funding to % of Education output |
| 0xc91894cb | Float32 | School Strike Response Curve | Maps difference between actual % funding and % ideal funding to % chance of a School strike |
| 0xea53b30f | Float32 | School Funding to Coverage Curve | Maps difference between actual % funding and % ideal funding to % coverage |
| 0xc91894a8 | Float32 | (OBS) School Min Acceptable Funding % | Minimum acceptable percentage for School department funding |
| 0x891894ad | Float32 | School Init/Max Allowed Funding | Initial and Maximum allowed funding percentage for schools |
| 0xa91894bc | Uint32 | School Strike Duration | Maximum duration of a School strike, in months |
| 0xe91894b3 | Float32 | School Strike Efficiency % | Efficiency of School buildings will drop to this % during a strike |
| 0x691894c0 | Float32 | School Min Grade to End Strike | Minimum grade that all schools must have to end a School strike |
| 0xc929c433 | Float32 | EQ Decay | Amount by which EQ decays each month |
| 0x0929c439 | Float32 | HQ Decay | Amount by which HQ decays each month |
| 0xc929c652 | Uint8 | Low Wealth Average Age | Average age assigned to new Low Wealth residents |
| 0x0929cc30 | Uint8 | Medium Wealth Average Age | Average age assigned to new Medium Wealth residents |
| 0x0929cc36 | Uint8 | High Wealth Average Age | Average age assigned to new High Wealth residents |
| 0xc929cc58 | Uint8 | Low Wealth EQ | EQ assigned to new Low Wealth residents |
| 0x0929cc65 | Uint8 | Medium Wealth EQ | EQ assigned to new Medium Wealth residents |
| 0x2929cc6b | Uint8 | High Wealth EQ | EQ assigned to new High Wealth residents |
| 0xc929cc8d | Uint8 | Low Wealth HQ | HQ assigned to new Low Wealth residents |
| 0x6929cc92 | Uint8 | Medium Wealth HQ | HQ assigned to new Medium Wealth residents |
| 0x4929cc97 | Uint8 | High Wealth HQ | HQ assigned to new High Wealth residents |
| 0x6941a67f | Float32 | Health Quotient to Life Expectancy Curve | Maps HQ of a tract to the Life Expectancy of that tract |
| 0x4941a92b | Float32 | Life Expectancy to Workforce % Curve | Maps Life Expectancy of a tract to the % of that tract that is in the workforce |
| 0x6941b022 | Float32 | Air Pollution to HQ Decay Curve | Maps amount of air pollution in a tract to the rate at which the HQ in that tract decays |
| 0xa941b028 | Float32 | Water Pollution to HQ Decay Curve | Maps amount of water pollution in a tract to the rate at which the HQ in that tract decays |
| 0xc941b02e | Float32 | Garbage Pollution to HQ Decay Curve | Maps amount of garbage pollution in a tract to the rate at which the HQ in that tract decays |
| 0xca027307 | Uint8 | Average Age reset value | When average age reaches life expectancy in a tract, the tract's average age is set to this value" |
| 0xca027325 | Float32 | EQ reset percent | When average age reaches life expectancy in a tract, the tract's EQ is multiplied by this value |
| 0xca027328 | Float32 | HQ reset percent | When average age reaches life expectancy in a tract, the tract's HQ is multiplied by this value |
| 0xea540621 | Float32 | Avg. Age to 1-10 Age Group | How average age translates to the distribution of population into the 1-10 age group |
| 0xea540622 | Float32 | Avg. Age to 11-20 Age Group | How average age translates to the distribution of population into the 11-20 age group |
| 0xea540623 | Float32 | Avg. Age to 21-30 Age Group | How average age translates to the distribution of population into the 21-30 age group |
| 0xea540624 | Float32 | Avg. Age to 31-40 Age Group | How average age translates to the distribution of population into the 31-40 age group |
| 0xea540625 | Float32 | Avg. Age to 41-50 Age Group | How average age translates to the distribution of population into the 41-50 age group |
| 0xea540626 | Float32 | Avg. Age to 51-60 Age Group | How average age translates to the distribution of population into the 51-60 age group |
| 0xea540627 | Float32 | Avg. Age to 61-70 Age Group | How average age translates to the distribution of population into the 61-70 age group |
| 0xea540628 | Float32 | Avg. Age to 71-80 Age Group | How average age translates to the distribution of population into the 71-80 age group |
| 0xea540629 | Float32 | Avg. Age to 81-90 Age Group | How average age translates to the distribution of population into the 81-90 age group |
| 0x8a891421 | Uint32 | School Capacity To Staff Divisor | The school's capacity is divided by this number to determine the number of teachers on staff |
| 0x8a89142a | Uint32 | Hospital Capacity To Staff Divisor | The hospital's capacity is divided by this number to determine the number of doctors on staff |
| 0x6a9f6edd | Float32 | Coverage radius slop multiplier | Coverage radii are multiplied by this value when computing tract coverage |
| 0x4aa84161 | Float32 | Maximum EQ Boost | Max EQ boost achievable without reward buildings. Used to scale values for Sims opinion polls. |
| 0x2aa84164 | Float32 | Maximum HQ Boost | Max HQ boost achievable without reward buildings. Used to scale values for Sims opinion polls. |
| 0x6ab70da7 | Float32 | Death's door HQ | If a tract's HQ falls below this number, they're at death's door." |
| 0x4ab70dac | Float32 | Death's door effect chance | Percent chance (0-100.0) that the effect will play for a tract that's at death's door. |
| 0x6ab71654 | Float32 | Death's door effect height | Base height above terrain at which the effect will play for a tract that's at death's door. |
| 0x4ab71659 | Float32 | Death's door effect height delta | Random height variance for effect for a tract that's at death's door. |
| 0xec43826b | Uint32 | School Capacity Chunk Size | How many people are represented by one unit in the coverage map |
| 0xac43826d | Uint32 | Hospital Capacity Chunk Size | How many people are represented by one unit in the coverage map |

### Police/Jail Simulator

<table>
<thead>
<tr>
<th><p>Property No.</p></th>
<th><p>Type</p></th>
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="4"><p><strong>Police Station Building</strong></p></td>
</tr>
<tr>
<td><p>0x48d71ed0</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Center Strength</p></td>
<td><p>(in Protection units)</p></td>
</tr>
<tr>
<td><p>0x48d71ed1</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Exterior Strength</p></td>
<td><p>(in Protection units)</p></td>
</tr>
<tr>
<td><p>0x48d71ed2</p></td>
<td><p>Float32</p></td>
<td><p>Police Station, Radius</p></td>
<td><p>(in meters)</p></td>
</tr>
<tr>
<td><p>0x48d71ed5</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Total Dispatches</p></td>
<td><p>Number of trucks this station can send</p></td>
</tr>
<tr>
<td><p>0x48d71ed9</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Dispatch Center Strength</p></td>
<td><p>(in Protection units)</p></td>
</tr>
<tr>
<td><p>0x48d71eda</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Dispatch Exterior Strength</p></td>
<td><p>(in Protection units)</p></td>
</tr>
<tr>
<td><p>0x48d71edb</p></td>
<td><p>Float32</p></td>
<td><p>Police Station, Dispatch Radius</p></td>
<td><p>(in meters)</p></td>
</tr>
<tr>
<td><p>0xcc0b0705</p></td>
<td><p>Sint32</p></td>
<td><p>Police Station, Total Copter Dispatches</p></td>
<td><p>Number of police helicopters this station can send</p></td>
</tr>
<tr>
<td colspan="4"><p><strong>Jail Building</strong></p></td>
</tr>
<tr>
<td><p>0x48d71ee0</p></td>
<td><p>Sint32</p></td>
<td><p>Jail, Inmate Capacity</p></td>
<td><p>Jail Inmate Capacity</p></td>
</tr>
<tr>
<td><p>0x48d71ee4</p></td>
<td><p>Sint32</p></td>
<td><p>Jail, Overcapacity Cost (per person)</p></td>
<td><p>Monthly cost, per convict, for every prisoner over regular (100%) capacity</p></td>
</tr>
<tr>
<td colspan="4"><p><strong>General</strong></p></td>
</tr>
<tr>
<td><p>0x68ddae92</p></td>
<td><p>Float32</p></td>
<td><p>Police, Max Jail Overcrowding Percentage</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae93</p></td>
<td><p>Float32</p></td>
<td><p>Police, Funding To Efficiency Response Curve</p></td>
<td><p>See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae95</p></td>
<td><p>Float32</p></td>
<td><p>Police, Max Allowed Funding Percentage</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae97</p></td>
<td><p>Float32</p></td>
<td><p>Police, Monthly Criminal Rehabilitation Percent</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9a</p></td>
<td><p>Float32</p></td>
<td><p>Police, Strike Efficiency</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9b</p></td>
<td><p>Uint32</p></td>
<td><p>Police, Max Strike Duration</p></td>
<td><p>In days. See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9c</p></td>
<td><p>Float32</p></td>
<td><p>Police, Min Funding To End Strikes</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9e</p></td>
<td><p>Float32</p></td>
<td><p>Police, Strike Response Curve</p></td>
<td><p>See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9f</p></td>
<td><p>Uint32</p></td>
<td><p>Police, Arrest Threshold</p></td>
<td><p>If crime is committed in a cell whose police protection value is above this, they'll get arrested</p></td>
</tr>
<tr>
<td><p>0xea614f63</p></td>
<td><p>Float32</p></td>
<td><p>Jail, Jailbreak Response Curve</p></td>
<td><p>Maps REAL jail capacity to jailbreak chance</p></td>
</tr>
<tr>
<td><p>0xea614f64</p></td>
<td><p>Float32</p></td>
<td><p>Jail, Jailbreak Escapee Percentage</p></td>
<td><p>Min/max percentage (0.0-100.0) of jail capacity that will escape during jailbreaks</p></td>
</tr>
<tr>
<td><p>0xea614f65</p></td>
<td><p>Float32</p></td>
<td><p>Jail, End Jailbreak Capacity</p></td>
<td><p>Stop any jailbreak in progress when REAL jail capacity percentage goes below this value</p></td>
</tr>
<tr>
<td><p>0x68ddaea0</p></td>
<td><p>Float32</p></td>
<td><p>Jail, Funding To Efficiency Response Curve</p></td>
<td><p>See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae91</p></td>
<td><p>Uint32</p></td>
<td><p>(Obs) Police, Update Period</p></td>
<td><p>In days. See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae94</p></td>
<td><p>Float32</p></td>
<td><p>(Obs) Police, Min Acceptable Funding Percentage</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae96</p></td>
<td><p>Uint32</p></td>
<td><p>(Obs) Police, Max Acceptable Crime Level</p></td>
<td><p>See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae98</p></td>
<td><p>Float32</p></td>
<td><p>(Obs) Police, Conviction Percentage</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae99</p></td>
<td><p>Float32</p></td>
<td><p>(Obs) Police, Unfailed Criminal Efficiency Percentage</p></td>
<td><p>0.0-100.0, See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x68ddae9d</p></td>
<td><p>Float32</p></td>
<td><p>(Obs) Police, Property Crimes Value Ratio</p></td>
<td><p>See ISC4PoliceSimulator.h</p></td>
</tr>
<tr>
<td><p>0x48d71ed3</p></td>
<td><p>Sint32</p></td>
<td><p>(Obs) Police Station, Monthly Upkeep Cost</p></td>
<td><p>(in Simoleons)</p></td>
</tr>
<tr>
<td><p>0x48d71ee2</p></td>
<td><p>Sint32</p></td>
<td><p>(Obs) Jail, Monthly Upkeep Cost</p></td>
<td><p>Jail Monthly Upkeep Cost</p></td>
</tr>
</tbody>
</table>

### Crime Simulator

<table>
<thead>
<tr>
<th><p>Property No.</p></th>
<th><p>Type</p></th>
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="4"><p><strong>Crime Types</strong></p></td>
</tr>
<tr>
<td><p>0xaa12fcb0</p></td>
<td><p>String</p></td>
<td><p>Crime Name</p></td>
<td></td>
</tr>
<tr>
<td><p>0xaa12fcb1</p></td>
<td><p>Uint32</p></td>
<td><p>Icon Resource Key</p></td>
<td><p>TGI</p></td>
</tr>
<tr>
<td><p>0xaa12fcb2</p></td>
<td><p>Uint8</p></td>
<td><p>Zone Filter</p></td>
<td><p>Zone types compatible with crime (none == can appear in any zone)</p></td>
</tr>
<tr>
<td><p>0xaa12fcb3</p></td>
<td><p>Uint8</p></td>
<td><p>Wealth Filter</p></td>
<td><p>Zone wealth values compatible with crime (none == can appear around any wealth)</p></td>
</tr>
<tr>
<td><p>0xaa12fcb4</p></td>
<td><p>Uint8</p></td>
<td><p>Zone Purpose Filter</p></td>
<td><p>Zone purpose types compatible with crime (none == can appear around any purpose)</p></td>
</tr>
<tr>
<td><p>0xaa12fcb5</p></td>
<td><p>Uint8</p></td>
<td><p>Crime Grid Value</p></td>
<td><p>The crime grid tract value will be increased by this amount</p></td>
</tr>
<tr>
<td><p>0xaa12fcb6</p></td>
<td><p>Uint8</p></td>
<td><p>Trigger Fire</p></td>
<td><p>If set to non-zero value, this will trigger a fire</p></td>
</tr>
<tr>
<td><p>0xaa12fcb7</p></td>
<td><p>Uint8</p></td>
<td><p>Lot Condition Filter</p></td>
<td><p>Lot conditions compatible with crime</p></td>
</tr>
<tr>
<td><p>0xaa12fcb8</p></td>
<td><p>Float32</p></td>
<td><p>Relative Occurrance</p></td>
<td><p>Relative occurance weight of this crime, only has meaning relative to values for other crimes.</p></td>
</tr>
<tr>
<td colspan="4"><p><strong>General</strong></p></td>
</tr>
<tr>
<td><p>0xe8ec2720</p></td>
<td><p>Uint32</p></td>
<td><p>Crime Update Period</p></td>
<td><p>How often the Crime simulator updates, in days</p></td>
</tr>
<tr>
<td><p>0xe8ec2721</p></td>
<td><p>Float32</p></td>
<td><p>Crime Police Factor</p></td>
<td><p>Crime Police Factor</p></td>
</tr>
<tr>
<td><p>0x49a34301</p></td>
<td><p>Float32</p></td>
<td><p>Crime Prop Request Curve</p></td>
<td><p>Crime level (0-1) vs. Prop Share</p></td>
</tr>
<tr>
<td><p>0x8a0cbaa3</p></td>
<td><p>Float32</p></td>
<td><p>Crime, Jobless Indicator Smoothing factor</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa4</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$: EQ -&gt; Base Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa5</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$$: EQ -&gt; Base Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa6</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$$$: EQ -&gt; Base Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa7</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$: Jobless ratio -&gt; Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa8</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$$: Jobless ratio -&gt; Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaa9</p></td>
<td><p>Float32</p></td>
<td><p>Crime, R$$$: Jobless ratio -&gt; Criminality Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaaa</p></td>
<td><p>Float32</p></td>
<td><p>Crime, Criminality -&gt; Crimes Curve</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaab</p></td>
<td><p>Float32</p></td>
<td><p>Crime, Police Protection -&gt; Crime Attenuation</p></td>
<td></td>
</tr>
<tr>
<td><p>0x8a0cbaac</p></td>
<td><p>Float32</p></td>
<td><p>Crime, Crime Grid Decay Factor</p></td>
<td><p>Example: 0.5 means values get halved every month</p></td>
</tr>
<tr>
<td><p>0x8a0cbaad</p></td>
<td><p>Float32</p></td>
<td><p>Crime, Criminal Grid Decay Factor</p></td>
<td><p>Fraction (0 to 1.0) of unjailed criminals that will commit crimes next month</p></td>
</tr>
</tbody>
</table>

### Fire Protection Simulator

<table>
<thead>
<tr>
<th><p>Property No.</p></th>
<th><p>Type</p></th>
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="4"><p><strong>Fire Station Props</strong></p></td>
</tr>
<tr>
<td><p>0x08f55dc0</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Center Strength</p></td>
<td><p>(in Fire Protection units)</p></td>
</tr>
<tr>
<td><p>0x08f55dc1</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Exterior Strength</p></td>
<td><p>(in Fire Protection units)</p></td>
</tr>
<tr>
<td><p>0x08f55dc2</p></td>
<td><p>Float32</p></td>
<td><p>Fire Station, Radius</p></td>
<td><p>(in meters)</p></td>
</tr>
<tr>
<td><p>0x08f55dc5</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Total Dispatches</p></td>
<td><p>Number of trucks this station can send</p></td>
</tr>
<tr>
<td><p>0x29233e9a</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Dispatch Center Strength</p></td>
<td><p>(in Fire Protection units)</p></td>
</tr>
<tr>
<td><p>0x29233e9b</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Dispatch Exterior Strength</p></td>
<td><p>(in Fire Protection units)</p></td>
</tr>
<tr>
<td><p>0x29233e9c</p></td>
<td><p>Float32</p></td>
<td><p>Fire Station, Dispatch Radius</p></td>
<td><p>(in meters)</p></td>
</tr>
<tr>
<td><p>0x0c0afdd7</p></td>
<td><p>Sint32</p></td>
<td><p>Fire Station, Total Plane Dispatches</p></td>
<td><p>Number of planes this station can send</p></td>
</tr>
<tr>
<td colspan="4"><p><strong>General</strong></p></td>
</tr>
<tr>
<td><p>0x29233e8d</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, Funding Efficiency Curve</p></td>
<td><p>See ISC4FireProtectionSimulator.h</p></td>
</tr>
<tr>
<td><p>0x29233e8f</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, Max Allowed Funding</p></td>
<td><p>100.0+ Maximum percentage you can fund a fire station</p></td>
</tr>
<tr>
<td><p>0x29233e94</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, Strike Efficiency Multiplier</p></td>
<td><p>0.0-1.0 efficiency multiplier when stations are on strike</p></td>
</tr>
<tr>
<td><p>0x29233e95</p></td>
<td><p>Sint32</p></td>
<td><p>FireProtectionSim, Max Strike Duration</p></td>
<td><p>Maximum number of days a strike can last</p></td>
</tr>
<tr>
<td><p>0x29233e96</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, Min Funding To End Strikes</p></td>
<td><p>0.0-100.0, See ISC4FireProtectionSimulator.h</p></td>
</tr>
<tr>
<td><p>0x29233e98</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, Strike Response Curve</p></td>
<td><p>See ISC4FireProtectionSimulator.h"</p></td>
</tr>
<tr>
<td><p>0x69b425db</p></td>
<td><p>Float32</p></td>
<td><p>FireProtectionSim, StationNoRoad Multiplier</p></td>
<td><p>(0.0 - 1.0)</p></td>
</tr>
<tr>
<td><p>0x08f55dc3</p></td>
<td><p>Sint64</p></td>
<td><p>(Obs) Fire Station, Monthly Upkeep Cost</p></td>
<td><p>in Simoleans</p></td>
</tr>
<tr>
<td><p>0x08f55dc4</p></td>
<td><p>Float32</p></td>
<td><p>(Obs) Fire Station, Funding Percentage</p></td>
<td><p>Percentage of funding</p></td>
</tr>
</tbody>
</table>

### Flamability Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xc9b40128 | Float32 | Flammability multiplier, summer | Flammability multiplier during summer |
| 0x29b40134 | Float32 | Flammability multiplier, abandonment | Flammability multiplier if building if abandoned |
| 0x29b4013b | Float32 | Flammability multiplier, no water | Flammability multiplier if building is not watered |
| 0x29b4013c | Uint32 | Flammability, hotspot settings | Hotspot settings: threshold value (0-255), radius (in tracts), minimum weight |
| 0x29b4013d | Float32 | Flammability, hotspot fire probability | Maps hotspot weight (# of cells above threshold) to monthly fire probability (in percent 0-100) |
| 0x29b4013e | Float32 | Flammability, random fire probability | Monthly fire probability (in percent 0-100) of random lot fire |

### Aura Simulator

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xea023270 | Float32 | Aura, Park Effect | Maps grid data to aura effect |
| 0xea023271 | Float32 | Aura, Pollution Effect, Air | Maps grid data to aura effect |
| 0xea023272 | Float32 | Aura, Pollution Effect, Water | Maps grid data to aura effect |
| 0xea023273 | Float32 | Aura, Pollution Effect, Garbage | Maps grid data to aura effect |
| 0xea023274 | Float32 | Aura, Pollution Effect, Radiation | Maps grid data to aura effect |
| 0xea023275 | Float32 | Aura, School Effect | Maps grid data to aura effect |
| 0xea023276 | Float32 | Aura, Hospital Effect | Maps grid data to aura effect |
| 0xea023277 | Float32 | Aura, Crime Effect | Maps grid data to aura effect |
| 0xea023278 | Float32 | Aura, Trip Length | Maps grid data to aura effect |
| 0xea023279 | Float32 | Aura, Traffic | Maps grid data to aura effect |
| 0xea02327a | Float32 | Aura, Long Term Decay Factor | 1.0 means no decay, 0.0 means full decay (no smoothing) |
| 0xea02327b | Float32 | Aura, Short Term Decay Factor | 1.0 means no decay, 0.0 means full decay (no smoothing) |
| 0xea02327c | Sint32 | Aura, Base Aura (Low) | Base aura for R\$,Cs\$,Id occupancy |
| 0xea02327d | Sint32 | Aura, Base Aura (Med) | Base aura for R\$\$,Cs\$\$,Co\$\$,Ir,Im occupancy |
| 0xea02327e | Sint32 | Aura, Base Aura (High) | Base aura for R\$\$\$,Cs\$\$\$,Co\$\$\$ occupancy |
| 0xea02327f | Float32 | Aura, Tax Rate Change Effect | Maps tax rate change (in percent) to aura effect |
| 0xea023280 | Float32 | Aura, Value/Wealth Effect | Maps (value_type-wealth_type) to aura effect |
| 0xea023290 | Float32 | Aura, Transient Effect, Fire | Magnitude and radius in meters of transient aura effect |
| 0xea023291 | Float32 | Aura, Transient Effect, Flora | Magnitude and radius in meters of transient aura effect |
| 0xea023292 | Float32 | Aura, Transient Effect, Civic Plop | Magnitude and radius in meters of transient aura effect |
| 0xea023293 | Float32 | Aura, Transient Effect, Network Plop | Magnitude and radius in meters of transient aura effect |
| 0xea0232a0 | Sint32 | Aura, Hotspot Settings | Hotspot settings: threshold value (0-255), radius (in tracts), minimum weight |
| 0xea0232a1 | Float32 | Aura, Hotspot Riot Probability | Maps hotspot weight (# of cells above threshold) to monthly fire probability (in percent 0-100) |

### Other

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x47e2c200 | Uint8 | Tract Size | Power of 2; determines the size of the sim grid |
| 0x68f26014 | Uint32 | Map View Unsigned Colors | RGBA color of 3D overlay of 2-color map view |
| 0x68f26015 | Uint32 | Map View Signed Colors | RGBA color of 3D overlay of 3-color map view |

## Zone Manager

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xe94825b2 | Sint32 | kZM_mZoneMinCellSize | kZM_mZoneMinCellSize |
| 0xe94825b3 | Sint32 | kZM_mZoneMaxCellSize | kZM_mZoneMaxCellSize |
| 0xe94825b4 | Sint64 | kZM_mZoneCreationCostArray | kZM_mZoneCreationCostArray |
| 0xe94825b5 | Sint64 | kZM_mZoneDestructionCostArray | kZM_mZoneDestructionCostArray |
| 0xe94825b6 | Uint32 | kZM_mZoneTextureResourceInstanceArray | kZM_mZoneTextureResourceInstanceArray |
| 0xe94825b7 | Uint8 | Zone Display Alpha | Replaces drag color alpha after zone placement |
| 0xe94825b8 | Uint32 | Zone Drag Color | RGBA color to blend with black and white texture NRRRCCCIIIMASSLP |
| 0xe94825b9 | Float32 | Zone Max Slope | Meters per cell must be less than this value NRRRCCCIIIMASSLP |

## Ordinance

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x28ebbc30 | Uint32 | Ordinance ID | ID of this ordinance |
| 0x6a416b21 | Uint32 | Name Key | Resource key of ordinance name resource |
| 0x28ebbc32 | String | Name String (non-localizable) | Ordinance name |
| 0xca416b2a | Uint32 | Description Key | Resource key of ordinance description |
| 0x28ebbc34 | String | Description String (non-localizable) | Ordinance description string |
| 0x28ebbc35 | Uint32 | Year Available | Year this ordinance becomes available |
| 0x28ebbc36 | Float32 | Monthly Chance | Monthly chance of this ordinance bemoming available |
| 0x28ebbc37 | Sint32 | Enactment Income | Revenue generated by enacting this ordinance |
| 0x28ebbc38 | Sint32 | Retractment Income | Cost of retracting this ordinance |
| 0x28ebbc39 | Sint32 | Monthly Constant Income | Constant part of monthly income generated by this ordinance |
| 0x28ebbc3a | Float32 | Monthly Income Factor | Factor applied to ordinance cost basis |
| 0x28ebbc3b | Uint32 | Advisor ID | Advisor ID for this ordinance |
| 0x28ebbc3c | Bool | Income Ordinance | True for ordinances that should appear on income part of budget |
| 0x28ed0380 | Float32 | Crime Effect | Crime multiplier |
| 0xaa5b8407 | Sint32 | Mayor Rating | This value get added globally to mayor rating |
| 0x08f79b8e | Float32 | Air Effect | Effect (multiplier) this ordinance has on air pollution |
| 0x28f42aa0 | Float32 | Flammability Effect | Effect (multiplier) this ordinance has on flammability |
| 0xe8f79c8b | Float32 | Water Effect | Effect (multiplier) this ordinance has on water pollution |
| 0xe8f79c90 | Float32 | Garbage Effect | Effect (multiplier) this ordinance has on garbage |
| 0xa8f4eb0c | Float32 | Water Use Reduction | Effect (multiplier) this ordinace has on water use |
| 0x0911e117 | Float32 | Power Reduction Effect | Factor by which this ordinance reduces power consumption |
| 0x2a631000 | Float32 | Residential Demand Effect | Factor applied to residential demand |
| 0x2a633000 | Float32 | Commercial Demand Effect | Factor applied to commercial demand |
| 0x2a634000 | Float32 | Industrial Demand Effect | Factor applied to industrial demand |
| 0x491b3ad5 | Float32 | Health Coverage Radius % Effect | Percentage (from 0 to 200) by which this ordinance affects coverage radius of health buildings |
| 0x891b3ae6 | Float32 | Health Effectiveness vs. Distance Effect | Maps % of coverage distance from a hospital to HQ boost % |
| 0xe91b3aee | Float32 | Health Quotient Boost Effect | Percentage (from 0 to 200%) by which this ordinance affects all HQ values |
| 0xc92d9c7a | Float32 | Health Quotient Decay Effect | Percentage (from 0 to 200%) by which this ordinance affects the rate at which HQ decays |
| 0x092d909b | Float32 | Health Capacity Effect | Percentage (from 0 to 200%) by which this ordinance affects the capacity of hospitals |
| 0xe92d9db4 | Float32 | Health Effectiveness vs. Average Age Effect | Maps average age of a tract to addional HQ boost % |
| 0xa91b3af4 | Float32 | School Coverage Radius % Effect | Percentage (from 0 to 200) by which this ordinance affects coverage radius of schools |
| 0xa91b3afa | Float32 | School Effectiveness vs. Distance Effect | Maps % of coverage distance from a school to EQ boost % |
| 0xa92d9d7a | Float32 | School EQ Boost Effect | Percentage (from 0 to 200%) by which this ordinance affects all EQ values |
| 0x692ef65a | Float32 | School EQ Decay Effect | Percentage (from 0 to 200%) by which this ordinance affects the rate at which EQ decays |
| 0x892d9d02 | Float32 | School Capacity Effect | Percentage (from 0 to 200%) by which this ordinance affects the capacity of schools |
| 0xc91b3b02 | Float32 | School Effectiveness vs. Average Age Effect | Maps average age to EQ boost % |
| 0x8a612fee | Sint32 | Travel Strategy Modifier | For each wealth type (\$-\$\$\$), modifies percentage of travelers using each of the three travel strategies |
| 0x8a67e373 | Float32 | Air Effect by zone type | Effect (multiplier) this ordinance has on air pollution for each zone type |
| 0x8a67e374 | Float32 | Water Effect by zone type | Effect (multiplier) this ordinance has on water pollution for each zone type |
| 0x8a67e376 | Float32 | Garbage Effect by zone type | Effect (multiplier) this ordinance has on garbage for each zone type |
| 0x8a67e378 | Float32 | Traffic Air Pollution Effect | Effect (multiplier) this ordinance has on air pollution generated by traffic |
| 0x2a654100 | Float32 | IR Demand Effect | The effect of this ordinance on Industrial Resource demand, in percent (0.0-100.0) |
| 0x2a654200 | Float32 | ID Demand Effect | The effect of this ordinance on Industrial Dirty demand, in percent (0.0-100.0) |
| 0x2a654300 | Float32 | IM Demand Effect | The effect of this ordinance on Industrial Manufacturing demand, in percent (0.0-100.0) |
| 0x2a654400 | Float32 | IHT Demand Effect | The effect of this ordinance on Industrial High-Tech demand, in percent (0.0-100.0) |
| 0x2a653320 | Float32 | CO\$\$ Demand Effect | The effect of this ordinance on Commercial Office \$\$ demand, in percent (0.0-100.0) |
| 0x2a653330 | Float32 | CO\$\$\$ Demand Effect | The effect of this ordinance on Commercial Office \$\$\$ demand, in percent (0.0-100.0) |
| 0x2a653110 | Float32 | CS\$ Demand Effect | The effect of this ordinance on Commercial Service \$ demand, in percent (0.0-100.0) |
| 0x2a653120 | Float32 | CS\$\$ Demand Effect | The effect of this ordinance on Comercial Service \$\$ demand, in percent (0.0-100.0) |
| 0x2a653130 | Float32 | CS\$\$\$ Demand Effect | The effect of this ordinance on Commercial Service \$\$\$ demand, in percent (0.0-100.0) |
| 0x092d91a3 | Uint32 | (Obs) Health Building types affected | Variable length list of building types affected by this ordinance |
| 0x292d91aa | Uint32 | (Obs) School Building types affected | Variable length list of building types affected by this ordinance |
| 0x28ebbc31 | Uint32 | (Obs) Old Name Key | DO NOT USE |
| 0x28ebbc33 | Uint32 | (Obs) Old Description Key | DO NOT USE |

## Network Properties

### General

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4835c6a4 | Float32 | PivotPointPosition | Relative to left, bottom, far corner of bounding box (x,y,z meters) |
| 0x4835c6a5 | Float32 | BoundingBox | Dist (meters) from the pivot pt to left, right, back, front, bottom, top side of model" |
| 0x6a845768 | Uint32 | ModelIsPrelit | If this property is present the game will not apply deform and lighting to the model |
| 0xabe1b5a3 | Bool | BridgeObstruction | This property prevents water automata from crossing under the bridge tile. |

### Bridge

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x482cb441 | Float32 | MinClearance | Min clearance below bridge (meters) |
| 0x482cb442 | Uint32 | NumEndPieces | Number of end pieces |
| 0x482cb443 | Uint32 | EndPieceExemplars | Exemplar ids for end pieces(in order) |
| 0x482cb444 | Uint8 | EndPieceRotations | Model rotations for end pieces |
| 0x482cb445 | Uint32 | RepeatPieceExemplar | Exemplar id for the repeat pieces |
| 0x482cb446 | Uint8 | RepeatPieceRotation | Model rotation for repeat piece |
| 0x482cb447 | Uint32 | SupportInterval | Number of cells between supports |
| 0x482cb448 | Uint32 | NumSupportPieces | Number of support pieces(count one side only) |
| 0x482cb449 | Uint32 | SupportPieceExemplars | Exemplar ids for support pieces(start at pillar) |
| 0x482cb44a | Uint8 | SupportPieceRotations | Model rotations for support pieces |
| 0x482cb44b | Float32 | EndPieceSpanLocations | Dist from top the two spans of each end piece are |
| 0x482cb44c | Float32 | ColumnTopPosForSupportPieces | Dist from pivot point to the top of concrete column (-ve for no column) |
| 0x482cb44d | Float32 | ColumnTopPosForEndPieces | Dist from pivot point to the top of concrete column (-ve for no column) |
| 0x482cb44e | Float32 | SupportColumnCorners | (x,z) corresponding to the 4 corners of the support column w.r.t column center |
| 0x482cb44f | Bool | CanWorkAsLandBridge | Set to true if this bridge can work as land bridge |
| 0x482cb450 | Bool | CanWorkAsWaterBridge | Set to true if this bridge can work as water bridge |
| 0x482cb455 | Float32 | MinHold | The lowest suspend wire can get in the middle |
| 0x482cb456 | Float32 | MinEndHold | The lowest suspend wire can get at the ends (leave it at 0 please) |
| 0x482cb457 | Float32 | PylonsHeight | Pylons height (meters) |
| 0x482cb458 | Uint32 | MinSpan | The shortest possible bridge of this type (tiles) |
| 0x482cb459 | Uint32 | EndSupportInterval | Number of cells between supports at the ends of the bridge |
| 0x482cb45a | Uint32 | MinPylons | Minimal number of pylons |
| 0x482cb45b | Uint32 | MaxPylons | Maximal number of pylons |
| 0x482cb45c | Uint32 | WireMainTexId | Texture ID for suspension wire |
| 0x482cb45d | Uint32 | WireTileTexId | Texture ID for vertical suspension wires |
| 0x482cb45e | Float32 | MainPylonCorners | (x,z) corresponding to the 4 corners of the pylon w.r.t pylon center |
| 0x482cb45f | Uint32 | BridgeWidth | Bridge width in tiles (defaults to 1) |
| 0x482cb467 | Uint32 | MaxSpan | The longest possible bridge of this type (tiles) |
| 0x482cb468 | Float32 | CeilingHeight | Distance from road top to ceiling of water passage below bridge tiles. |
| 0x482cb469 | Float32 | CableStayedFrontAnchors | 3D start and end (x,y,z) of cable attachments on front side of pylon. |
| 0x482cb46a | Float32 | CableStayedRearAnchors | 3D start and end (x,y,z) of cable attachments on rear side of pylon. |
| 0x482cb46b | Uint32 | CableStayedWireTexture | Instance ID of texture to use for cable-stayed bridge wires. |
| 0x482cb46c | Float32 | CableStayedWireThickness | Thickness of cable-stayed wires in meters. |
| 0x482cb46d | Float32 | CableStayedSpanAnchors | Start and end positions for cable-stayed bridge wires on the span, relative to the pylon." |
| 0x482cb46e | Uint32 | CableStayedWireCount | The number of wires on one side of a pylon on a cable-stayed bridge. |
| 0x482cb46f | Uint32 | Bridge Image Key | Group and instance ID for preview image of bridge. |
| 0x482cb470 | Uint32 | Bridge Costs | One-time and per-tile costs for bridge, in simoleons. |
| 0x482cb471 | Float32 | WireTilingUnit | Height of a repeating wire tile for suspension bridges. |
| 0x482cb472 | Float32 | Bridge height bias | Vertical displacement for all models in a bridge. |
| 0x482cd460 | Float32 | SuspensionWireBase | Offset of suspension wire base |
| 0x482cd461 | Float32 | SuspensionWireInside | Offset of suspension wire inside the bridge tile |
| 0x482cd462 | Float32 | SupportColumnBase | Offset of pylon base |
| 0x482cd463 | Float32 | MinAltitudeAboveWater | Minimum estimated elevation above water |
| 0x482cd464 | Float32 | MaxAltitudeAboveWater | Maximum estimated elevation above water |
| 0x482cd465 | Float32 | MinEndIntervalFraction | Force pylon-to-end distance to be at least some% of pylon-to-pylon distance. |
| 0x482cd466 | Uint32 | Bridge Name Key | Group and instance ID for string name of bridge. |

### Miscellaneous

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x879d12e7 | Float32 | MaxSlopeAlongNetwork | Range: \[0.0 - 90.0\] |
| 0x279d1707 | Float32 | MaxSlopeOnNetworkSide | Range: \[0.0 - 90.0\] |
| 0x07b36c71 | Float32 | MaxNetworkSlopeChange | Range: \[0.0 - 90.0\] |
| 0xc7b36ca4 | Float32 | MaxTerrainHtIncrease | How much can terrain be raised during network placement \[0.0 - 100000.0\] |
| 0xc7b36ca5 | Float32 | MaxTerrainHtDecrease | How much can terrain be lowered during network placement \[0.0 - 100000.0\] |
| 0xc804dd86 | Float32 | MaxNetworkHtAdjustment | Range: \[0.0 - 100000.0\] |
| 0xc804dd87 | Float32 | MinTerrainSlopeForTunnelStart | Min terrain slope to trigger tunnel placement |
| 0xc804dd88 | Float32 | MaxTunnelSlope | Maximum slope of tunnel (in degrees) |
| 0xc804dd89 | Float32 | MaxDisplacementBeyondRefPlane | Maximum amount (in meters) by which a network vertex is allowed to move beyond reference plane |
| 0xc804dd90 | Bool | UseFreehandMode | Use freehand mode of placement (i.e., anchor points freeze) |
| 0xc804dd91 | Uint32 | NumFramesBetweenAnchorPtFreeze | \[deprecated\] Number of frame updates between the freezing of successive anchor points |
| 0xc804dd92 | Uint32 | NumCellsBetweenAnchorPtFreeze | Min number of cells between successive anchor points in different zooms |
| 0xc804dd93 | Float32 | MaxDistFromTerrain | How far away from the terrain is the network allowed to be \[0.0 - 100000.0\] |
| 0xc804dd94 | Float32 | MaxRetainingWallHt | Max height of the retaining walls \[0.0 - 100000.0\] |
| 0xc804dd95 | Float32 | MaxPylonHt | Max height of the supporting pylons \[Reating wall ht - 100000.0\] |
| 0xc804dd96 | Float32 | MaxHtDiffBetweenLandBridgeEnds | Max allowed terrain height diff between the two ends of land bridges |
| 0xc804dd97 | Bool | SmoothenOnlyConnectedTiles | Smoothen only those tiles that are connected to the segment being placed |
| 0xc804dd98 | Uint32 | numSmoothingProgressionSteps | Number of times we attempt expanding the smoothing region before giving up |
| 0xc804dd99 | Uint32 | distAddedPerSmoothingProgressionStep | How much (in cells) does the smoothing region expand in each smoothing progression step |
| 0xc804dd9a | Float32 | networkHtChangeThatRequiresFixing | If an existing network moves by less than this, we do not attempt to fix it (for efficiency) |
| 0xc804dd9b | Uint32 | TimeBetweenAnchorPtFreeze | Time in milliseconds between the freezing of successive anchor points |
| 0xa96e5641 | Float32 | Underground Trench Floor Depth | Default depth of underground network trench floor below terrain |
| 0x496e564c | Float32 | Underground Piece Depth | Default depth of underground network piece below terrain |
| 0x096e5653 | Float32 | Underground Intersection Height | Default height above trench floor to place intersectons |
| 0x496e5a36 | Bool | Use Pipe Depth | If false, normal pipe pieces are placed as per intersections |
| 0xe974eaa1 | Uint32 | NetworkTextureId | Id of the network texture for which it is OK to have pylon/retaining wall |
| 0xe974eaa2 | Uint32 | ConnectedVerts | Pairs of cell vertices connected by retaining walls / side flaps |
| 0xe974eaa3 | Float32 | PylonCornerXZs | (x,z) corresponding to the 4 corners of the pylon w.r.t cell center |
| 0xe974eaa4 | Uint32 | TunnelResourceIds | Model resource id(s) for tunnel piece(s) |
| 0xe974eaa5 | Uint32 | TunnelModelRotations | Tunnel model rotations |
| 0xe974eaa6 | Float32 | TunnelModelHeights | Tunnel piece model heights |
| 0xe974eaa7 | Uint32 | Special Pylon Model Id | Pylon model exemplar instance used by some networks (can be single instance or one per zoom) |
| 0x4a270db0 | Float32 | Construction Crew Time | Number of seconds the construction crew will spend per tile while building network |
| 0x4a270e94 | Float32 | Construction Crew Vehicle Speed | Speed of construction crew vehicles in meters/second |
| 0x4a271248 | Uint32 | Construction Crew Lead Vehicle Instance | Instance ID of construction crew lead vehicle |
| 0x4a27124f | Uint32 | Construction Crew Follow Vehicle Instance | Instance ID of construction crew follow vehicle |
| 0x4a275748 | Uint32 | Construction Crew Vehicle Path Type | Type of path used by construction crew vehicles (0=None, 1=Auto, 2=Ped, 3=Train, 4=Subway |
| 0x4a2d49b9 | Uint32 | Simolean Cost Per Tile | Cost to create a tile of network using this tool |
| 0x8a2d49ea | Uint32 | Simolean Cost Per Bridge Tile | Cost to create a bridge tile of network using this tool |
| 0x8a2d49f0 | Uint32 | Simolean Cost Per Tunnel Tile | Cost to create a tunnel tile of network using this tool |
| 0x6a2d49f4 | Float32 | Simolean Cost Per Meter Displaced | Cost to raise/lower one vertex one meter when using this tool |
| 0xea86e3b5 | Uint32 | Simolean Cost Per Tile to Demolish | Cost to demolish a tile of network using this tool |

## Hidden

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x489b6974 | Uint32 | Test res key table | Test for Resource key table editor |
| 0x07af514b | Uint32 | ResMan Registered Groups | Specifies a group ID registered with the resource manager |

## Terrain

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x48cd7b20 | Float32 | MaxNormalTerrainHeight | Max normal height in fractally generated terrains, for different city size choices |
| 0x48cd7b21 | Float32 | SeaLevel | Sea level (meters) |
| 0x48cd7b22 | Float32 | MinRegularHtFactor | Factor governing the min ht for regular terrain |
| 0x48cd7b23 | Float32 | MaxRegularHtFactor | Factor governing the max ht for regular terrain |
| 0x48cd7b24 | Float32 | MinMountainHtFactor | Factor governing the min ht for mountain terrain |
| 0x48cd7b25 | Float32 | MaxMountainHtFactor | Factor governing the max ht for mountain terrain |
| 0x48cd7b26 | Float32 | MaxTerrainHeight\|Maximum altitude of a terrain vertex |  |
| 0x48cd7b27 | Float32 | MinTerrainHeight | Minimum altitude of a terrain vertex |
| 0x48cd7b28 | Float32 | ImageImportScaleFactor | How many meters correspond to one unit of gray scale value in image |
| 0x48cd7b2a | Float32 | DefaultTerrainHeight | Default terrain height for new city (meters) |
| 0x48cd7b30 | Float32 | TemperatureRangeFactor | Factor governing the max temperature range for texture assignment |
| 0x48cd7b31 | Float32 | WaterProximityRangeFactor | Factor governing the max water proxmity range for texture assignment |
| 0x48cd7b40 | Uint32 | NumInitialErosionPasses | Number of erosion passes at initial terrain creation time |
| 0x48cd7b41 | Uint32 | NumHydraulicIterationsPerInitialErosionPass | Number of hydraulic erosion iterations in each initial erosion pass |
| 0x48cd7b42 | Uint32 | NumWindIterationsPerInitialErosionPass | Number of wind erosion iterations in each initial erosion pass |
| 0x48cd7b43 | Float32 | SeaLevelChangeDueToWaterSlider | The sea level change range (meters) corresponding to the water slider, for diff city sizes |
| 0x48cd7b50 | Uint32 | MinCellsInUsefulFlatArea | Do not auto flatten it |
| 0x48cd7b51 | Float32 | MaxHtChangeToFlattenFactor | Controls the extent of height change allowed in auto-flattening |
| 0x48cd7b52 | Float32 | MaxTerraceAltitudeFactor | Controls the maximum altitude upto which auto-flattening gets done |
| 0x48cd7b53 | Float32 | MinTerraceAltitudeFactor | Controls the lowest altitude at which terraces get created |
| 0x48cd7b54 | Uint32 | AutoFlatAreaEdgeSmootheningRadius | To what distance (in cells) around an auto-flattened area we do smoothing |
| 0x48cd7b60 | Uint32 | MinShoreCliffSize | Minimum number of shore vertices in a shore cliff |
| 0x48cd7b61 | Float32 | MinShoreCliffCandidateHt | Minimum pre-existing ht difference at shore for it to be considered for turning into a cliff |
| 0x48cd7b62 | Float32 | MinShoreCliffHt | Minimum ht above sea level at a shore cliff (after cliff creation) |
| 0x48cd7b63 | Float32 | MaxShoreCliffHt | Maximum ht above sea level at a shore cliff (after cliff creation) |
| 0x48cd7b64 | Uint32 | MaxShoreCliffSize | Maximum number of shore vertices in a shore cliff |
| 0x48cd7b65 | Float32 | MaxNormalYForCliff | A face is considered cliff if the y-component of its normal is less than this |
| 0x48cd7b70 | Float32 | MinSeaLevel | Minimum sea altitude |
| 0x48cd7b71 | Float32 | MaxSeaLevel | Maximum sea altitude |
| 0x48cd7b72 | Float32 | SeaRaiseLowerAmount | Extent by which the sea level is raised/lowered for each player click |
| 0x48cd7b73 | Float32 | TerrainRaiseLowerAmount | Extent by which the terrain level is raised/lowered each time raise/lower menu is selected |
| 0xa9c283d0 | Uint8 | MaxBeachWidth | How far from water (in cells) does the beach extend |
| 0xa9c283d1 | Float32 | MaxBeachAltitude | How high above the sea level(meters), does the beach extend |
| 0x48cd7b80 | Uint8 | AutoFlattenUponCreation | Run auto-flatten tool upon initial terrain creation |
| 0x48cd7b81 | Uint8 | ShoreCliffsUponCreation | Run cliff creation tool upon initial terrain creation |
| 0x48cd7ba0 | Float32 | TypicalBrushAngleIncrement | Angle (in degrees) by which the brush rotates between successive applications |
| 0x48cd7bf1 | Uint32 | NumFlowStepsPerWaterErosionBrushApplication | Number of water flow steps in each application of water erosion brush |
| 0x48cd7bf2 | Uint32 | NumWaterErosionIterationsPerInvocation | Number of water erosion steps in each application of water erosion tool |
| 0x48cd7bf3 | Uint32 | NumSmoothingIterationsAfterWaterErosion | Number of smoothing iterations after each application of water erosion tool |
| 0x48cd7c00 | Float32 | EdgeReconcilliationSmoothingRadiusVsHeightDiff | Specifiess the smoothing radius as a function of height adjustment needed |
| 0x48cd7c01 | Uint32 | EdgeReconcilliationSmoothingIterations | Smoothing iterations for edge reconcilliation |
| 0x48cd7c02 | Float32 | EdgeReconcilliationHtDifferenceThreshold | If the height difference is less than this, don't reconcile |
| 0x497f42a4 | Uint8 | Unwatered Building Color | RGBA color for unwatered buildings in pipe view |
| 0xe97f42b0 | Uint8 | Watered Building Color | RGBA color for watered buildings in pipe view |
| 0xa97f42ce | Uint8 | Watered Terrain Color | RGBA color for watered terrain cells in pipe view |
| 0x097f4c4e | Uint8 | Unwatered Terrain Color | RGBA color for unwatered terrain cells in pipe view |
| 0x297f42b7 | Bool | Draw Unwatered Terrain Cell Color | Determines whether unwatered terrain cells are colored in pipe view |
| 0x89861864 | Uint32 | VolcanicAshLifeTime | How long (microsecs) is the volcanic ash visible on screen |
| 0x89a312c0 | Float32 | TerrainTexTilingFactor | 100 meters of terrain corresponds to this fraction of texture in farthest zoom |
| 0x89a312c2 | Uint32 | TextureRandomizationGridSize | Width of the coarse grid (in terrain cells) where we assign the same texture family member |
| 0x69ac5640 | Float32 | MinWaterDepthForDeepSeaBedTexture | If the water depth exceeds this, we apply deep seabed texture |
| 0x69ac5641 | Float32 | MaxWaterDepthForDeepSeaBedTexture | Upto this water depth we use deep seabed texture for terrain (No texturing beyond that depth) |
| 0x29ab15c0 | Float32 | WaterDepthForMaxAlpha | At this depth (meters), water becomes opaque |
| 0x29ab15c1 | Uint8 | WaterMinAlpha | Min alpha of water |
| 0x29ab15c2 | Float32 | WaterDepthToColorGradientFactor | Number of pixels in the gradient corresponding to each meter of water depth |
| 0x29ab15c3 | Bool | DisplayWaterSurface | Enable/Disable the display of water surface |
| 0x29ab15c4 | Bool | DisplayTerrainSurface | Enable/Disable the display of terrain surface |
| 0x29ab15c5 | Float32 | WaterNightColorAdjustment | Modifications to the r,g,b of water at night" |
| 0x29ab15c6 | Float32 | CityEdgeLayerHeights | Heights (meters) of all but the bottom-most layers on city edge |
| 0x29ab15c7 | Float32 | CityEdgeBrightnessKludgeFactor | Multiplication factor to tune the brightness of cliffs on city edges |
| 0x69db8d00 | Uint32 | TextureUpdateIntervalForTerrainBrushes | Controls how often terrain texture updates happen while applying terrain brushes |
| 0x69db8d01 | Float32 | ModKey1StrengthMultiplier | Controls how the brush strength is modified by the control key |
| 0x69db8d02 | Float32 | ModKey1WidthMultiplier | Controls how the brush strength is modified by the control key |
| 0x69db8d03 | Float32 | ModKey2StrengthMultiplier | Controls how the brush strength is modified by the shift key |
| 0x69db8d04 | Float32 | ModKey2WidthMultiplier | Controls how the brush strength is modified by the shift key |
| 0x69db8d05 | Float32 | ApplicationTimeIntervalForFullBrushStrength | Time interval (secs) between applications to get full brush strength |

## Lava

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x69987e60 | Float32 | LavaColorGradientMapFactor | Number of pixels in color gradient corresponding to every meter of lava depth |
| 0x69987e61 | Float32 | LavaMaxFlowRate | Higher the viscosity, lower should this number be. |
| 0x69987e62 | Float32 | LavaHtDiffForMaxFlowRate | Lava height differential at which the max flow rate is reached |
| 0x69987e63 | Float32 | LavaLiquidToSolidConversionFactor | When unit amount of lava solidifies, it increases the terrain height by this much |
| 0x69987e64 | Uint8 | LavaMinAlpha | Min alpha for lava |
| 0x69987e65 | Float32 | LavaMinAlphaDepth | When the lava depth is less than this, we set alpha to be LavaMinAlpha |
| 0x69987e66 | Float32 | LavaMaxAlphaDepth | If lava depth is more than this, it becomes opaque (i.e., max alpha) |
| 0x69987e67 | Float32 | LavaScorchedTerrainDecalSize | Width of scorched terrain decal (meters) |
| 0x69987e68 | Float32 | LavaUnderWaterSolidificationMultiple | Solidification rate under water this many times that over land |
| 0x69987e69 | Float32 | LavaDepthBurnThreshold | The lava depth at which occupants will catch on fire |
| 0x69987e6a | Float32 | LavaDepthDeepFryThreshold | The lava depth at which occupants will instantly burn down |
| 0x69987e6b | Uint32 | LavaAnimationFrameDuration | Duration of each lava texture animation frame (microsecs) |
| 0x69987e6c | Float32 | LavaMinAmountForDepositToHappen | If lava amount is less than this, we don't deposit it (We simply dry it up!) |
| 0x69987e6d | Uint32 | LavaScorchDecalLifeTime | Life time of scorch decal(microsecs) |
| 0x69987e6e | Float32 | LavaScorchDecalFadeInTime | Fade in time (Secs) of scorch decal |
| 0x69987e6f | Float32 | LavaScorchDecalFadeOutTime | Fade out time (Secs) of scorch decal |

## Water

### Water Ripples

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x491c9c00 | Bool | RipplesEnabled | Enable/disable ripples |
| 0x491c9c01 | Uint32 | RippleMinShoreSizeForPlacement | Place ripples only if the shore is these many cells long |
| 0x491c9c02 | Float32 | RippleQuadWidth | Approximate width of the quads along the ribbon axis (meters) |
| 0x491c9c03 | Float32 | RippleLandVertexHtAboveSeaLevel | Land side of the ribbon is keptabove sea level to get ripple washing the beach effect |
| 0x491c9c04 | Float32 | RippleTextureUIncrementPerQuad | What portion of the texture corresponds to each quad |
| 0x491c9c05 | Float32 | RippleWaterSideRibbonWidth | Dist (meters) from ribbon center to the quad edge on water side |
| 0x491c9c06 | Float32 | RippleLandSideRibbonWidth | Dist (meters) from ribbon center to the quad edge on land side |
| 0x491c9c07 | Uint32 | RippleMicroSecsPerFrame | Microseconds spent in each frame of animation |
| 0x491c9c08 | Uint8 | RippleLandVertexAlpha | Alpha values for the ribbon vertices on the land side |
| 0x491c9c09 | Uint8 | RippleWaterVertexAlpha | Alpha values for the ribbon vertices on the water side |
| 0x491c9c0a | Float32 | RippleWaterSideRibbonWidthVariation | Factor governing the variation of the ribbon width \[0-1\] |
| 0x491c9c0b | Float32 | RippleConcavityThresholdAngle | If the variation in ripple tangent direction is more than this, we break the ripple there |
| 0x491c9c0c | Uint32 | RippleTerrainUpdateAreaThreshold | If the area (square cells) of terrain edits exceeds this, ripples get reevaluated |
| 0x491c9c0d | Uint32 | RippleAlphaIncrementSteps | On the edges of the ripples, alpha increments over these many steps to reach its max |

### Water Waves

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x6932dc00 | Float32 | DistFromShoreToWaveStartLocation | Distance (meters) from the shore to the starting location of waves |
| 0x6932dc01 | Float32 | WaveMinProductionInterval | Min time (sec) between the production of successive waves |
| 0x6932dc02 | Float32 | WaveMaxProductionInterval | Max time (sec) between the production of successive waves |
| 0x6932dc03 | Float32 | WaveInnerRadius | Inner radius (meter) of the wave arc |
| 0x6932dc04 | Float32 | WaveOuterRadius | Outer radius (meter) of the wave arc |
| 0x6932dc05 | Float32 | WaveArcAngle | Arc angle (degrees) for the wave |
| 0x6932dc06 | Float32 | WaveMinTimeInState | Min time (sec) the wave spends in each of the states |
| 0x6932dc07 | Float32 | WaveMaxTimeInState | Max time (sec) the wave spends in each of the states |
| 0x6932dc08 | Float32 | WaveInitialMoveSpeed | Initial movement speed (meter/sec) of the wave |
| 0x6932dc09 | Float32 | WaveInitialExpandSpeed | Initial expansion speed (meter/sec) of the wave |
| 0x6932dc0a | Float32 | WaveMinMoveSpeed | Min movement speed (meter/sec) of the wave |
| 0x6932dc0b | Float32 | WaveMinExpandSpeed | Min expansion speed (meter/sec) of the wave |
| 0x6932dc0c | Float32 | WaveMaxMoveSpeed | Max movement speed (meter/sec) of the wave |
| 0x6932dc0d | Float32 | WaveMaxExpandSpeed | Max expansion speed (meter/sec) of the wave |
| 0x6932dc0e | Float32 | WaveMinExpandAcceleration | Min acceleration of expansion in each of the states |
| 0x6932dc0f | Float32 | WaveMaxExpandAcceleration | Max acceleration of expansion in each of the states |
| 0x6932dc10 | Float32 | WaveMinMoveAcceleration | Min acceleration of movement in each of the states |
| 0x6932dc11 | Float32 | WaveMaxMoveAcceleration | Max acceleration of movement in each of the states |
| 0x6932dc12 | Uint32 | MaxWaves | Maximum number of waves in the city |
| 0x6932dc13 | Float32 | InterWaveGap | Gap (meters) between two waves |
| 0x6932dc14 | Float32 | WaveMaxOrientationDifference | Maximum difference in the orientation of different waves |

### Water Shimmer

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xa91cbe00 | Float32 | ShimmerMinQuadWidth | Min quad widths (meters) in different zooms |
| 0xa91cbe01 | Float32 | ShimmerMaxQuadWidth | Max quad widths (meters) in different zooms |
| 0xa91cbe02 | Uint32 | ShimmerQuadDensity | Number of shimmer quads to have if all of a 256x256 happenned to be water |

## Terrain Textures

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x09c2aef0 | Float32 | TextureBlendStrength | Higher this value, the more weightage this texture gets while blending with others |
| 0x09c2aef3 | Float32 | Z0_TextureSpreadCurve | Specifies how does the texture strength fall off with distance |
| 0x09c2aef4 | Float32 | Z1_TextureSpreadCurve | Specifies how does the texture strength fall off with distance |
| 0x09c2aef5 | Float32 | Z2_TextureSpreadCurve | Specifies how does the texture strength fall off with distance |
| 0x09c2aef6 | Float32 | Z3_TextureSpreadCurve | Specifies how does the texture strength fall off with distance |
| 0x09c2aef7 | Float32 | Z4_TextureSpreadCurve | Specifies how does the texture strength fall off with distance |

## Brushes

### Brush Categories

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8a3143b7 | Uint32 | CategoryGodMisc | Brush belongs to god mode, miscellaneous category |
| 0x2a3143d7 | Uint32 | CategoryMayorMisc | Brush belongs to mayor mode, miscellaneous category |
| 0x6a33d682 | Uint32 | CategoryGodMountain | Brush belongs to god mode, mountain category |
| 0xea33d694 | Uint32 | CategoryGodValley | Brush belongs to god mode, valley category |

### Brush UI Elements

| Property No. | Type   | Name             | Description                         |
|--------------|--------|------------------|-------------------------------------|
| 0xaa2ed800   | Uint32 | UIActiveEffectID | UI effect in active state           |
| 0xaa2ed801   | Uint32 | UIIdleEffectID   | UI effect in idle state             |
| 0xaa2ed802   | Uint32 | UIActiveIconID   | Icon effect in active state         |
| 0xaa2ed803   | Uint32 | UIIdleIconID     | Icon effect in idle state           |
| 0xaa2ed804   | Uint32 | UIActiveCursorId | Hardware cursor ID for active state |
| 0xaa2ed805   | Uint32 | UIIdleCursorId   | Hardware cursor ID for idle state   |

### Brush Components

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8a020200 | Uint32 | Comp1TextureId | Component1: Texture id |
| 0x8a020201 | Bool | Comp1AlignedWithMouseMoveDirection | Component1: should be aligned with the mouse movement direction |
| 0x8a020202 | Float32 | Comp1Width | Component1: zoom specific widths |
| 0x8a020203 | Float32 | Comp1Strength | Component1: zoom specific brush strengths |
| 0x8a020204 | Uint8 | Comp1BaseTextureVal | Component1: Base texture value (Raise/lower if value is more/less than this) |
| 0x8a020205 | Uint32 | Comp1OperationId | Component1: Operation id |
| 0x8a020206 | Uint32 | Comp1DecalTextureId | Component1: Decal texture id for paint brush |
| 0x8a020207 | Float32 | Comp1MaxDecalRotation | Component1: Max rotation of decal texture (degrees) |
| 0x8a020208 | Uint32 | Comp1MaxPlacementsPerCell | Component1: Max \# of effects/decals placed in a cell during a scrubbing session |
| 0x8a020209 | Uint32 | Comp1IDOfEffectToPlace | Component1: (group id, instance id) of the effect to place" |
| 0x8a020300 | Uint32 | Comp2TextureId | Component2: Texture id |
| 0x8a020301 | Bool | Comp2AlignedWithMouseMoveDirection | Component2: should be aligned with the mouse movement direction |
| 0x8a020302 | Float32 | Comp2Width | Component2: zoom specific widths |
| 0x8a020303 | Float32 | Comp2Strength | Component2: zoom specific brush strengths |
| 0x8a020304 | Uint8 | Comp2BaseTextureVal | Component2: Base texture value (Raise/lower if value is more/less than this) |
| 0x8a020305 | Uint32 | Comp2OperationId | Component2: Operation id |
| 0x8a020306 | Uint32 | Comp2DecalTextureId | Component2: Decal texture id for paint brush |
| 0x8a020307 | Float32 | Comp2MaxDecalRotation | Component2: Max rotation of decal texture (degrees) |
| 0x8a020308 | Uint32 | Comp2MaxPlacementsPerCell | Component2: Max \# of effects/decals placed in a cell during a scrubbing session |
| 0x8a020309 | Uint32 | Comp2IDOfEffectToPlace | Component2: (group id, instance id) of the effect to place |
| 0x8a020400 | Uint32 | Comp3TextureId | Component3: Texture id |
| 0x8a020401 | Bool | Comp3AlignedWithMouseMoveDirection | Component3: should be aligned with the mouse movement direction |
| 0x8a020402 | Float32 | Comp3Width | Component3: zoom specific widths |
| 0x8a020403 | Float32 | Comp3Strength | Component3: zoom specific brush strengths |
| 0x8a020404 | Uint8 | Comp3BaseTextureVal | Component3: Base texture value (Raise/lower if value is more/less than this) |
| 0x8a020405 | Uint32 | Comp3OperationId | Component3: Operation id |
| 0x8a020406 | Uint32 | Comp3DecalTextureId | Component3: Decal texture id for paint brush |
| 0x8a020407 | Float32 | Comp3MaxDecalRotation | Component3: Max rotation of decal texture (degrees) |
| 0x8a020408 | Uint32 | Comp3MaxPlacementsPerCell | Component3: Max \# of effects/decals placed in a cell during a scrubbing session |
| 0x8a020409 | Uint32 | Comp3IDOfEffectToPlace | Component3: (group id, instance id) of the effect to place |
| 0x8a020500 | Uint32 | Comp4TextureId | Component4: Texture id |
| 0x8a020501 | Bool | Comp4AlignedWithMouseMoveDirection | Component4: should be aligned with the mouse movement direction |
| 0x8a020502 | Float32 | Comp4Width | Component4: zoom specific widths |
| 0x8a020503 | Float32 | Comp4Strength | Component4: zoom specific brush strengths |
| 0x8a020504 | Uint8 | Comp4BaseTextureVal | Component4: Base texture value (Raise/lower if value is more/less than this) |
| 0x8a020505 | Uint32 | Comp4OperationId | Component4: Operation id |
| 0x8a020506 | Uint32 | Comp4DecalTextureId | Component4: Decal texture id for paint brush |
| 0x8a020507 | Float32 | Comp4MaxDecalRotation | Component4: Max rotation of decal texture (degrees) |
| 0x8a020508 | Uint32 | Comp4MaxPlacementsPerCell | Component4: Max \# of effects/decals placed in a cell during a scrubbing session |
| 0x8a020509 | Uint32 | Comp4IDOfEffectToPlace | Component4: (group id, instance id) of the effect to place |

### Other

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8a020101 | Float32 | BrushCost | Cost/application at different zoom levels |
| 0x8a020102 | Float32 | BrushWiggleAmount | Cost/application at different zoom levels |
| 0x8a020103 | Uint32 | BrushActiveSound | Sound Id |
| 0x8a020104 | Uint32 | BrushReleaseOneShot | Sound Id |
| 0x48cd7bb2 | Float32 | (Obs) MountainBaseBrushHtFactor | Factor determining the extent of height modification by mountain base brush |
| 0x48cd7bb3 | Float32 | (Obs) MountainRidgeBrushHtFactor | Factor determining the extent of height modification by mountain ridge brush |
| 0x89861863 | Float32 | (Obs) VolcanoBrushAngleIncrement | Angle (in degrees) by which volcano brush rotates between successive applications |

## Lighting

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x29189beb | Float32 | Texture floor | Brightness floor for terrain textures |
| 0x29189bec | Bool | Use environment map | Whether to use art-supplied environment map for lighting |
| 0x29189bed | Bool | Test environment map | Use test environment map to determine orientation |
| 0x29189bee | Float32 | Terrain shadow amount | How much models are shadowed by the terrain |
| 0x29189bef | Bool | Test terrain shadowing | Test model shadowing by terrain |
| 0x29189bf0 | Float32 | Daytime global color | Global lighting value for day time -- everything gets multiplied by this. |
| 0x09b6d6ae | Float32 | Nighttime global color | Global lighting value for night time -- everything gets multiplied by this. |
| 0x29189bf1 | Float32 | Flora terrain shadow amount | How much flora are shadowed by the terrain |
| 0x29189bf2 | Float32 | Model terrain shadow amount | How much models (buildings) are shadowed by the terrain |
| 0x29189bf3 | Float32 | Automata terrain shadow amount | How much automata are shadowed by the terrain |
| 0x29189bf4 | Float32 | Atmospheric scattering colour | The colour the terrain gets tinted by in the distance |
| 0x29189bf5 | Float32 | Atmospheric scattering | How much the terrain gets tinted |
| 0x29189bf6 | Float32 | LightingUpdateDelta | The required change in brightness before the terrain gets updated |
| 0x29189bf7 | Float32 | NightThreshold | The brightness below which night falls |
| 0x085489c8 | Uint32 | Shadow Texture ID | ID of FSH texture to use for flora's shadow |
| 0x085489c9 | Float32 | Shadow offset | Offset of shadow from object center |
| 0x085489ca | Float32 | Shadow size | Size of shadow |
| 0x085489cb | Float32 | Shadow color | Color of shadow |
| 0x085489cc | Float32 | Shadow strength | Strength of flora shadows |
| 0x085489cd | Float32 | Shadow threshold | Mask threshold of flora shadows |
| 0x085489ce | Float32 | Sun direction | Sun direction in degrees, clockwise from Z axis |
| 0x085489cf | Float32 | Sun pitch | Sun pitch in degrees, up from XZ plane |
| 0x085489d0 | Float32 | Hill shadow strength | Strength of hill shadows |
| 0x085489d1 | Float32 | Hill shadow warp | Can be used to bend shadows downwards (below 1) or upwards (above 1) |
| 0x085489d2 | Float32 | Hill shadow fade distance | Depth below the hill shadow at which object shadows fade to nothingness |

## Budget Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x6a9c7718 | Sint64 | Budget: Initial Funds | Starting funds for a new city, by difficult level |
| 0x890e0a99 | Float32 | Budget: MaxTaxRate | Maximum Tax Rate - something like maybe 25% |
| 0x090e0a9f | Sint64 | Budget: MinAllowableFunds | The minimum before you are bankrupt. Usually something like -100,000 |
| 0x490e0aa6 | Sint64 | Budget: BondIncrement | Bonds are issued in values that are of this increment |
| 0x090e0aac | Uint8 | Budget: MaxBonds | The maximum number of outstanding bonds that is allowed |
| 0x890e0ab4 | Sint64 | Budget: MaxBondAmount | The maximum amount of outstanding bond debt that is allowed |
| 0x8a3fb98d | Float32 | Budget: BondInterestRate | Interest applied to principal once and added to total |
| 0x0a3fb9a8 | Uint32 | Budget: BondPaybackMonths | Number of months to payback a bond |
| 0xa9188ef5 | Float32 | Budget: TaxRateOccWeight_R\$ | Multiplier to tweak the relative weighting of the R\$ occupant type's taxes |
| 0xe918c920 | Float32 | Budget: TaxRateOccWeight_R\$\$ | Multiplier to tweak the relative weighting of the R\$\$ occupant type's taxes |
| 0x4918c925 | Float32 | Budget: TaxRateOccWeight_R\$\$\$ | Multiplier to tweak the relative weighting of the R\$\$\$ occupant type's taxes |
| 0xa918c929 | Float32 | Budget: TaxRateOccWeight_Cs\$ | Multiplier to tweak the relative weighting of the CS\$ occupant type's taxes |
| 0x4918c92c | Float32 | Budget: TaxRateOccWeight_Cs\$\$ | Multiplier to tweak the relative weighting of the CS\$\$ occupant type's taxes |
| 0x4918c930 | Float32 | Budget: TaxRateOccWeight_Cs\$\$\$ | Multiplier to tweak the relative weighting of the CS\$\$\$ occupant type's taxes |
| 0x8918c937 | Float32 | Budget: TaxRateOccWeight_Co\$\$ | Multiplier to tweak the relative weighting of the CO\$\$ occupant type's taxes |
| 0x4918c93a | Float32 | Budget: TaxRateOccWeight_Co\$\$\$ | Multiplier to tweak the relative weighting of the CO\$\$\$ occupant type's taxes |
| 0x69a36e40 | Float32 | Budget: TaxRateOccWeight_IResource | Multiplier to tweak the relative weighting of the IResource occupant type's taxes |
| 0xa918c942 | Float32 | Budget: TaxRateOccWeight_IDirty | Multiplier to tweak the relative weighting of the IDirty occupant type's taxes |
| 0x8918c93e | Float32 | Budget: TaxRateOccWeight_IManufacturing | Multiplier to tweak the relative weighting of the IManufacturing occupant type's taxes |
| 0xa9a36e47 | Float32 | Budget: TaxRateOccWeight_IHighTech | Multiplier to tweak the relative weighting of the IHighTech occupant type's taxes |
| 0x8a480df7 | Float32 | Budget: Waning Wealth Property Tax Multiplier | Multiplier applied to a building tax value for each level of difference in wealth level |
| 0x4ac519b8 | Float32 | Budget: Land Value to Simoleans | For each taxable square of the given land value, the number of Simoleans produced |
| 0xebff69e7 | Float32 | Budget: Difficulty Tax Multiplier | Multiplier for tax revenue by difficulty type |
| 0x0c032488 | Float32 | Budget: Initial Tax Rate | Starting tax rate for all developer types, indexed by difficulty type |

## City Obliteration Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x6a5a6700 | Uint32 | Obliterate_ClusterWindowWidth | Width in cells of each demolition cluster window |
| 0x6a5a6701 | Float32 | Obliterate_NumClustersVsTime | Cumulative number of clusters to demolish as a function of time (secs) |
| 0x6a5a6702 | Float32 | Obliterate_SmokeScreenFormationTime | Time (secs) between the creation of Finale effect and our last big wipe-out sweep of the city |

## Automata Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x696e88db | Uint8 | Zone Filter | Zone types compatible with automaton (none == can appear in any zone) |
| 0x296e88e9 | Uint8 | Wealth Filter | Zone wealth values compatible with automaton (none == can appear around any wealth) |
| 0x496e88f1 | Uint8 | Zone Purpose Filter | Zone purpose types compatible with automaton (none == can appear around any purpose) |
| 0xc973c9aa | Uint8 | Layer Filter | Which automata layers this model can appear in |
| 0x09c80416 | Uint32 | Model Resource Key | Model type, group, and instance ID" |
| 0x09c80417 | Uint32 | Auxiliary Model 1 Key (headlights) | Type/Group/Instance ID for headlight/taillight model |
| 0xc9e69af6 | Uint32 | Auxiliary Model 2 Key | Type/Group/Instance for additional model (e.g. flashing lights on emerg. vehicles) |
| 0xec214180 | Uint32 | Auxiliary Model 3 Key | Type/Group/Instance for additional model |
| 0xcc21420d | Uint32 | Auto-load Auxiliary Models | Index (1,2,3,etc.) of auxiliary model to load automatically on Init |
| 0xaa5a9633 | Bool | Ignore Lighting | Automaton should not be lit by the lighting manager |
| 0x2a62d9f3 | Uint32 | Crime Type | Crime sims only - which crime type this model represents |
| 0xea958845 | Uint8 | Anim Loop Count Range | For static (one-shot) sims: How many times automaton will loop through its animation before fading out |
| 0x4b733e12 | String | Automaton Display Name | Player-visible name of this automaton during query |
| 0xcbbba52f | Uint32 | Sound Bank ID | Refers to an .abk file with player-drive sounds |
| 0x8bbd735e | Bool | Conditional Automaton | If true, automaton will be ghosted in the earned vehicle catalog view until an advisor condition is satisfied |
| 0xebfc5e26 | Uint32 | My Sim Wealth Level | 0 = \$, 1 = \$\$, 2 = \$\$\$ |
| 0xebfc5e5e | Uint32 | My Sim Icon Image | Resource ID of the icon to be used in the choose vehicle dialog |
| 0xebfc5fba | Sint32 | My Sim Sort Order | Relative sort ordering in the catalog |
| 0x2c0c922e | Uint32 | MySim Walk Gender \|Male=0, Female=1, used by MySim ped chooser |  |
| 0xec15654a | Float32 | Mayor Limo Money Properties | Cost per second, desirability radius meters, desirability magnitude |
| 0x2c23a3a1 | Uint32 | Final Group Id | Automata group ID which controls the creation and driving properties for this automaton |
| 0xac2bc81c | Uint32 | Shadow Model Key | Model type, group, and instance for shadow model |

## Construction Tuning Exemplar

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x8989ec22 | Float32 | Segment Height | Height of one growth level |
| 0x8989ec23 | Float32 | Post Width | Width of corner posts |
| 0x8989ec24 | Float32 | Scaffold Gap | Gap between scaffold and building |
| 0x8989ec25 | Float32 | Plank Width | Width of the planks that run around the top of the scaffold |
| 0x8989ec26 | Float32 | Plank Texture Scale | How large the plank texture is, in meters |
| 0x8989ec27 | Float32 | Scaffold Texture Scale | How large the scaffold texture is, in meters |
| 0x8989ec28 | Float32 | Girders Texture Scale | How large the top girders texture is, in meters |
| 0x8989ec29 | Float32 | Scaffold Growth Rate | How fast scaffolding goes up in meters per day |
| 0x8989ec2a | Float32 | Scaffold Removal Rate | How fast scaffolding is removed in meters per day |
| 0x8989ec2b | Float32 | Crane Post Width | Width of the post that holds up the crane model |
| 0x8989ec2c | Float32 | Crane Post Gap | Size of gap between the crane post and the scaffold |
| 0x8989ec2d | Float32 | Crane Height Above Scaffold | How far above the scaffold to place the bottom of the crane |
| 0x8989ec2e | Float32 | Crane Rotation Time | Milliseconds to complete one full rotation |

## Automata Tuning Exemplar

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4998c89c | Float32 | Vehicle Density Curve | Maps city population to a multiplier (0.0-1.0) for vehicle density |
| 0x4998c901 | Float32 | Ped Density Curve | Maps city population to a multiplier (0.0-1.0) for ped (sim) density |
| 0x4a511873 | Float32 | Bus Density Curve | Maps city population to a multiplier (0.0-1.0) for bus density |
| 0x0a51188a | Float32 | Freight Train Density Curve | Maps city population to a multiplier (0.0-1.0) for freight train density |
| 0x2a511893 | Float32 | Commute Train Density Curve | Maps city population to a multiplier (0.0-1.0) for commute train density |
| 0xca51189a | Float32 | Freight Truck Density Curve | Maps city population to a multiplier (0.0-1.0) for freight truck density |
| 0x4998c89e | Float32 | Max Vehicles Per Second | Max number of vehicles to cross a tile per second |
| 0x4998c903 | Float32 | Max Peds Per Second | Max number of peds to cross a tile per second |
| 0x8a511dd1 | Float32 | Max Buses Per Second | Max number of buses to cross a tile per second |
| 0xea511de0 | Float32 | Max Freight Trains Per Second | Max number of freight trains to cross a tile per second |
| 0xca511de6 | Float32 | Max Commute Trains Per Second | Max number of commute trains to cross a tile per second |
| 0xca511df2 | Float32 | Max Freight Trucks Per Second | Max number of freight trucks to cross a tile per second |
| 0x4998c89f | Uint32 | Max Vehicles | Maximum number of vehicles at one time |
| 0x4998c900 | Uint32 | Vehicle Min/Max KPH | Minimum and maximum DEFAULT speed for vehicles, in kilometers per hour |
| 0x4998c904 | Uint32 | Max Peds | Maximum number of pedestrianss at one time |
| 0x4998c905 | Uint32 | Ped Min/Max KPH | Minimum and maximum DEFAULT speed for pedestrians, in kilometers per hour |
| 0x4998c908 | Uint32 | Max Aircraft | Maximum number of aircraft at one time |
| 0x4998c90b | Uint32 | Max Watercraft | Maximum number of watercraft at one time |
| 0x4998c90c | Float32 | Commute clock | Maps time of day on 24-hour clock to a percentage of commute automata generated (0.0 - 1.0) |
| 0x4998c90d | Float32 | Bus clock | Maps time of day on 24-hour clock to a percentage of bus automata generated (0.0 - 1.0) |
| 0x4998c90e | Float32 | Freight train clock | Maps time of day on 24-hour clock to a percentage of freight train automata generated (0.0 - 1.0) |
| 0x4998c90f | Float32 | Commute train clock | Maps time of day on 24-hour clock to a percentage of commute train automata generated (0.0 - 1.0) |
| 0x4998c910 | Float32 | Occupant trip clock | Maps time of day on 24-hour clock to a percentage of occupant trip automata generated (0.0 - 1.0) |
| 0x4998c911 | Float32 | Freight truck clock | Maps time of day on 24-hour clock to a percentage of freight truck automata generated (0.0 - 1.0) |
| 0x4998c912 | Float32 | Stop Sign Delay | How long in seconds an automaton will pause at a stop sign |
| 0x4998c913 | Float32 | Street Go Time | How long in seconds traffic coming from secondary streets gets the green light |
| 0x4998c914 | Float3 | Road Go Time | How long in seconds traffic coming from main roads gets the green light |
| 0x4998c915 | Float32 | Avenue Go Time | How long in seconds traffic coming from avenues/boulevards gets the green light |
| 0x4998c916 | Float32 | Fade Time | How long in seconds it takes automata to fade in or out |
| 0x4998c918 | Uint8 | Vehicle Min Zoom Visibility | Lowest zoom level at which vehicles are visible |
| 0x4998c919 | Uint8 | Pedestrian Min Zoom Visibility | Lowest zoom level at which pedestrians are visible |
| 0x4998c91a | Uint8 | Aircraft Min Zoom Visibility | Lowest zoom level at which aircraft are visible |
| 0x4998c91b | Uint8 | Watercraft Min Zoom Visibility | Lowest zoom level at which watercraft are visible |
| 0x4998c91c | Bool | Use 24-hour clock | Automata should base traffic levels on 24-hour clock |
| 0x4998c89d | Uint8 | Active Travel Types | Which travel types are currently visible and simulated by the automata system |
| 0x4998c902 | Uint8 | Vehicle Lifespan Range | Number of cells that occupant-trip vehicles should travel before disappearing |
| 0x4998c909 | Uint8 | Ped Lifespan Range | Number of cells that occupant-trip pedestrians should travel before disappearing |
| 0x4998c90a | Float32 | Occupant Trip Noise Range | Range for random value used to dampen occupancy values when generating occupant trips |
| 0x4998c91d | Uint8 | Occupant Trip Population Radius | How many cells around a road tile the system will check population for occupant trips |
| 0x89aec88b | Float32 | Emergency Vehicle Idle Time | How long in seconds an emergency vehicle will remain idle when repathing or handling event |
| 0x89aec88c | Uint8 | Emergency Vehicle Max Cell Distance | Max distance in cells an emergency vehicle can stop from its dispatch destination |
| 0x89aec88d | Uint8 | Emergency Vehicle Repath Attempts | How many times an emergency vehicle will try to repath to its destination |
| 0x89aec88e | Uint32 | Emergency Vehicle KPH | Default speed for emergency vehicles, in kilometers per hour |
| 0xa9af1e54 | Uint8 | Occupant Trip Zone Filter | Which zone types will generate occupant trips |
| 0xa9af1e55 | Uint8 | Occupant Trip Purpose Filter | Which zone purpose types will generate occupant trips |
| 0x49be9565 | Bool | Drive on Right | DEBUG ONLY - Sims drive on the right side of the road, like proper Americans |
| 0xc9c18eae | Float32 | Moving Van Frequency | How often (0.0-1.0) a moving van will be created in response to a new residence |
| 0xa9d6cc17 | Float32 | Fire Crew Offsets | Offsets (in meters) of fire team from center of engine and director from front of engine |
| 0xa9d6cc18 | Float32 | Fire Crew Competence Pct | Min Percentage (0.0-1.0) of fire team efficiency that will give the super, normal, and incompetent animations |
| 0xc9da95d4 | Float32 | Attraction Threshold | Magnitude of a repulsor or attractor at which peds will break their paths to get away from or closer to it |
| 0x29dd40c1 | Float32 | Path Offset Range for Peds | Minimum (left side) and maximum (right side) range of offset from paths for pedestrians |
| 0x29dd40c2 | Float32 | Path Offset Range for Vehicles | Minimum (left side) and maximum (right side) range of offset from paths for vehicles |
| 0xc9ee640a | Float32 | Grade max angle | Maximum angle (in degrees) of network grade that will change the speed of a vehicle |
| 0xc9ee640b | Float32 | Grade speed multiplier | Percentage that will be added to/subtracted from a vehicle's speed when driving up/down a grade at max angle |
| 0xc9ee640c | Float32 | Fire Crew Max Stream Dist | Max distance between fire and crew for the crew to aim its water stream at it |
| 0xc9ee640d | Uint8 | Emergency Vehicle Clear Radius | Number of tiles around emergency vehicles on which traffic will be removed |
| 0x6a09f62f | Float32 | Crime Sim multiplier | Percentage (0.0-1.0) of actual crimes in a cell that will generate a corresponding crime sim |
| 0x6a09f630 | Uint8 | Sim Prop anim range | Min and Max number of times a one-shot sim will loop through its animation before fading out |
| 0x6a09f631 | Float32 | Crime layer clock | Maps time of day on 24-hour clock to a percentage of crime props generated (0.0 - 1.0) |
| 0xea441c97 | Uint8 | Freight Train Length | Min/max length in cars, including engine, of freight trains |
| 0x8a441c9c | Uint8 | Commute Train Length | Min/max length in cars, including engine, of commuter trains |
| 0x6a440d40 | Uint32 | Train Min/Max KPH | Min/max speed of trains in kilometers per hour |
| 0x8a4efa75 | Float32 | Vehicle Skid | Percentage (0.0 - 1.0) of skid that will be applied to vehicle turns. 0 = clamp to paths |
| 0x2a511cbc | Float32 | Curve speed multiplier | Multiplied by a vehicle's default speed when it goes around a curve |
| 0x0a53fd32 | Uint32 | Sims Per Train Car | How many trips are satisfied by each train car. Determines train length. |
| 0xca5545ea | Uint32 | Vehicle Blur Speed KPH | Speed in KPH at which vehicles will draw motion blur effect. |
| 0x6b42922c | Float32 | Simulation Speed multiplier | Multiplier for automata speed when sim is in slow, medium, fast, and player-drive mode. 1.0 = default speed |
| 0x4bae8fe0 | Float32 | Speed Multiplier by Network | Multiply by default speed on road, rail, highway, street, pipe, powerline, avenue, subway, light rail, monorail, 1-way road, dirt road, ground highway |
| 0x4bae8fe1 | Float32 | Lane Switch Cost | Cost to add per vehicle when deciding whether to switch lanes to pass slower-moving vehicles |
| 0x4bae8fe2 | Float32 | Lane Switch Max Distance | Max distance in meters that a vehicle will switch lanes on a multi-lane network |
| 0xebfb4a0a | Uint8 | Max CSIs | Maximum number of city-situation-indicators that will be visible |
| 0xcc101142 | Float32 | Playerdrive Vehicles Per Second | Desired \# of vehicles per second that will be generated on roads during player-drive |
| 0x6c200139 | Uint32 | Playerdrive Vehicle Max Count | Desired maximum \# of vehicles in the world during player-drive |
| 0x8c3e8185 | Uint32 | Travellers per bus | How many travellers it takes to yield a bus automata |
| 0xcba5895b | Float32 | Spawn/Recall for Streets | a % (0.0-1.0) chance of adding/removing automaton from tile when actual auto count is b% (0.0-1.0) lower/higher than desired. |
| 0xcba5895c | Float32 | Spawn/Recall for Roads | a % (0.0-1.0) chance of adding/removing automaton from tile when actual auto count is b% (0.0-1.0) lower/higher than desired. |
| 0xcba5895d | Float32 | Spawn/Recall for Avenues | a % (0.0-1.0) chance of adding/removing automaton from tile when actual auto count is b% (0.0-1.0) lower/higher than desired. |
| 0xcba5895e | Float32 | Spawn/Recall for Highway | a % (0.0-1.0) chance of adding/removing automaton from tile when actual auto count is b% (0.0-1.0) lower/higher than desired. |
| 0xcba5895f | Float32 | Spawn/Recall for Rail | a % (0.0-1.0) chance of adding/removing automaton from tile when actual auto count is b% (0.0-1.0) lower/higher than desired. |
| 0xcba58a5b | Float32 | Congestion to CPS for Streets | Response curve of congestion vs. expected automata per second on a tile |
| 0xcba58a5c | Float32 | Congestion to CPS for Roads | Response curve of congestion vs. expected automata per second on a tile |
| 0xcba58a5d | Float32 | Congestion to CPS for Avenues | Response curve of congestion vs. expected automata per second on a tile |
| 0xcba58a5e | Float32 | Congestion to CPS for Highway | Response curve of congestion vs. expected automata per second on a tile |
| 0xcba58a5f | Float32 | Congestion to CPS for Rail | Response curve of congestion vs. expected automata per second on a tile |

## Disasters

### Earthquake

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a08c500 | Float32 | QuakeBrushStrengthAtEpicenterVsQuakeIntensity | Brush strength multiplier at epicenter vs. quake intensity |
| 0x4a08c501 | Float32 | QuakeBrushWidthAtEpicenterVsQuakeIntensity | Brush width multiplier at epicenter vs. quake intensity |
| 0x4a08c502 | Float32 | QuakeBrushStrengthVsDistance | Variation of brush strength with distance from epicenter |
| 0x4a08c503 | Float32 | QuakeBrushWidthVsDistance | Variation of brush width with distance from epicenter |
| 0x4a08c504 | Float32 | QuakeDistBetweenEffects | Distance in meters, specifying how far apart we place effects |
| 0x4a08c505 | Float32 | QuakeFaultLineCurviness | Max deviation from a straight fault line |
| 0x4a08c506 | Float32 | QuakeMaxFaultLineSlopeVariation | Max variation (degrees) in the slope of fault line |
| 0x4a08c507 | Float32 | QuakeBrushTravelSpeed | Speed (meters/sec) with which earthquake brush moves |
| 0x4a08c508 | Uint32 | QuakeMicroSecsBetweenShakeEffects | Microsecs between shake effects |
| 0x4a08c509 | Float32 | QuakeDistBetweenAutomataRepulsors | Distance in meters, specifying how far apart we place automata repulsors |

### Volcano

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xea4bc6e4 | Float32 | VolcanoLavaCurveProductionRate | Production Rate for the Flow of VolcanoLava (Input Time in Fraction from \[0, 1\]) |
| 0x4a4bc714 | Float32 | VolcanoLavaCurveSolidifcationRate | Solidification Rate for the Flow of VolcanoLava (Input Time in Fraction from \[0, 1\]) |
| 0xaa4bc72a | Float32 | VolcanoLavaScaleIntensityOfProduction | Multiplying Factor to the Response curve so response curve shape preserves |
| 0x0a4bc742 | Float32 | VolcanoLavaTotalLavaTimeInSecs | Time In Seconds until lava flowing and solidification continues |
| 0x0a4bc752 | Uint32 | VolcanoLavaOrificeRadius | Orifice Size of Lava Flow in Metres |
| 0x6a4bc8ed | Bool | VolcanoLavaShouldLavaFlow | To Allow the flow of lava flow |

### Pipe-Burst

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a08c600 | Float32 | PipeBurstMinLeakTimeBeforeBurst | Min time (secs) from onset of leak until burst happens |
| 0x4a08c601 | Float32 | PipeBurstMaxLeakTimeBeforeBurst | Max time (secs) from onset of leak until burst happens |

### Riot

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xea400620 | Uint32 | Riot, NumStages | Total number of stages |
| 0xea400621 | Uint32 | Riot, SecondsBetweenStages | Number of seconds per stage |
| 0xea400622 | Uint32 | Riot, Controller2Stage | Stage at which second controller gets added |
| 0xea400623 | Uint32 | Riot, SpawnArray | Array of number of new leaders to spawn at each stage |
| 0xea400624 | Float32 | Riot, Protection-vs-Suppression | Maps Police Protection value (0-255) to Riot Suppression( 0=none, 1=riot progression halted, 2+=riot regresses |
| 0xcadb6b3e | Uint32 | Riot, MaxInstances | Maximum number of simultaneous riot instances |
| 0x2adb6b6d | Uint32 | Riot, MaxLeaders | Maximum number of riot leaders created per instance |

### Disaster Creation Parameters

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a08c700 | String | Effect Name | Specifies base name of disaster effect |
| 0x4a08c701 | Uint32 | Manager ID | Specifies the id of the disaster manager to use |
| 0x4a08c702 | Bool | StopPickAtWaterSurface | Mouse pick for disaster trigger should choose water surface instead of terrain bed underneath |
| 0xca821b8c | Uint8 | Go To Zoom Level | Specifies the camera zoom level to use on disaster go to |

### Other

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xa9b6ecd3 | Uint32 | Stage Time | Ticks to next fire stage by stage |
| 0xa9b6ecd4 | Uint32 | Spread Time | Ticks between spread attempts per stage |
| 0xa9b6ecd5 | Uint32 | Spread Radius | In meters beyond occupant/lot boundaries |
| 0xa9b6ecd6 | Float32 | Wind Scalar | Wind effect on spread direction is directly scaled by this |
| 0xa9b6ecd7 | Float32 | Fires / Area (Top) | Number of top fires per unit area |
| 0xa9b6ecd8 | Float32 | Fires / Area (Side) | Number of side fires per unit area |
| 0xa9b6ecd9 | Float32 | Extinguish Rate vs. Protection | The rate at which a fire declines as a function of protection |
| 0xa9b6ecda | Float32 | Percent FireStart vs. Flammability | Maps Flammability(0-255) to percent chance(0-100) of fire starting when ignited |

## Miscellaneous Occupant

| Property No. | Type   | Name           | Description                              |
|--------------|--------|----------------|------------------------------------------|
| 0xaa1dd396   | Uint32 | OccupantGroups | List of groups this occupant belongs to. |

## Network Lot

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xaa120972 | Float32 | NetworkLotConfigPropertyMaxSlopeAllowed | The Max slope this lot will develop on |
| 0xaa120973 | Float32 | NetworkLotConfigPropertyMinSlopeAllowed | The Min slope this lot will develop on |
| 0xc9a5a1be | Uint32 | kPropertyID_LotConfigNetworkTileId | kPropertyID_LotConfigNetworkTileId |
| 0x49d55951 | Uint8 | kPropertyID_NetworkPlacementPattern | kPropertyID_NetworkPlacementPattern |
| 0xec3bd470 | Uint8 | kPropertyID_RotationsAllowed | kPropertyID_RotationsAllowed |
| 0xcc3e4755 | Uint8 | kPropertyID_FlipsAllowed | kPropertyID_FlipsAllowed |

## Data View

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x4a0b47e0 | Uint32 | DataView: Type filter | Occupant types to include or exclude (0=unused). |
| 0x4a0b47e1 | Bool | DataView: Invert filter | If true, the occupant filter is exclusive rather than inclusive. |
| 0x4a0b47e2 | Bool | DataView: Hide zones | If true, zoning decals are hidden. |
| 0x4a0b47e3 | Uint32 | DataView: View level | Specifies a surface or underground view to use. |
| 0x4a0b47e4 | Uint32 | DataView: Color ramp | Color progression to use for data. |
| 0x4a0b47e5 | Uint32 | DataView: Data source | Data overlay to display. |
| 0x4a0b47e6 | Uint8 | DataView: Zone opacity | Override value for undeveloped zone opacity (0-255). |
| 0x4a0b47e7 | Bool | DataView: Interpolate data | If true, data map is interpolated to city cell resolution. |
| 0x4a0b47e8 | Uint32 | DataView: Quantize lots | Force data to be uniform over lots, possibly of a specific type. |
| 0x4a0b47e9 | Uint32 | DataView: Highlight mode | Selects building types for coverage rings and highlights. |
| 0x4a0b47ea | String | DataView: Coverage effect | Specifies visual effect for coverage rings. |
| 0x4a0b47eb | Uint32 | DataView: Custom view | Specifies a CLSID of special code to create a custom view. |
| 0x4a0b47ec | Uint32 | DataView: Maximum scale | Specifies a scaling factor for 16-bit maps. |
| 0x4a0b47ed | Uint32 | DataView: Demand type | Specifies a layer subtype for development layers (R\$, CO\$\$, etc.) |
| 0x4a0b47ee | Uint32 | DataView: Coverage circle color | Enables coverage circles for current highlight type with given color (0xRRGGBB, HTML-style). |
| 0x4a0b47ef | Uint32 | DataView: Highlight color | Shows highlighted buildings on 2D map with given color (0xAARRGGBB). |
| 0x4a0b47f0 | Bool | DataView: Force zones | If true, developed lots will show up as plain zone coloring. |
| 0x4a0b47f1 | Uint8 | DataView: Network vislevel | Sets which networks are visible. |
| 0x4a0b47f2 | Uint32 | DataView: Legends Color | Set Color for legend on Data view |
| 0x4a0b47f3 | Uint32 | DataView: Legends GUIDS | GUID for ledgend Text GroupID, GUID |
| 0x4a0b47f4 | Uint32 | DataView: Legends Header | Selects building types for coverage rings and highlights. |
| 0x4a0b47f5 | Bool | DataView: Show zone map | Displays zone coloring in the 2D map. |
| 0x6b7c5cdd | Uint32 | DataView: Travel Types | List of travel types |

## Model Highlight

| Property No. | Type    | Name           | Description |
|--------------|---------|----------------|-------------|
| 0xea639fb1   | Float32 | No highlight   |             |
| 0xea639fb2   | Float32 | General OK     |             |
| 0xea639fb3   | Float32 | General Not OK |             |
| 0xea639fb4   | Float32 | Create OK      |             |
| 0xea639fb5   | Float32 | Create Not OK  |             |
| 0xea639fb6   | Float32 | Destroy OK     |             |
| 0xea639fb7   | Float32 | Destroy Not OK |             |
| 0xea639fb8   | Float32 | Query OK       |             |
| 0xea639fb9   | Float32 | Query Not OK   |             |

## Graphs

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xaa4c0d1b | Uint32 | Graph type | Type of the graph to be shown (line, bar, etc.) |
| 0xea4aedc6 | Float32 | Graph minimum Y value | Overrides the automatic minimum Y value. |
| 0x6a4aeded | Float32 | Graph maximum Y value | Overrides the automatic maximum Y value. |
| 0x6a4aedef | Float32 | Graph Y tick spacing | Overrides the automatic Y tick spacing. |
| 0x6a4aee40 | Uint32 | Graph Plot data source 1 | Array of GUIDs, one per plot, each representing a data source. |
| 0x6a4aee5f | Uint32 | Graph Plot data source 2 | (Line only) Array of GUIDs, one per plot, each representing a data source. |
| 0x6a4aee68 | Uint32 | Graph Plot combine op | (Line only) Array of ints, one per plot, each representing how data sources 1 and 2 are combined (none, +, -, \*, /). |
| 0x6a4aeedc | Uint32 | Graph Plot label key | Array of ints, one per plot, each representing a localized string key for the label. |
| 0x6a4aeedf | Uint8 | Graph Plot color | Array of RGB triplets, 3 integers per plot, each representing a line color. |
| 0x6a4aeee2 | Float32 | Graph Plot scale | Array of floats, one per plot, which scales the plot by that amount. |
| 0x6a4aeee3 | Uint32 | Graph Plot series | (Bar only) Array of ints, one per plot, each representing which series that plot should be in. |
| 0x6a4aeee4 | Uint8 | Graph Plot series fill color | (Bar only) Array of RGB triplets, 3 integers per series, each representing a fill color for a whole series. |
| 0x6a4aeee5 | Uint8 | Graph Plot series line color | (Bar only) Array of RGB triplets, 3 integers per series, each representing a outline color a whole series. |

## Trend Bar

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0x6a6564f4 | Uint32 | Trend Bar: Data Source | History data source for this trend bar |
| 0x6a6564f6 | Float32 | Trend Bar: Response Curve | Converts from input data source range to {0,1} |

## Audio Tuning

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xca359f17 | Float32 | Audio:ZoomDistances | Distance above ground or sea for microphone position |
| 0x6a359f22 | Float32 | Audio:ZoomDistanceTweaks | Tweak values to nudge each delta |
| 0xea4a7c55 | Float32 | Audio:ZoomDistanceCameraPull | Amount of horiz dist to camera to pull to camera |
| 0x2a35a25f | Float32 | Audio:ZoomScaleFactor | Scale factor for all zoom levels |
| 0x2a36e3cb | Float32 | Audio:ListenerRolloffFactor | How fast sounds rolloff with distance |
| 0x0a36f410 | Float32 | Audio:AmbienceAttentionSpanRadii | Radii for attention per zoom |
| 0x2aa40ccc | Float32 | Audio:ListenerGranularity | Values per zoom controlling update garnularity in meters |
| 0x2a3ff8cd | Uint32 | Audio:AmbienceExemplarIds | Array of exemplars to load |
| 0x6a946a50 | Float32 | Audio:VolumeLimitingCurve | Volume limiting curve |
| 0x0a946a57 | Uint32 | Audio:Max Playing One-Shots | Max playing one-shots |
| 0xaabaa0d3 | Uint32 | Audio:Max Concurrent One-Shots | Max concurrent playing one-shots |
| 0x4a946a5d | Uint32 | Audio:Max Playing Sounds | Max playing sounds |
| 0xea3fbdd7 | Uint32 | Audio:FreshScoreKey | Freshness score key without the class id |
| 0x6a3fbdda | Uint32 | Audio:LoopId | Ambient loop id |
| 0x0a25896b | Uint8 | Audio:ZoomScoreEnable | Bitfield describing which zoom levels score is active for |
| 0xaa3fbdde | Uint8 | Audio:ZoomLoopEnable | Bitfield describing which zoom levels loop is active for |
| 0x2a3fbde1 | Uint32 | Audio:ANDFilters | Filter GUIDs that MUST be satisfied |
| 0x0a410ba0 | Uint32 | Audio:ORFilters | Filter GUIDs any of which must be satisfied |
| 0x2a3fbde5 | Uint32 | Audio:NOTFilters | Filter GUIDs that must NOT be satisfied |
| 0xea3fc42a | Uint32 | Audio:LoopVolume | Loop Volume |
| 0xaa3fc48e | Uint32 | Audio:FreshVolume | Freshness Volume |
| 0x6a3fc4c7 | Uint32 | Audio:FreshSPL | Sound Pressure Level |
| 0x8a552758 | Uint32 | Audio:LayerPositionMode | Layer Position Mode |
| 0x8a70b1a2 | Uint32 | Audio:LayerDensityMode | Layer Density Mode |
| 0x8a3fc5dd | Float32 | Audio:LayerWeight | Priority scalar |
| 0xca4132e9 | Float32 | Audio:Density2FreshPlayCurve | Density to freshness play percentage curve |
| 0x6a4132f3 | Float32 | Audio:Density2FreshVolumeCurve | Density to freshness volume curve |
| 0x6a4132f6 | Float32 | Audio:Density2LoopVolumeCurve | Density to loop volume curve |
| 0x0a4168e1 | Float32 | Audio:(Occupant)GroupRadius | Size of glob for grouping single layer, or occupant |
| 0x0a56212a | Float32 | Audio:CellGroupRadius | Size of glob for grouping cells |
| 0x2a9590de | Float32 | Audio:VolumeAttackLimit | Max amount of full volume to change up per second |
| 0x0a9599bf | Float32 | Audio:VolumeDecayLimit | Max amount of full volume to change down per second |
| 0x8aa039b7 | Uint32 | Audio:LayerPositionSmoothDelta | Layer position smoothing delta limit |
| 0x4aa03db1 | Uint32 | Audio:LayerVolumeSmoothDelta | Layer volume smoothing delta limit |
| 0xcbfb03fa | Float32 | Audio:AEMSMaxVolume | Max volume for AEMS systems |
| 0xcbfb03ff | Float32 | Audio:AEMSMasterFxLevel | Master FX level |
| 0xebfb0404 | Uint32 | Audio:AEMSMasterFxType | Effect type |
| 0x4bfdd955 | Float32 | Audio:AEMSVolumeCurve | AEMS Volume curve |
| 0x8c376d4f | Float32 | Audio:AEMSZoomVolumes | Volume for AEMS system at each zoom level |
| 0x4a7cb3ba | Uint32 | Audio: Min Music Volume Level | Minimum music volume level setting for slider in audio prefs (0-1024) |
| 0x4a7cb3bb | Uint32 | Audio: Min Sound Volume Level | Minimum sound volume level setting for slider in audio prefs (0-1024) |
| 0x4a7cb3bc | Uint32 | Audio: Max Music Volume Level | Max music volume level setting for slider in audio prefs (0-1024) |
| 0x4a7cb3bd | Uint32 | Audio: Max Sound Volume Level | Max sound volume level setting for slider in audio prefs (0-1024) |
| 0x4a7cb3be | Uint32 | Audio: Music Vol Adjustment | Amount by which to adjust music volume such that at 80 percent it matches the sfx volume at full |
| 0x4a7cb3bf | Uint32 | Audio: Music Fadeout Time (ms) | Time (in ms) within which music fades out when switching radio stations |
| 0x8a5e7b50 | Uint32 | Audio: Music Playlist Entry 1 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b51 | Uint32 | Audio: Music Playlist Entry 2 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b52 | Uint32 | Audio: Music Playlist Entry 3 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b53 | Uint32 | Audio: Music Playlist Entry 4 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b54 | Uint32 | Audio: Music Playlist Entry 5 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b55 | Uint32 | Audio: Music Playlist Entry 6 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b56 | Uint32 | Audio: Music Playlist Entry 7 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b57 | Uint32 | Audio: Music Playlist Entry 8 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b58 | Uint32 | Audio: Music Playlist Entry 9 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b59 | Uint32 | Audio: Music Playlist Entry 10 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5a | Uint32 | Audio: Music Playlist Entry 11 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5b | Uint32 | Audio: Music Playlist Entry 12 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5c | Uint32 | Audio: Music Playlist Entry 13 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5d | Uint32 | Audio: Music Playlist Entry 14 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5e | Uint32 | Audio: Music Playlist Entry 15 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b5f | Uint32 | Audio: Music Playlist Entry 16 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b60 | Uint32 | Audio: Music Playlist Entry 17 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b61 | Uint32 | Audio: Music Playlist Entry 18 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b62 | Uint32 | Audio: Music Playlist Entry 19 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b63 | Uint32 | Audio: Music Playlist Entry 20 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b64 | Uint32 | Audio: Music Playlist Entry 21 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b65 | Uint32 | Audio: Music Playlist Entry 22 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b66 | Uint32 | Audio: Music Playlist Entry 23 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b67 | Uint32 | Audio: Music Playlist Entry 24 | Music playlist entry values (Title, Filename, on/off) |
| 0x8a5e7b68 | Uint32 | Audio: Music Playlist Entry 25 | Music playlist entry values (Title, Filename, on/off) |

## My Sim Template

| Property No. | Type | Name | Description |
|----|----|----|----|
| 0xea296f8d | Uint32 | My Sim: Bitmap ID | Specify ID for bitmap in Select-A-My-Sim dialog. |
| 0xea296f8f | String | My Sim: Default name | Specifies default name for My Sim. |
| 0xea296f90 | Uint8 | My Sim: Zodiac Sign | Specify default zodiac sign for My Sim. |
| 0xea296f91 | Bool | My Sim: Is Male | Specify My Sim gender (true=male, false=female) |
| 0xca416b3f | Uint32 | My Sim: Name res key | My sim default name resource key |

## U-Drive-It

| Property No. | Type   | Name                                | Description |
|--------------|--------|-------------------------------------|-------------|
| 0x2BE8FBF3   | UInt32 | UDriveIt Vehicle Panel Exemplar Key |             |
| 0x4BE0D7C4   | UInt32 | UDriveIt Vehicle Icon Key           |             |

## General Properties

| Property No. | Type | LengthType | Length | Value | Name | Description |
|----|----|----|----|----|----|----|
| 0x496e5a36 | Bool |  |  |  | Use Pipe Depth | If false, normal pipe pieces are placed as per intersections |
| 0x6bac0b3e | Uint8 |  |  |  | Path Lookahead Tiles | How many tiles traffic autos should look ahead when determining paths |
| 0x8cb3511f | Uint32 | variable | 1 | 0x00000000 | Occupant Types | Types of occupants |
| 0xcab1ce3a | Sint32 |  |  |  | Subjective Factor Threshold (Min value) | Min value of desirability for subjective factors (pollution,garbage,school,hospital,crime,traffic,triplength). |
| 0xcab1ce3c | Sint32 |  |  |  | Subjective Factor Threshold (Max value) | Max value of desirability for subjective factors (pollution,garbage,school,hospital,crime,traffic,triplength). |
| 0x296E756E | Uint32 |  |  |  | Class ID: Aircraft | Class ID of an aircraft model |
| 0x096E7574 | Uint32 |  |  |  | Class ID: Watercraft | Class ID of a watercraft model |
| 0xc98204b9 | String |  |  |  | Visual effect name 1 |  |
| 0x8A3F1505 | UInt32 |  |  |  | Submenu Key: Zoning: Residential Menu |  |
| 0x8A3F14DC | UInt32 |  |  |  | Submenu Key: Zoning: Commercial Menu |  |
| 0x8A3F1502 | UInt32 |  |  |  | Submenu Key: Zoning: Industrial Menu |  |
| 0xEA5AC496 | UInt32 |  |  |  | Submenu Key: Terrain Effects |  |
| 0x8A3F131B | UInt32 |  |  |  | Submenu Key: Terraforming: CreateFauna Menu |  |
| 0x2BE8E61B | Uint32 |  |  |  | UI Driving Panel | Property is referenced by Instance ID, and points to the User Interface file for the U-Drive-IT Driving Panel" |
| 0x2BE8E6CB | Uint32 |  |  |  | UI Icons(U-Drive-It) | These are the main Icons/Images on the Driving Panel |
| 0xEC1B2361 | Uint32 |  |  |  | UI Status Window | Property is referenced by Instance ID, and points to the User Interface file for the Status Window. The Status Window displays the Control Keys for each of the vehicles" |
| 0x00004005 | UInt32 |  |  |  | Submenu Key: Networks: Highway & Ramps Menu |  |
| 0x00004001 | UInt32 |  |  |  | Submenu Key: Networks: Rails & Depots Menu |  |
| 0x00004002 | UInt32 |  |  |  | Submenu Key: Networks: Miscellaneous Transport Menu |  |
| 0x00004000 | UInt32 |  |  |  | Submenu Key: Networks: Road Menu |  |
| 0x00004003 | UInt32 |  |  |  | Submenu Key: Utilities: Power Plant Menu |  |
| 0x00004004 | UInt32 |  |  |  | Submenu Key: Utilities: Water Plant Menu |  |
| 0x2A49D7CA | UInt32 |  |  |  | Submenu Key: Utilities: Sanitation Menu |  |

## Properties Not in XML

The following exemplar properties were discovered since the most recent update of the XML file, and are therefore not included in it. They are also not currently categorized into one of the above groups of properties.

`0x09C2AEF1 - Texture Size - Texture Size in Pixels for each Zoom`  
`0x09C2AEF2 - Texture Mask Size - Mask Size in Pixels for each Zoom`  
`0x2aa405d3 - De-Loc String - Text De-localization string for Languages. Main Exemplar`  
`0xEA5AC496 - Submenu Key: Terrain Effects`  
`0x2A49D7CA - Submenu Key: Utilities: Sanitation Menu`

## Unknown Properties

The following properties have been found, but their format and purpose have not been decoded. Each is listed by it's Property Number, and the above group to which it most likely belongs.

    CA9B4CA8 - Civic Buildings

    0xa8eaa060 - Ordinance Simulator
    0xa8eaa061 - Ordinance Simulator
    0xa8eaa062 - Ordinance Simulator
    0xa8eaa063 - Ordinance Simulator
    0xa8eaa064 - Ordinance Simulator
    0xa8eaa065 - Ordinance Simulator
    0xa8eaa066 - Ordinance Simulator
    0xa8eaa067 - Ordinance Simulator

    0x0b579c20 ? Background Loader
    0x0b579c2a ? Background Loader
    0x0b579c2b ? Background Loader
    0xCA480831 ? Park Manager (0x0000000000000000)

    0x482CB451 - Bridges
    0x482CB452 - Bridges
    0x482CB453 - Bridges
    0x482CB454 - Bridges (value same as minhold property

    0x6c0700c4 ? Automata Tuning Exemplar
    0xEC06e7cf ? Automata Tuning Exemplar
    0xEC0700C0 ? Automata Tuning Exemplar

    0x6a8a09d2 - Demolition Threshhold
    0x6a8a09d3 - Demolition Threshhold
    0x6a8a09d4 - Demolition Threshhold
    0x6a8a09d5 - Demolition Threshhold

    0x00000000 - MultiProp - 4 purposes: Buildings = String Resource Key for Hover,
                 Motorcycle Bank Robbery =, Helicopter and Spaceship = , Ferries = Ferry Capacity
    0xc973c9a9 - Air_URBAN (Float "1")
