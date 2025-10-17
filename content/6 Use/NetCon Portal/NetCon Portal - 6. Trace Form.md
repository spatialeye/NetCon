---
title: NetCon Portal - 6. Trace Form
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 5. Barrier State Change|previous]] [[./NetCon Portal - 7. Data Patching|next]]

# NetCon Portal - 6. Trace Form
Trace Form provides the possibility to run any kind of NetCon trace on the network. Instead of operating the traces via API interface, Trace Form combines settings for all traces together and displays the results in the map (rather than just as a JSON export file).  
## Select Existing Template
First page of the Trace form offers the user the option to select an existing template. If there is none saved or if no template is needed, then continue with the default ‘New Template’ option.
![[../../Zimages/Trace_select_template.png|Trace_select_template.png]]
## Setting the trace criteria
The Trace Form offers many criteria to be set up. These are divided into separate categories:
- **General settings**
- **Start criteria**
- **Stop criteria**
- **Block criteria**
- **Yield criteria**

Sections Start, Stop, Block and Yield criteria have the same form fields (used differently of course). Provided values must represent stored values of the a Connection record. More values can be supplied separated by commas. Values are entered manually.  
-	**Connection Id**s: Specific Connection ID where to start, end, block, yield the trace. If feature is selected, then this field is prefilled for the Start criteria section. See [[../../8 API/Parameters/ConnectionIds|ConnectionIds]] for more details. 
-	**Asset Table Name**: Name or names of tables where trace should start, end etc. See [[../../8 API/Results/Connection Or Path Results/AssetTableName|AssetTableName]] for more details. 
-	**Asset Ids**: ID of the source record (usually GIS ID) where trace should start, end etc. See [[../../8 API/Results/Connection Or Path Results/AssetId|AssetId]] for more details. 
-	**Custom Asset Ids**: Any custom ID (e.g. SAP ID) stored on the Connection record can be used as well to set up the trace. See [[../../8 API/Results/Connection Or Path Results/CustomAssetId|CustomAssetId]] for more details. 
-	**Label**: see [[../../8 API/Results/Connection Or Path Results/Label|Label]] for more details
-	**Hierarchy**: requires specific pattern entry, see [[../../8 API/Parameters/AssetHierarchyPattern|AssetHierarchyPattern]] for more details
-	**Specification**: see [[../../8 API/Parameters/SpecificationPattern|SpecificationPattern]] for more details
-	**Commodity**: see [[../../8 API/Parameters/CommodityPattern|CommodityPattern]] for more details

The General settings offer these trace criteria: 
-	**Trace function name**: with options Trace Out (default), Connection, Isolatable Section, Neighbor, Trace Meshed, Trace Path, Outage Impact. 
-	**Trace mode**: with options Normal (default), Down, Mazed, Up, Backwards
-	**Expand paths**: see [[../../8 API/Parameters/ExpandPaths|ExpandPaths]] for more details
-	**Max steps**: maximum number of steps that the trace can do
-	**Max cost**: maximum cost (e.g. a line length) that the trace can do
-	**Max results**: maximum number of results that the trace can return
-	**Block barring connection**: see [[../../8 API/Parameters/BlockBarringConnections|BlockBarringConnections]] for more details
-	**Stop at barring connection**: see [[../../8 API/Parameters/StopAtBarringConnections|StopAtBarringConnections]] for more details

After setting the criteria, hit the Trace button to run the trace and display the results.
## Save trace template
In the General setting section, the name and description of a template can be provided. After hitting the button Save, the name and description along with all the provided trace criteria will be saved into a GeoNotes table TraceTemplate. The trace criteria are stored in the form of a JSON configuration file. Saved templates will become available in the list of templates at the beginning of the Trace Form.