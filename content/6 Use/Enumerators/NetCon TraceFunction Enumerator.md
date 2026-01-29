---
title: NetCon TraceFunction Enumerator
description: Determines what kind of query or trace is performed on the network.
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
---
# NetCon TraceFunction Enumerator

Enumerator that determines the query (get) or trace that is performed on network.

See also [[./NetCon Trace Function and Mode|NetCon Trace Function and Mode]] for the combination effect between Function and Mode.

| Mode Id | Mode                 | Description                                                                                                                                                                                                  |
| ------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0       | getConnection        | Retrieves all connections matching a where clause.                                                                                                                                                           |
| 1       | getIsolatableSection | Retrieves all connections inside an [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Isolatable Sections\|Isolatatble Section]].                                                                                                                            |
| 2       | getOperatedSection   | Retrieves all connections inside an [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Operated Sections\|Operated Section]].                                                                                                                                 |
| 3       | getControlSection    | Retrieves all connections inside a [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Control or NetCongestion Sections\|Control Section]].                                                                                                                   |
| 4       | getCustomSection     | Retrieves all connections inside a [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Custom Sections\|Custom Section]].                                                                                                                                      |
| 5       | getNeighbors         | Retrieves neighboring connections.                                                                                                                                                                           |
| 10      | tracePath            | Traces a network and returns the first path that is a match.                                                                                                                                                 |
| 11      | traceOut             | Traces a network and returns all paths that are a match.                                                                                                                                                     |
| 12      | traceMeshed          | Traces a meshed network, i.e. one that whose flow it both up and down stream for the current barring states.                                                                                                 |
| 13      | traceNeighbors       | Traces to the neighboring asset of this asset; all connections belong to this asset between start connection and result will not be counted as neighbors.                                                    |
| 14      | traceAsset           | Not available yet. Traces all connections that belong to an asset, connecting to the starting connection.                                                                                                    |
| 15      | traceSingularPath    | Traces a path at long as it does not branch. Can go into both directions from the start element. All result elements are connected and can be lined up, never exceeding degree 2.                            |
| 16      | traceOutageImpact    | Performs an outage isolation, calculates the impacted area, the upstream barriers that need to be closed to effectuate to isolation, and the backfeeding barriers that can be used to allieviate the outage. |
| 17      | traceOutageRootCause | Not available yet. Performs a root cause analysis given a set of outages identified by connections.                                                                                                          |

(\*) It is only in very peculiar situations that flow is going towards a barring barrier, but those can exist if it 'by-passes' the barrier.
