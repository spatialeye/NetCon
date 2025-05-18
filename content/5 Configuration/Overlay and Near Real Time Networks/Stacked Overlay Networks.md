---
title: Stacked Overlay Networks
description: 
permalink: 
aliases: 
draft: false
date: 2025-03-12
tags: 
---
[[./Overlay Networks for Data Quality|previous]] [[./Distribute Overlay Networks Architecture|next]]
# Stacked Overlay Networks

> [!Tip] Overlay Networks can be stacked
> It is possible to have an Overlay Network on top of another Overlay Network, just as well as on top of a normal Network. 


Other examples of Overlay Networks applications are:
* Network reductions (morphing graph structures into equivalent or subsets)
* Near Real Time barrier status;
* NetPlan future network plans;
* Periodic roll forward to do an update of the connections registered in the GIS.

These examples can all occur at the same time; if so, their relationship and data flow is as follows:

```mermaid
---
title: Overlay networks architecture
---
flowchart  
	sourceGIS@{ shape: cyl, label: "GIS connections" }
	sourceRoll@{ shape: cyl, label: "GIS connections update" }
	sourceDQ@{ shape: cyl, label: "Data Quality connections" }
	sourceNRT@{ shape: cyl, label: "Near Real Time connections" }
	sourcePlan@{ shape: cyl, label: "NetPlan connections" }
	NetworkGIS@{ shape: rounded, label: "E/G/W/... network" }
	NetworkRoll@{ shape: rounded, label: "Rollforward network" }
	NetworkDQ@{ shape: rounded, label: "DQ network" }
	NetworkNRT@{ shape: rounded, label: "NRT network" }
	NetworkPlan@{ shape: rounded, label: "Planned network" }
	sourceGIS-->NetworkGIS
	NetworkGIS-->NetworkDQ
	sourceDQ--->NetworkDQ
	NetworkDQ-->NetworkNRT
	sourceNRT---->NetworkNRT
	sourceRoll--->NetworkRoll
	NetworkGIS-->NetworkRoll
	NetworkRoll-.->NetworkGIS
	NetworkDQ-->NetworkPlan
	sourcePlan---->NetworkPlan

```

