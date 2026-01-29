---
title: StartPredicate
description: An expression to indicate with which connections to start tracing, e.g. AssetTableName=e_busbar AND AssetId=1234 AND (NOT Cost<1)
Type: string
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
  - ApiParameter
  - StartPredicate
---
# StartPredicate

Type of: _string_
Unique: __

An expression to indicate with which connections to start tracing, e.g. AssetTableName=e_busbar AND AssetId=1234 AND (NOT Cost<1)

A single string parameter `StartPredicate` can be provided to provide a predicate with which to find the start connections for a trace.
(Or in case for [[../../6 Use/Enumerators/NetCon TraceFunction Enumerator|Trace Function]] a query is chosen, this will be used as the `WherePredicate`).

