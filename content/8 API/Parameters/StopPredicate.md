---
title: StopPredicate
description: An expression to indicate with which connections to start tracing, e.g. AssetHierarchy->e_stationcomplex->CustomAssetId="CBC10BDA-61D5-49EA-9F48-2269004A1F9A" AND AssetTableName!=e_hv_hypernode
Type: string
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
  - ApiParameter
  - StopPredicate
---
# StopPredicate

Type of: _string_
Unique: __

An expression to indicate with which connections to start tracing, e.g. AssetHierarchy->e_stationcomplex->CustomAssetId="CBC10BDA-61D5-49EA-9F48-2269004A1F9A" AND AssetTableName!=e_hv_hypernode

A single string parameter `StopPredicate` can be provided to provide a predicate with which to find at what kind of connections the trace should stop and return the result.
(Or in case for [[../../6 Use/Enumerators/NetCon TraceFunction Enumerator|Trace Function]] a query is chosen, this will be ignored.)

When a `StopPredicate` is hit, the trace does not continue with connections behind the match. If such is desired, an [[./YieldPredicate|YieldPredicate]] should be used instead.