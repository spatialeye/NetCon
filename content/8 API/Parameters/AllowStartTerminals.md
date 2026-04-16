---
title: AllowStartTerminals
description: True if terminals are allowed as start criteria, false (default) if they are filtered out.
Type: boolean
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2026-02-09
tags:
  - ApiParameter
  - AllowStartTerminals
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
# AllowStartTerminals

Type of: _boolean_
Unique: __

True if terminals are allowed as start criteria, false (default) if they are filtered out.

This is an internal parameter - not (yet) exposed to API users.

On searching start network elements, it is typically undesired/unwanted to start from a terminal.
Terminals are often 'invisible', and are encapsulating the asset from the GIS.
If they are in the start set build with the start predicate, then the trace will start from there, because the terminals encapsulate the asset.

Therefore, by default, this parameter is set to false so the start predicate will get an extra filter to take out terminals.
This is only done if the start predicate does not filter on Ids (in which case filtering on terminals would take out explicit given network elements, which is unwanted).
If true (possible override) then no extra filter is set.
