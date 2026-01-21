---
title: NetCon Portal - 3.1 Outage Impact Analysis
description:
permalink:
aliases:
draft: false
date: 2025-09-30
tags:
---
[[./NetCon Portal - 2. Layers|previous]] [[./NetCon Portal - 3.2 Outage Object|next]]

# NetCon Portal - 3.1 Outage Impact Analysis
Outage Impact Analysis is a specific type of trace that highlights part of a network that would be impacted if an outage occurred on the selected feature.

**Start action**:
- Start Outage Analysis from a location (button on the Outage Analysis & Monitor panel or in the context menu)
- Start Outage Analysis from an area (button on the Outage Analysis & Monitor panel or in the context) 
- Start Outage Analysis from a selected feature, e.g. pipe (button on the Outage Analysis & Monitor panel or in the context)

**Output**:
- Visual: 
	- Green-colored buffered area of a part of a network that is impacted by the potential outage
	- Blue-colored circles highlighting operatable barriers (e.g. valves to close)
- Data displayed in Query result dialog:
	- Service Points (i.e. end customers) affected by the potential outage
	- All operatable barriers related to the resulting outage

![[../../Zimages/Outage_impact_analysis.png|Outage_impact_analysis.png]]
## Outage Analysis From Location
For this action, users are prompted to enter a point geometry. Place on an existing object (e.g. a pipe). Connection records in a small area around the targeted location will be selected and used for the trace. Usually, only one Connection ID is selected as a starting point. As a result, only one operatable part of the network is returned in the trace. 
## Outage Analysis From Area
For this action, users are prompted to enter an area geometry. Every Connection record in the area is selected. This often returns multiple operatable parts of the network as a result of the trace. 
## Outage Analysis From Selected Feature
After selecting a feature on the map (e.g. a pipe), this function will become available on the Outage Analysis panel or on the context menu. This function gets all Connection records where AssetID = ID of the selected feature. For line features it will likely be many. 
## Clear Analysis
This action clears visual layers from the map and data from the Query result dialog. 
## Re-run Outage Analysis 
This action runs Outage Impact Analysis trace is from an existing Outage object with stored (pre-defined) connection ID values.