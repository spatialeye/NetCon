---
title: Distribute Overlay Networks Architecture
description: 
permalink: 
aliases: 
draft: false
date: 2025-03-12
tags:
  - "#OverlayNetwork"
  - OverlayNetwork
---
[[./Stacked Overlay Networks|previous]]
# Distribute Overlay Networks Architecture

Overlay networks can run on one and the same or separated servers.
In case the load becomes too much, they can be separated out.
For example, the Near Real Time network and Planned network can get their own servers respectively.

```mermaid
---
title: Distributed trace api setup
---
flowchart  
	subgraph Shared infrastructure
		sourceGIS@{ shape: cyl, label: "GIS connections" }
		sourceRoll@{ shape: cyl, label: "GIS connections update" }
		sourceDQ@{ shape: cyl, label: "Data Quality connections" }
		sourceNRT@{ shape: cyl, label: "Near Real Time connections" }
		sourcePlan@{ shape: cyl, label: "NetPlan connections" }
	end
	subgraph Server 1
		NetworkGIS@{ shape: rounded, label: "E network" }
		NetworkRoll@{ shape: rounded, label: "Rollforward network" }
		NetworkDQ@{ shape: rounded, label: "DQ network" }
		NetworkNRT@{ shape: rounded, label: "NRT network" }
		sourceGIS-->NetworkGIS
		sourceDQ--->NetworkDQ
		NetworkGIS-->NetworkDQ
		sourceNRT---->NetworkNRT
		NetworkDQ-->NetworkNRT
		sourceRoll--->NetworkRoll
		NetworkGIS-->NetworkRoll
		NetworkRoll-.->NetworkGIS
	end
	subgraph Server 2
		NetworkGIS2@{ shape: rounded, label: "E network" }
		NetworkRoll2@{ shape: rounded, label: "Rollforward network" }
		NetworkDQ2@{ shape: rounded, label: "DQ network" }
		NetworkPlanST@{ shape: rounded, label: "Planned network tomorrow" }
		NetworkPlanLT@{ shape: rounded, label: "Planned network long term" }
		sourceGIS-->NetworkGIS2
		sourceDQ--->NetworkDQ2
		NetworkGIS2-->NetworkDQ2
		sourcePlan---->NetworkPlanST
		sourcePlan---->NetworkPlanLT
		sourceRoll--->NetworkRoll2
		NetworkGIS2-->NetworkRoll2
		NetworkRoll2-.->NetworkGIS2
		NetworkDQ2-->NetworkPlanST
		NetworkDQ2-->NetworkPlanLT
	end
	ApiDQ((Api DQ))
	ApiNRT((Api NRT))
	ApiPlanST((Api ST Fut))
	ApiPlanLT((Api LT Fut))

	NetworkDQ--->ApiDQ
	NetworkNRT-->ApiNRT
	NetworkPlanST-->ApiPlanST
	NetworkPlanLT-->ApiPlanLT
```
