---
title: NetworkMatch()
description: Creates a predicate to use on [[Connections|Connections]] to filter them.
Type: NetworkPredicate
Order: 999
Unique: false
permalink:
aliases:
draft: false
date: 2024-10-02
tags:
  - NetworkMatch
  - TopLevelExpression
  - Expression
---
# NetworkMatch()

Type of: _NetworkPredicate_
Unique: __

Creates a predicate to use on [[Connections|Connections]] to filter them.


## Parameters
| File                                                                     | type   | mand  | description                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------ | ------ | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/PropertyKey\|PropertyKey]]         | string | false | Unique name that identifies a property, e.g. 'assettablename', '', 'station.name' or 'material.shortname'. The property key must have been made known to the system via [[Data Enrichment|Data Enrichment]] or it must be a standard property. Standard properties are: assettablename, assettablenames, assetid, assetids, customassetid, customassetids, label, commoditysubnetwork, commoditysubnetworks. |
| [[../Parameters/PropertyPattern\|PropertyPattern]] | string | true  | A string with or without a [[Wildcard|Wildcard]] pattern that must be matched for a NetworkPredicate to be true.                                                                                                                                                                                                                                                                                      |


## Results
| File                                                                    | type             | unique | description                                             |
| ----------------------------------------------------------------------- | ---------------- | ------ | ------------------------------------------------------- |
| [[../Results/NetworkPredicate\|NetworkPredicate]] | NetworkPredicate | false  | A predicate that can be used to filter [[Connections|Connections]]. |


