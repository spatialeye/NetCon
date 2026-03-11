---
title: Geometry Retention Time
description:
permalink:
aliases:
draft: false
date: 2026-03-11
tags:
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
# Geometry Retention Time

Time in minutes that the geometries are retained when a query is executed. 
The default is 5 minutes, which means that geometries that are not used by any process for the last 5 minutes, are purged from the system.

When set to 0, geometries are retained forever *and preloaded into memory* so access is instantaneous. 
The trade of is more memory is required.

Because the output of the [[Configuring NetCon TraceAPI|TraceAPI]] is typically in GeoJSon, which does not support curves, geometries in the cache are faceted.
For very small geometries, a minimal precision of 1/3 of the line length of the geometry is used. 
For large geometries, faceting is done course with a larger faceting distance.
In between, 0.3 (m) is used a faceting distance.

