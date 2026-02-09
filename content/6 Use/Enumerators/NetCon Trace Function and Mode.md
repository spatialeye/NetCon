---
title: NetCon Trace Function and Mode
description:
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
---
# NetCon Trace Function and Mode

Enumerator that provides feedback on the Trace Function and Mode that were chosen by making an [[../../8 API/NetCon API Calls|API Call]].
See also [[./NetCon TraceFunction Enumerator|NetCon TraceFunction Enumerator]] and [[./NetCon TraceMode Enumerator|NetCon TraceMode Enumerator]].

The [[../../8 API/Parameters/BlockBarringConnections|BlockBarringConnections]] parameter can alter the [[./NetCon TraceMode Enumerator|Trace Mode]] that is being used performing the [[./NetCon TraceFunction Enumerator|Trace Function]], which is useful if barring barriers must be returned as well during a flow trace.

| Function Id | Mode Id | Function Name        | Mode Name                 | Block Barring Connections | Value                         |
| ----------: | ------- | -------------------- | ------------------------- | ------------------------- | ----------------------------- |
|           0 | -       | getConnection        | -                         |                           | get-connection                |
|           1 | -       | getIsolatableSection | -                         |                           | get-isolatablesection         |
|           2 | -       | getOperatedSection   | -                         |                           | get-operatedSection           |
|           3 | -       | getControlSection    | -                         |                           | get-controlSection            |
|           4 | -       | getCustomSection     | -                         |                           | get-customSection             |
|           5 | -       | getNeighbors         | -                         |                           | get-neighbors                 |
|          10 | 1       | tracePath            | normal                    | true/false                | trace-path-forward            |
|             | 2       |                      | **backwards**             | true/false                | trace-path                    |
|             | 4       |                      | down                      | true                      | trace-path-downstream         |
|             | 8       |                      | up                        | true                      | trace-path-upstream           |
|             | 20      |                      | downInclBarring           | false                     | trace-path-downstream         |
|             | 24      |                      | upInclBarring             | false                     | trace-path-upstream           |
|          11 | 1       | traceOut             | **normal**                | true/false                | trace-out                     |
|             | 2       |                      | backwards                 | true/false                | trace-out-backwards           |
|             | 4       |                      | down                      | true                      | trace-out-downstream          |
|             | 8       |                      | up                        | true                      | trace-out-upstream            |
|             | 20      |                      | downInclBarring           | false                     | trace-out-downstream          |
|             | 24      |                      | upInclBarring             | false                     | trace-out-upstream            |
|          12 | 12      | traceMeshed          | meshed                    | true                      | trace-meshed                  |
|             | 28      |                      | meshedInclBarring         | false                     | trace-meshed                  |
|          13 | 1       | traceNeighbors       | trace-neighbors-backwards | true/false                | trace-neighbors               |
|             | 2       |                      | backwards                 | true/false                | trace-neighbors-backwards     |
|             | 4       |                      | down                      | true                      | trace-neighbors-downstream    |
|             | 8       |                      | up                        | true                      | trace-neighbors-upstream      |
|             | 20      |                      | downInclBarring           | false                     | trace-neighbors-downstream    |
|             | 24      |                      | upInclBarring             | false                     | trace-neighbors-upstream      |
|          14 | 3       | traceAsset           | any                       | true/false                | trace-asset                   |
|          15 | 1       | traceSingularPath    | normal                    | true/false                | trace-singularpath            |
|             | 2       |                      | backwards                 | true/false                | trace-singularpath-backwards  |
|             | 4       |                      | down                      | true                      | trace-singularpath-downstream |
|             | 8       |                      | up                        | true                      | trace-singularpath-upstream   |
|             | 20      |                      | downInclBarring           | false                     | trace-singularpath-downstream |
|             | 24      |                      | upInclBarring             | false                     | trace-singularpath-upstream   |
|          16 | -       | traceOutageImpact    | -                         |                           | trace-outage-impact           |
|          17 | -       | traceOutageRootCause | -                         |                           | trace-outage-root-cause       |
