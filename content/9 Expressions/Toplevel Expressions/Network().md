---
title: Network()
description: An expression that provides a handle to the network, which contains [[Connections|Connections]] and knows about their [[Sections|Sections]] and [[Flow|Flow]].
permalink:
aliases:
draft: true
date: 2024-10-02
tags:
  - Network
  - Expression
  - TopLevelExpression
---
# Network()

An expression that provides a handle to the network, which contains [[Connections|Connections]] and knows about their [[Sections|Sections]] and [[Flow|Flow]].

## Parameters
| File                                                             | type   | mand | description                                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------------- | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/NetworkName\|NetworkName]] | string | true | Name of a network that has been defined, either by setting up a NetworkTraceBase feature source or by creating a temporary derived WhatIf network. The network name is typically one of 'E', 'G', 'H', 'S', 'T', or 'W' (for electricity, gas, heat, sewage, telecom or water). |


## Results
| File                                                              | type          | unique | description                                                                                                               |
| ----------------------------------------------------------------- | ------------- | ------ | ------------------------------------------------------------------------------------------------------------------------- |
| [[../Results/NetworkEngine\|NetworkEngine]] | NetworkEngine | true   | An engine that holds the network network, which contains [[Connections|Connections]] and knows about their [[Sections|Sections]] and [[Flow|Flow]]. |


