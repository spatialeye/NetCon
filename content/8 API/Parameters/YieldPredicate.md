---
title: YieldPredicate
description: An expression to indicate with which connections to return during tracing, e.g. AssetTableName=e_service_point AND (NOT Role=Prosumer)
Type: string
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
  - ApiParameter
  - YieldPredicate
---
# YieldPredicate

Type of: _string_
Unique: __

An expression to indicate with which connections to return during tracing, e.g. AssetTableName=e_service_point AND (NOT Role=Prosumer)

A single string parameter `YieldPredicate` can be provided to provide a predicate with which to find at what kind of connections the trace should return as a result.
(Or in case for [[../../6 Use/Enumerators/NetCon TraceFunction Enumerator|Trace Function]] a query is chosen, this will be ignored.)

When a `YieldPredicate` is matched, the result is considered to be sought after and returned, but the trace continues. This is useful e.g. when looking for service points that can be one behind another. In that, if differs from the [[./StopPredicate|StopPredicate]].
