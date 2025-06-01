---
title: NetCon API Calls
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-30
tags: 
---
# NetCon API Calls

See also [[./NetCon API Introduction|NetCon API Introduction]].

About the parameters of the API calls.

* Many parameters are optional. The combination of the parameters that you do (or do not) provide, will determine the result that you get.
* Some parameter have `pattern` appended to their name. Those are support [[./Wildcards|Wildcards]] patterns.
 
---
## Meta information calls
  
These are generic services to ask information about the network. 

| File                                                                    | description                                                                 |
| ----------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| [[./Calls/Statistics\|Statistics]]                       | \-                                                                          |
| [[./Calls/Engine Process States\|Engine Process States]] | Returns state records of the execution of processes of the network engines. |
| [[./Calls/DataQuality\|DataQuality]]                     | Return counts of                                                            |
| [[./Calls/Catalogs\|Catalogs]]                           | Returns all NetCon catalogs and enumerator values.                          |



---
## Look up and search calls, that will return connections

| File                                                                    | description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| [[./Calls/GetConnection\|GetConnection]]                 | Retrieves all connectivity information of assets for matching criteria. |
| [[./Calls/GetControlSection\|GetControlSection]]         | \-                                                                      |
| [[./Calls/GetCustomSection\|GetCustomSection]]           | \-                                                                      |
| [[./Calls/GetIsolatableSection\|GetIsolatableSection]]   | \-                                                                      |
| [[./Calls/GetNeighbor\|GetNeighbor]]                     | \-                                                                      |
| [[./Calls/GetNeighborDownstream\|GetNeighborDownstream]] | \-                                                                      |
| [[./Calls/GetNeighborUpstream\|GetNeighborUpstream]]     | \-                                                                      |
| [[./Calls/GetOperatedSection\|GetOperatedSection]]       | \-                                                                      |



---
## Trace and network following calls, that will return paths

| File                                                                | description |
| ------------------------------------------------------------------- | ----------- |
| [[./Calls/TraceMazed\|TraceMazed]]                   | \-          |
| [[./Calls/TraceNeighbor\|TraceNeighbor]]             | \-          |
| [[./Calls/TraceOut\|TraceOut]]                       | \-          |
| [[./Calls/TraceOutageImpact\|TraceOutageImpact]]     | \-          |
| [[./Calls/TraceOutDownstream\|TraceOutDownstream]]   | \-          |
| [[./Calls/TraceOutUpstream\|TraceOutUpstream]]       | \-          |
| [[./Calls/TracePath\|TracePath]]                     | \-          |
| [[./Calls/TracePathDownstream\|TracePathDownstream]] | \-          |
| [[./Calls/TracePathUpstream\|TracePathUpstream]]     | \-          |


---
## Network manipulation calls, that will change the state and create data patches

| File | description |
| ---- | ----------- |

 