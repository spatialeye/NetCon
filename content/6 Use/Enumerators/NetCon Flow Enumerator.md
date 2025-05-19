---
title: NetCon Flow Values
description: Encodes the flow as used in NetCon.
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# NetCon Flow Enumerator

Enumerator encoding the flow as used in NetCon.
The definition and contents of the table is standard and cannot be altered.

| FlowType | FlowValue | Description                                                                                                                                                                             |
| -------: | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|        0 | None      | This connection cannot be reached from a source, or the way the barriers are currently operated, there is no flow reaching it.                                                          |
|        1 | Down      | Flow goes in the direction from FromId to ToId.                                                                                                                                         |
|        2 | Up        | Flow goes in the direction from ToId to FromId. This is only possible for bi-directional connections.                                                                                   |
|        3 | Mazed     | Both the FromId and ToId are fed from a source, so the flow can be both ways. A network in which there is redundancy and consumers are fed via different routes, is a mazet network. `` |
|        4 | Violation | Should not occur. A violation is when a connection is uni-directional (it can only transport from FromId to ToId) but it is used the other way round.                                   |
|        8 | No engine | There is no TraceEngine present to compute the flow.                                                                                                                                    |


