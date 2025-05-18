---
title: NetCon Barrier Enumerator
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# NetCon Barrier Enumerator

Enumerator defining the switching or barring behavior of the network assets that can block the flow.
See also [[../../3 Overview/Barrier or Operational State|Barrier]].

| BarrierType | BarrierValue         | Description                                                                                                            |
| ----------: | -------------------- | ---------------------------------------------------------------------------------------------------------------------- |
|           0 | NoBarrier            | When this connection is not used for blocking/allowing the commodity, all other states indicate that is used for that. |
|          -2 | MostlyBarring        | It is blocked but allowing a trickle to pass through (not valid for every network).                                    |
|          -1 | IsConducting         | The connection is currently conducting the commodity.                                                                  |
|           1 | IsBarring            | The connection is currently blocking the commodity.                                                                    |
|           5 | AlwaysBarring        | The barrier cannot be operated and is always barring                                                                   |
|          -5 | AlwaysConducting     | The barrier cannot be operated and is always conducting                                                                |
|          10 | AutonomousBarring    | It is normally blocked but the Smart Grid can turn it on.                                                              |
|         -10 | AutonomousConducting | It is normally conducting but the Smart Grid can turn it off.                                                          |
|          15 | AlwaysBarring        | It is normally blocked but the Smart Grid can turn it on.                                                              |
|         -15 | AlwaysConducting     | It is normally conducting but the Smart Grid can turn it off.                                                          |

