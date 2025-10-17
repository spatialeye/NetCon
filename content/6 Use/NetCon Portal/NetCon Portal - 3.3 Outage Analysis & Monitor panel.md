---
title: NetCon Portal - 5. Outage Analysis & Monitor panel
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 3.2 Outage Object|previous]] [[./NetCon Portal - 4. Observation|next]]

# NetCon Portal - 3.3 Outage Analysis & Monitor panel
Outage Analysis & Monitor panel is an additional panel that holds several action buttons and displays dynamic tabs in relation to outage impact analysis.  

**Buttons**:
- Run Analysis (drop down button) 
	- From Location
	- From Area
	- From Selected Feature (visible only when appropriate feature is selected in the map)
- Clear Analysis... 
- Save Outage

**Tabs** (both tabs are visible only if there are records fitting the queries available): 
- *Current Outages*: list of current outages. The list is generated based on a query “Current Outages” defined in the project file. The query is called every time map is moved.
- *Customers without service*: list of service points that are currently without service (i.e. they got “no flow”). The list is generated based on a query “Customers without service” defined in the project file. The query is called every time map is moved.

![[../../Zimages/Outage_analysis_monitor_panel.png|Outage_analysis_monitor_panel.png]]