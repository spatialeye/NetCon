---
title: Viewer Project Configuration
description:
permalink:
aliases:
draft: false
date: 2025-10-03
tags:
---
[[./NetCon Portal - 2. Admin portal configuration|next]]
# Viewer Project configuration

## Prerequisites

The viewer project that will be used to run NetCon Portal application must properly display source GIS data, i.e. Feature Source is configured correctly, appropriate business collections are populated with the necessary fields, geometry visibility and styles are configured as well. This set up is part of a standard project configuration and will not be described here. 
Additionally, the project should have the connectivity model styles and visibility properly configured. For more details see [[../Configuration - 8. Viewing/Configuration of Connectivity Viewing|Configuration of Connectivity Viewing]].
## Feature sources
The viewer project should list below feature sources. 
### DQ
Feature source of type GeoNotes that holds a table (e.g. NetConConnection_DQ) for storing data patching records. GeoNotes features sources can be hosted on PostGIS, Oracle, MSSQL or GeoPackage DB. The structure of the table is similar to the Connection table. Added fields are: 
- Removed - used by a data patch to mark Connection record as removed, this effectively removes the record from the network calculations
- Outage Reason
- Work Order Id
### Outage
Feature source of type GeoNotes that holds tables for storing Outage and Observation objects. Furthermore, this feature source holds other supporting tables for storing relations between Outage and Connection records.  
#### Outage table
![[../../Zimages/FS_Outage_table.png|FS_Outage_table.png]]
#### Observation
![[../../Zimages/FS_Observation_table.png|FS_Observation_table.png]]
### Sticky Note
Feature source of type GeoNotes that holds the table for storing Sticky Notes. 
![[../../Zimages/FS_Sticky_Note_table.png|FS_Sticky_Note_table.png]]
### Trace Template
Feature source of type GeoNotes that holds the table Trace Template. Trace Template record stores set of trace criteria. 
![[../../Zimages/FS_Trace_template_table.png|FS_Trace_template_table.png]]
### DQ remove table
Feature source of type GeoPackage that loads feature source DQ (GeoNotes) in a raw format. This way, the hidden table 'NetConConnection Deletions' is accessible. This table is used to monitor removing data patches. 
### Trace
Feature source of type Network Trace. This feature source requires the NetworkTraceBase.dll add-in. This feature source consumes data from the Connection table and produces the calculated connectivity model that is held in memory. The configuration of the Trace feature source can vary. The below picture shows possible configuration. 
![[../../Zimages/FS_Trace.png|FS_Trace.png]]
### Outage Configuration
Feature source of type CSV. It hold a simple table with parameters that are used for configuring the NetCon Portal project. It has these attributes: Group, Name, Value and Comment. Below are displayed currently used parameters. 
```
Group,Name,Value,Comment
TRACE,TRACE_NETWORK_NAME,E NRT,
STATE,STATE_ENUM_STATE_CONDUCTING,Closed
STATE,STATE_ENUM_STATE_BARRING,Open
STATE,STATE_ENUM_STATE_ALWAYS_CONDUCTING,Always Closed
TRACE,TRACE_DISCIPLIN,Electricity,
COLLECTION_NAME,COLLECTION_NAME_BARRIER,valve,
COLLECTION_NAME,BARRIER_NAME,Isolating Equipment,
COLLECTION_NAME,COLLECTION_NAME_SERVICE_POINT,servicepoint,
COLLECTION_NAME,COLLECTION_NAME_LINE,pipe,
COLLECTION_NAME,DQ_COLLECTION_NAME,dqoutput,
GEONOTE_NAME,GEONOTE_NAME_OUTAGE,outage,
GEONOTE_NAME,GEONOTE_NAME_OBSERVATION,observation,
COLLECTION_NAME,ASSET_TABLE_NAMES,"hv_busbar, ..., service_point",
OTHER,DQ_CONNECTION_ID_START,1000000000,
OTHER,CS_EPSG_CODE,3396,
```
## Business collections
This section clarifies what business collections should be available in the viewer project. Certain business collections are necessary for the project to work properly. It is recommended to follow the structure of business collections as listed below. 
### 1. Map
This folder holds all business collections that are displayed on the map (or are related to tables that are displayed on the map - various asset type tables such as the Cable Type table). 
#### Connection
The business collection 'Connection' is a copy of a business collection 'ModelNetConConnection'. Whereas 'ModelNetConConnection' is used as a base for network calculations and thus should not be heavily modified, 'Connection' is used for presenting the Connection records in the NetCon Portal application and therefore can be modified accordingly (joined tables, added fields etc.). 

The collection should have the internal name 'modelnetconconnection2'. 

The collection has joined DQ table (data patch). The tables are joined via connection ID (MetaHistoryRootId). Direct field *Removed* from the DQ table should be added to the collection. 

The field *Barrier* should be modified as below. 
```cs
{
    var barrier_w_dq = IF(HasValue([DQ record]), [DQ record].Barrier.ToLong(), [NetConConnection Map].IsBarrier);
    return barrier_w_dq;
}
```

The field *Flow* should be modified as below. 
```cs
IF(HasValue([DQ record].Id), NetConFlowString("E NRT", [DQ record].Id), NetConFlowString("E NRT", [NetConConnection Map].MetaHistoryRootId))
```

New geometry field *FlowArrow* should be added to the collection as GeometryL.MidPoints(). This geometry will be displayed alongside the source GIS data. The style settings of this geometry will differ from other MidPoint geometry fields of the Connection table. The styling should be done based on an attribute differentiating the GIS linear objects, e.g. pipe diameter attribute for water pipes.  

The Filter tab of the source collection should be set as follows:
```cs
StatusCode >= 0 AND StatusCode <= 10
```

The Properties tab of the collection should be set as follows: 
```cs
Concat(Connection.AssetTableName, " ", Connection.AssetId)
```
#### Source table(s) representing a barrier
For every table that represents a barrier object, the field *State* must be modified to display the current value if change of state has been made in the NetCon Portal application. To get the value from the DQ table, the source NetConConnection table must be joined via *AssetId* and then the DQ table with the NetConConnection table via connection ID. Then the field *State* can be defined as follows: 
```cs
{
    var state = IF(HasValue([DQ rec].Barrier), LookupConvert([DQ rec].Barrier, -1, "Closed", 1, "Open", -15, "Always Closed"), LookupConvert([E HV Circuit Breaker].[Switch State Type], "closed", "Closed", "opened", "Open"));
    
    return state;
}
```
#### Service Point
This collection represents the end points of the network, where the commodity is distributed to. For this collection, join the ServiceDownLog table via *AssetId* field. Then you can add a field *NoService* that is calculated from the joined (if any) ServiceDownLog record. 
### 2. GeoNotes
This folder holds most of the GeoNotes business collections. 
#### Outage
This business collection represents the records of the Outage table. 

The fields *ValidFrom* and *ValidTo* should be set to ToLocalTime() and have following date formatting: {0:dd/MM/yyyy HH:mm:ss}. Next, unmodified copies of these fields *ValidFromUpd* (se_valid_from2) and *ValidFromTo* (se_valid_to2) should exist as well. These fields can be hidden. Another pair of data fields - ValidFromTxt and ValidToTxt - are used for the record description. The fields can be set as follows: 
```cs
{
    var day = Outage.ValidFrom.Day;
    var month = Outage.ValidFrom.Month;
    var month_txt = LookupConvert(month, 1, "Jan", 2, "Feb", 3, "Mar", 4, "Apr", 5, "May", 6, "Jun", 7, "Jul", 8, "Aug", 9, "Sep", 10, "Oct", 11, "Nov", 12, "Dec");
    var year = Outage.ValidFrom.Year;
    var year_txt = year.ToString();
    var year_short = Concat(year_txt[2], year_txt[3]);
    
    return Concat(day, "-", month_txt, "-", year_short);
}
```
In the Properties tab of the collection then set the description as follows: 
```cs
Concat(Outage.Status, " outage ", Outage.ValidFromTxt, " : ", Outage.ValidToTxt)
```

Field *NumberOfCustomers* should be renamed to *AllCustomers*. Field *NumberOfKeyCustomers* should be renamed to *KeyCustomers*. 

The collection should contain a join field *AffectedCustomers*. This field can be set up as a relationship field to the ServicePoint table (join must be done via OutageConnection and NetConConnection tables). Similarly, join field *BarriersToClose* should be created as a relationship field to the table representing barrier objects (join must be done via OutageConnection and NetConConnection tables). 
#### Sticky Note
The business collection for sticky notes that can be added in the NetCon Portal application. 

Hide original fields *Inserted (UTC)* and *Changed (UTC)*. Create a copy of these fields as *Inserted* and *Changed*, set them ToLocalTime() and format them {0:dd/MM/yyyy HH:mm:ss}. 
### 3. Fulltext
This folder holds all business collections that are used for generating the full-text search. Collections are copies of the business collections that we want to add to the full-text search. To find out more about setting up full-text search in Lite application, see the XY server documentation: [Full-text search setup]([Setup Full-Text Search - X&Y Server User Guide](https://documentation.spatial-eye.com/xy/2024_1/en/68d1c957-dfda-4712-aa7c-cf6cc5cf2127.htm)). 
### 4. ModelConnection
This folder contains all business collections that are related to network calculations. Mainly the collection 'ModelNetConConnection' that ideally does not have any modifications so the calculation engine is not slowed down when recalculating changes. Other included collections: 
- DQOutput - stores data patches
- ConnectionHistory - records any changes made on Connection records
- RemovedDQConnection - for monitoring deleted data patches
### 5. Trace
This folder holds all business collections produced by the Trace feature source. 
### 6. Configuration
This folder holds the collection 'outageconfiguration' that is loaded at the start of the NetCon Portal application and the parameters and their values listed in the table are used for flexible configuration of the product. 
## Business queries
Several business queries should be set up for the NetCon Portal application to work properly. 
- **Current Outages** - Outage table, date filter (ValidFrom < Now().AddDays(30))
- **Data Patches** - DQ table, no filter. Just for quicker access to data patches. 
- **Sticky Note Layer** - Sticky Note table, spatial filter (Location.Interacts(Map.Extent()))
## Map definitions
There are two map definitions: **Default** and **NetCon**. Default layer displays the source GIS objects, added GeoNotes objects such as Outage and Observation, as well as flow arrows of the related Connection records. The flow arrows are placed in the Background layer to prevent selecting them in the map. NetCon layer displays only Connection records. Usually, the operatable sections are displayed. Sections are distinguished by a color. 