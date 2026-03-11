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

| Id  | Name           | Description                                                        |
| --- | -------------- | ------------------------------------------------------------------ |
| 0   | None           | No special role in trace results.                                  |
| 1   | Start          | Used as start of trace.                                            |
| 2   | Stop           | Retrieved as end of trace by matching the stop predicate.          |
| 3   | StartAndStop   | Used as start and end of trace by matching the stop predicate.     |
| 4   | Yield          | Retrieved as end of trace by matching the yield predicate.         |
| 5   | StartAndYield  | Used as start and end of trace by matching the yield predicate.    |
| 8   | Waypoint       | Used to set a way point for trace.                                 |
| 16  | MakeBarring    | Trace has overriden the barrier state to barring.                  |
| 32  | MakeConducting | Trace has overriden the barrier state to conducting.               |
| 64  | Alternative    | An alternative path to a shortest path that is the end of a trace. |
