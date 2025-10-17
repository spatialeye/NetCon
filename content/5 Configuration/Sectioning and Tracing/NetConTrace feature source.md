---
title: NetConTrace feature source
description:
permalink:
aliases:
draft: false
date: 2024-10-31
tags:
  - ToDo
---
# NetConTrace feature source

This feature source needs to be configured to enable the NetCon 2.0 sectioning and tracing. 
Both the tracing and section take the same input [[../../6 Use/DataModel/NetCon Connection|NetCon Connection]]s.

After loading, which time is dependent on the speed of the database and the number of connections, tracing is available.
Depending on the settings below, the feature source will cluster/section the network into Isolatable and Operated Sections, as well as Control and Custom sections.

#ToDo Write more.

| Configuration line item            | Description                                                                                                                                                                                                  | Default value                                                     | Parameter                       |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- | ------------------------------- |
| Discipline                         | Domain that will determine the class of network that network will create. One of:<br>{ Generic, Electricity, Gas, Water, Sewage, Telecom }                                                                   | Generic                                                           | Disciplin                       |
| Network name                       | Name that the output network of this feature source can be identified with, in expressions as well as the TraceApi, e.g. "E" or "G" or "E.DQ" or "G.DQ"                                                      | E, G, W, S or T                                                   | NetworkName                     |
| Underlying network                 | Name of another network this network is overlaying by adding / removing connections, e.g. "E" or "G"                                                                                                         | -                                                                 | UnderlyingNetworkName           |
| Read-only Connection table         | Name of a business collection that is used as input to populate the network. Used when there is no underlying network.                                                                                       | NetConConnection                                                  | ReadonlyConnectionTable         |
| Writable Connection table          | Name of a source collection that is used to store add/remove operations on connections in the network.                                                                                                       | GeoNoteConnection                                                 | WritableConnectionTable         |
| Status Range From                  | Minimum status code to include in the connection network, for filtering.                                                                                                                                     | 0 (Unknown)                                                       | NetworkStatusRangeMin           |
| Status Range To                    | Maximum status code to include in the connection network, for filtering.                                                                                                                                     | 10 (Decommissioned)                                               | NetworkStatusRangeMax           |
| Cuttable connection expression     | Predicate to denote which connections can be cut for outage isolation. (\*)                                                                                                                                  | -                                                                 | CuttableConnectionExpression    |
| Generate isolatable sections       | Whether connections need to be grouped into an isolatable section network.                                                                                                                                   | true                                                              | GenerateIsolatableSections      |
| Include unfed isolatable sections  | Parameter that specifies if one desires isolatable sections for parts of the network that are not connected to a source. (\*)<br>In the previous clustering section generator, this was called `omit_empty`. | true                                                              | IncludeUnfedIsolatableSections  |
| Generate operable sections         | Whether isolatable sections need to be grouped into an operated section network.                                                                                                                             | true                                                              | GenerateOperableSections        |
| Operable section cut expression    | Predicate to denote which connections will cut operable sections - apart from the ones that are barring                                                                                                      | assettablename=\*trans\*,\*trafo\*                                | OperableSectionCutExpression    |
| Generate Control Sections           | Whether isolatable sections need to be grouped into a Control Section network.                                                                                                                                | false                                                             | GenerateControlSections          |
| Control Section cut expression      | Predicate to denote which connections will cut Control Sections - apart from the ones that are barring                                                                                                        | assettablename=\*_isolating_equipment device_type=circuit_breaker | ControlSectionCutExpression      |
| Control Section upstream expression | Upstream condition that needs to be met before a new Control Section is created, e.g. the existence of a busbar.                                                                                                | assettablename=\*_connecting_segment AND device_type=\*busbar\*     | ControlSectionUpstreamExpression |
| Generate custom sections           | Whether isolatable sections need to be grouped into a custom section network.                                                                                                                                | false                                                             | GenerateCustomSections          |
| Custom section cut expression      | Predicate to denote which connections will cut custom sections - apart from the ones that are barring                                                                                                        | -                                                                 | CustomSectionCutExpression      |
| Custom section upstream expression | Upstream condition that needs to be met before a new custom section is created, e.g. the existence of a busbar.                                                                                                | -                                                                 | CustomSectionUpstreamExpression |
(\*) Note that these items still need to be implemented.

The predicates in the the table mentioned above can take wildcards just as the filter expressions passed to the reduction functions and API. These predicates support wildcard patterns.

For example, to generate Control Sections for circuit breakers the cuttable expression could be:

	assettablename=eo_isolatingequipmentinstallation AND devicetype=circuitbreaker

And the accompanying upstream predicate would be:

	assettablename=eo_connectorsegment AND devicetype=busbar

In another system, the cuttable expression could be:

	assettablenames=*power_switch

And the accompanying upstream predicate would be:

	assettablenames=mv_busbar,hv_busbar

| Predicate expression part         | Meaning                                                                                                 |
| --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `*`, `?` and `,`                  | Match any pattern rather than only a literal                                                            |
| assettablename                    | Matches the assettablename of connections                                                               |
| assettablenames                   | Matches one ore more assettablenames of a connection                                                    |
| assetid                           | Exact match of an assid                                                                                 |
| assetids                          | Comma separated list of exact asset ids                                                                 |
| customassetid                     | Exact match of an customassetid of connections                                                          |
| customassetids                    | Comma separated list of exact customassetids                                                            |
| commoditysubnetwork               | Matches the first part of the commodity of connections                                                  |
| commoditysubnetworks              | Comma separated list of match patterns for the first part of the commodity                              |
| Any assethierarchy property       | Any key-value property that occurs in the assethierarchy of connections, or that is added by enrichment |
| Any specification property        | Any key-value property that occurs in the specification of connections, or that is added by enrichment  |
| Any assetinfo enrichment property | Any key-value property that is added to connections by enrichment                                       |

## Output tables

| Table                      | Field                | Field Type | Description                                                                                       |
| -------------------------- | -------------------- | ---------- | ------------------------------------------------------------------------------------------------- |
| NetConConnection           |                      |            | Enriched version of the NetConConnection input table, containing all elements of the network.     |
|                            | Id*                  | long       | Key of the connection                                                                             |
|                            | FromNodeId           | long       |                                                                                                   |
|                            | ToNodeId             | long       |                                                                                                   |
|                            | ...                  |            |                                                                                                   |
|                            | Flow                 | enum       | none, upstream, downstream or meshed depending on how this connection is fed from a source         |
|                            | IsolatedSectionId    | long       | Id of the isolated section this connection belongs to.                                            |
|                            | OperatedSectionId    | long       | Id of the operated section this connection belongs to.                                            |
|                            | ControlSectionId      | long       | Id of the Control Section this connection belongs to.                                              |
|                            | CommoditySectionId   | long       | Id of the commodity section this connection belongs to.                                           |
| NetConIsolatableSection    | Id*                  | long       | Key of the connection                                                                             |
|                            | FromNodeId           | long       |                                                                                                   |
|                            | ToNodeId             | long       |                                                                                                   |
|                            | ...                  |            |                                                                                                   |
|                            | Flow                 | enum       | none, upstream, downstream or meshed depending on how this isolatable section is fed from a source |
|                            | OperatedSectionId    | long       | Id of the operated section this isolatable section belongs to.                                    |
|                            | ControlSectionId      | long       | Id of the Control Section this isolatable section belongs to.                                      |
|                            | CommoditySectionId   | long       | Id of the commodity section this isolatable section belongs to.                                   |
| NetConIsolatableTrace      | SourceId*            | long       | Id of isolatable section that is feeding as source.                                               |
|                            | FeedingId*           | long       | Id of isolatable section that is directly feeding.                                                |
|                            | FedId*               | long       | Id of isolatable section that is being fed.                                                       |
|                            | Depth                | long       |                                                                                                   |
|                            | Cost                 | long       |                                                                                                   |
| TraceResultNode            |                      |            | Simple node table that can be used to get a list of all nodes in the trace results.               |
|                            | Id*                  | long       |                                                                                                   |
|                            | EdgeType             | enum       |                                                                                                   |
|                            | GeometryP            | point      |                                                                                                   |
| TraceResultNode2Connection | ConnectionId*        | long       | Id of the connection.                                                                             |
|                            | NodeId*              | long       | Id of the node that the connection connects to by either its FromNodeId or ToNodeId.              |
| TraceResultPath            | ConnectionId*        | long       |                                                                                                   |
|                            | ...                  | long       |                                                                                                   |
|                            | Flow                 | enum       |                                                                                                   |
|                            | PreviousConnectionId |            |                                                                                                   |
|                            | Depth                | int        |                                                                                                   |
|                            | SumCost              | double     |                                                                                                   |
|                            | Marker               | enum       |                                                                                                   |
|                            |                      |            |                                                                                                   |
