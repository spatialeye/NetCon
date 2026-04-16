---
title: Indices
description: NetCon uses start indices to quickly find the connections with which to start a trace.
permalink:
aliases:
draft: false
date: 2026-02-24
tags:
  - Index
  - Indices
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
# Indices

When a trace over the network is started, NetCon will try to use indices in order to quickly find the start connections. Hence, indices are only applied to find the start connections.

If no indices have been defined for a query, the entire [[Network|Network]] needs to be scanned to find the start connections.

It is not always necessary to have an index on any elements. In particular, if [[And|And]] is used, it already helps if an index is present in either the left or right hand side. For [[Or|Or]], both sides need to have an index. Also [[In|In]] predicates can use indices.

The various indices should be separated by a `,` or `;`

Build in indices:
* [[../8 API/Results/Connection Or Path Results/Role|Role]] with the value [[../3 Overview/3.5 Commodity Networks/Sources|Source]]
* [[../8 API/Results/Connection Or Path Results/Id|Id]]
* [[../8 API/Results/Connection Or Path Results/FromId|FromId]]
* [[../8 API/Results/Connection Or Path Results/ToId|ToId]]

Indices that are always recommended are:
 * [[../8 API/Results/Connection Or Path Results/AssetTableName|AssetTableName]]
 * [[../8 API/Results/Connection Or Path Results/AssetId|AssetId]]
 * [[../8 API/Results/Connection Or Path Results/CustomAssetId|CustomAssetId]]

If labels are used to start searches, this also should to be added:
 * [[../8 API/Results/Connection Or Path Results/Label|Label]]

Furthermore, indices on [[../8 API/Results/Connection Or Path Results/AssetHierarchy|AssetHierarchy]] or enriched data can be prove to be useful, 
 * AssetHierarchy->SubStation->Id
 * AssetHierarchy->Ean->Id
 * AssetHierarchy->Address->Postcode

For example, if you have enriched your network with address information, and you start traces by address, you definitely would use add the Postcode. If a house number is used as a refined, that can be sought on the fly.

If you want to start traces from a particular kind of asset, you could also use the [[../8 API/Results/Connection Or Path Results/Specification|Specification]] as an index.
* Specification->SwitchType->Id

