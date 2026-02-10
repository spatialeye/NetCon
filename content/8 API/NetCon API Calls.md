---
title: NetCon API Calls
description:
permalink:
aliases:
draft: false
date: 2026-01-29
tags:
---
# NetCon API Calls

See also [[./NetCon API Introduction|NetCon API Introduction]].

About the parameters of the API calls.

* Many parameters are optional. The combination of the parameters that you do (or do not) provide, will determine the result that you get.
* Some parameter have `pattern` appended to their name. Those are support [[./Wildcards|Wildcards]] patterns.

Most calls are also available in an [[./NetCon Async API Calls|NetCon Async API Calls]] version.
 
---
## Meta information calls
  
These are generic services to ask information about the network. 

| File                                                                    | description                                                                                          |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [[./Calls/Statistics\|Statistics]]                       | Returns counts of how often certain properties, such as Barrier or Role or AssetTableName, occur.    |
| [[./Calls/DataQuality\|DataQuality]]                     | Return counts of islands, missing nodes, supernumerary nodes and supernumerary links in the network. |
| [[./Calls/Catalogs\|Catalogs]]                           | Returns all NetCon catalogs and enumerator values.                                                   |
| [[./Calls/Engine Process States\|Engine Process States]] | Returns state records of the execution of processes of the network engines.                          |



---
## Look up and search calls, that will return connections

| File                                                                    | description                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[./Calls/GetConnection\|GetConnection]]                 | Retrieves all connectivity information of assets for matching criteria.                                                                                                                                                                                                 |
| [[./Calls/GetControlSection\|GetControlSection]]         | Retrieves all connections inside a Control Section.                                                                                                                                                                                                                     |
| [[./Calls/GetCustomSection\|GetCustomSection]]           | Retrieves all connections inside a Custom Section.                                                                                                                                                                                                                      |
| [[./Calls/GetIsolatableSection\|GetIsolatableSection]]   | Retrieves all connections inside an Isolatatble Section.                                                                                                                                                                                                                |
| [[./Calls/GetNeighbor\|GetNeighbor]]                     | Retrieves neighboring connections.                                                                                                                                                                                                                                      |
| [[./Calls/GetNeighborDownstream\|GetNeighborDownstream]] | Retrieves neighboring connections that are connected with a downstream flow.                                                                                                                                                                                            |
| [[./Calls/GetNeighborUpstream\|GetNeighborUpstream]]     | Retrieves neighboring connections that are connected with an upstream flow.                                                                                                                                                                                             |
| [[./Calls/GetOperatedSection\|GetOperatedSection]]       | Retrieves all connections inside an Operated Section.                                                                                                                                                                                                                   |
| [[./Calls/PredicateQuery\|PredicateQuery]]               | A compact query that requires all Start parameters to be packed in a StartPredicate, all Stop parameters in a StopPredicate, etc. The predicate allows for AND, OR, NOT and () in its expressions. The TraceFunction and TraceMode also need to be supplied explicitly. |



---
## Trace and network following calls, that will return paths

| File                                                                | description                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[./Calls/PredicateQuery\|PredicateQuery]]           | A compact query that requires all Start parameters to be packed in a StartPredicate, all Stop parameters in a StopPredicate, etc. The predicate allows for AND, OR, NOT and () in its expressions. The TraceFunction and TraceMode also need to be supplied explicitly. |
| [[./Calls/TraceMeshed\|TraceMeshed]]                 | Traces a meshed network, i.e. one that whose flow it both up and down stream for the current barring states.                                                                                                                                                            |
| [[./Calls/TraceNeighbor\|TraceNeighbor]]             | Traces to the neighboring asset of this asset; all connections belong to this asset between start connection and result will not be counted as neighbors.                                                                                                               |
| [[./Calls/TraceOut\|TraceOut]]                       | Traces a network and returns all paths that are a match.                                                                                                                                                                                                                |
| [[./Calls/TraceOutageImpact\|TraceOutageImpact]]     | Performs an outage isolation, calculates the impacted area, the upstream barriers that need to be closed to effectuate to isolation, and the backfeeding barriers that can be used to allieviate the outage.                                                            |
| [[./Calls/TraceOutDownstream\|TraceOutDownstream]]   | Traces a network and returns all paths that are a match by following a downstream flow.                                                                                                                                                                                 |
| [[./Calls/TraceOutUpstream\|TraceOutUpstream]]       | Traces a network and returns all paths that are a match by following an upstream flow.                                                                                                                                                                                  |
| [[./Calls/TracePath\|TracePath]]                     | Traces a network and returns the first path that is a match.                                                                                                                                                                                                            |
| [[./Calls/TracePathDownstream\|TracePathDownstream]] | Traces a network and returns the first path that is a match by following a downstream flow.                                                                                                                                                                             |
| [[./Calls/TracePathUpstream\|TracePathUpstream]]     | Traces a network and returns the first path that is a match by following an upstream flow.                                                                                                                                                                              |


---
## Network manipulation calls, that will change the state and create data patches

| File | description |
| ---- | ----------- |

 