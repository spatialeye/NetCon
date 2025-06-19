---
title: NetCon Trace Function and Mode
description: 
permalink: 
aliases: 
draft: false
date: 2025-06-19
tags: 
---
# NetCon Trace Function and Mode

Enumerator that provides feedback on the Trace Function and Mode that were chosen by making an [[../../8 API/NetCon API Calls|API Call]].
See also [[TraceFunction|TraceFunction]].

| Function Id | Mode Id | Function Name        | Mode Name                 | Value                         |
| ----------: | ------- | -------------------- | ------------------------- | ----------------------------- |
|           0 | -       | getConnection        | -                         | get-connection                |
|           1 | -       | getIsolatableSection | -                         | get-isolatablesection         |
|           2 | -       | getOperatedSection   | -                         | get-operatedSection           |
|           3 | -       | getControlSection    | -                         | get-controlSection            |
|           4 | -       | getCustomSection     | -                         | get-customSection             |
|           5 | -       | getNeighbors         | -                         | get-neighbors                 |
|          10 | 1       | tracePath            | normal                    | trace-path-forward            |
|             | 2       |                      | **backwards**             | trace-path                    |
|             | 4       |                      | down                      | trace-path-downstream         |
|             | 8       |                      | up                        | trace-path-upstream           |
|          11 | 1       | traceOut             | **normal**                | trace-out                     |
|             | 2       |                      | backwards                 | trace-out-backwards           |
|             | 4       |                      | down                      | trace-out-downstream          |
|             | 8       |                      | up                        | trace-out-upstream            |
|          12 | 12      | traceMeshed          | meshed                    | trace-meshed                  |
|          13 | 1       | traceNeighbors       | trace-neighbors-backwards | trace-neighbors               |
|             | 2       |                      | backwards                 | trace-neighbors-backwards     |
|             | 4       |                      | down                      | trace-neighbors-downstream    |
|             | 8       |                      | up                        | trace-neighbors-upstream      |
|          14 | 3       | traceAsset           | any                       | trace-asset                   |
|          15 | 1       | traceSingularPath    | normal                    | trace-singularpath            |
|             | 2       |                      | backwards                 | trace-singularpath-backwards  |
|             | 4       |                      | down                      | trace-singularpath-downstream |
|             | 8       |                      | up                        | trace-singularpath-upstream   |
|          16 | -       | traceOutageImpact    | -                         | trace-outage-impact           |
|          17 | -       | traceOutageRootCause | -                         | trace-outage-root-cause       |

| Mode Id | Mode      | Description                                                                                                 |
| ------- | --------- | ----------------------------------------------------------------------------------------------------------- |
| 1       | normal    | Follow connections in the order from FromId to ToId and reversed if bidirectional.                          |
| 2       | backwards | Opposite of 'normal'; unidirectional connections are traversed in the opposite direction.                   |
| 3       | any       | Ignore directionality of the connections.                                                                   |
| 4       | down      | Follow flow downstream flow (as determined by barriers, commodity rules and flow restrictions).             |
| 8       | up        | Follow flow upstream flow (as determined by barriers, commodity rules and flow restrictions).               |
| 12      | meshed    | Follow flow upstream or downstream flow (as determined by barriers, commodity rules and flow restrictions). |

