---
title: Aspect
description: Enum to select what data quality aspect will be computed. If none is provided, all are computed.
Type: string
Order: 999
Mandatory: false
permalink: 
aliases: 
draft: false
date: 2025-06-01
tags:
  - ApiParameter
  - Aspect
---
# Aspect

Type of: _string_
Unique: __

Enum to select what data quality aspect will be computed. If none is provided, all are computed.

A single string parameter `aspect` can be provided to select the data quality aspect for which the count will be computed. 
If not provided, all will be reported.

Possible values:
* **IslandsCount**: compute the number of islands, each comprised of connected connections, can be found in the network;
* **MissingNodes**: starting from the assumption that between different assets with [[../Results/Connection Or Path Results/EdgeType|EdgeType]] of type `Link` (line asset), there should be an asset with Edgetype of type `SelfLoop` (point asset), it will look for nodes where the SelfLoops are missing;
* **SupernumeraryNodes**: will find all connections of EdgeType `SelfLoop` that are on the same node;
* **SupernumeraryLinks**: will find all connections of EdgeType `Link` that are connecting to and from the same nodes.
