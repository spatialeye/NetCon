---
title: NetCon TraceMarker Enumerator
description: Mark a special role of connections in path results when tracing.
permalink: 
aliases: 
draft: false
date: 2025-04-19
tags: 
---
# NetCon TraceMarker Enumerator

TraceMarkers mark a special role of connections in path results when tracing.

| Id  | Name           | Description                                          |
| --- | -------------- | ---------------------------------------------------- |
| 0   | None           | No special role in trace results.                    |
| 1   | Start          | Used as start of trace.                              |
| 2   | End            | Retrieved as end of trace.                           |
| 3   | StartAndEnd    | Used as start and retrieved as end of trace.         |
| 4   | Waypoint       | Used to set a way point for trace.                   |
| 16  | MakeBarring    | Trace has overriden the barrier state to barring.    |
| 32  | MakeConducting | Trace has overriden the barrier state to conducting. |
