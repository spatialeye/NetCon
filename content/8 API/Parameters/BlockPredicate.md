---
title: BlockPredicate
description: An expression to indicate with connections will block a trace, e.g. commodity->(net=LV OR net=PL) OR AssetTableName=e_lv*"
Type: string
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
  - ApiParameter
  - BlockPredicate
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
# BlockPredicate

Type of: _string_
Unique: __

An expression to indicate with connections will block a trace, e.g. commodity->(net=LV OR net=PL) OR AssetTableName=e_lv*"

A single string parameter `StartPredicate` can be provided to provide a predicate with which to find at what kind of connections the trace should stop and return the result.
(Or in case for [[../../6 Use/Enumerators/NetCon TraceFunction Enumerator|Trace Function]] a query is chosen, this will be ignored.)

