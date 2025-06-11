---
title: Commodity Rules
description: 
permalink: 
aliases: 
draft: false
date: 2025-06-05
tags: 
---
# Commodity Rules

If *no* commodity rules are provided, it is assumed that every [[../../3 Overview/Networks/Commodity|Commodity]] of a connection can be provided by its neighbouring connections leading to it. In other words, starting from a source and going down stream, if a connection can be reached and has a commodity set, than it is assumed that commodity is going through that connection. The [[../../8 API/Results/Connection Or Path Results/Flow|Flow]] is established that way, going from the [[../../3 Overview/Networks/Sources|Source]] to other connections in the network.

If a node can be reached via different paths, i.e. it is fed from a Source via more than one connection, the entire Cycle is marked as having a meshed flow. For example, if two transformers are feeding the same part of the network, or if a section of a gas network is connected to two pressure regulating stations.

In some situations, several cables are in parallel. Since this creates a cycle in the graph, the parallel cables will be marked as meshed. For example, see below the cables going to this small substation.

![[../../Zimages/single _phase_cables_without_commodity_rules 1.png|single _phase_cables_without_commodity_rules 1.png]]
When we look at the commodities going through these cables, we see that the they are transporting MV (medium voltage), phase A, B, C individually. The substation connectors and busbar are phase ABC combined.

## Normal commodity rule

By adding the following rules, we can avoid that the downstream flow from the substation is detected as a meshed flow:

| Discipline | From Commodity Pattern | To Commodity Pattern | Add reverse? |
| ---------- | ---------------------- | -------------------- | ------------ |
| E          | ::ABC                  | ::A                  | false        |
| E          | ::ABC                  | ::B                  | false        |
| E          | ::ABC                  | ::C                  | false        |

As we see, the flow is no longer meshed, but also the first connector where power comes in, which is ABC, is no longer fed from in individual cables, since ABC can not be fed from the individual phases.
![[../../Zimages/single _phase_cables_with_normal_commodity_rules.png|single _phase_cables_with_normal_commodity_rules.png]]


## Combine commodity rule

By adding the a combine rule, we enable that downstream commodities can become a combination of their upstream feeders. 

| Discipline | From Commodity Pattern 1 | From Commodity Pattern 2 | From Commodity Pattern 3 | To Commodity Pattern | Add reverse? |
| ---------- | ------------------------ | ------------------------ | ------------------------ | -------------------- | ------------ |
| E          | ::A                      | ::B                      | ::C                      | ::ABC                | false        |

With all these rules together, we get what we want:

![[../../Zimages/single _phase_cables_with_combine_and_normal_commodity_rules.png|single _phase_cables_with_combine_and_normal_commodity_rules.png]]

## Defining commodity rules

The NetConCommodityTransitionRule collection has the following definition:

| FieldName | FieldType                                                              | Optional |
| --------- | ---------------------------------------------------------------------- | -------- |
| Disciplin | Letter denoting [[../../3 Overview/Networks/Disciplin|Disciplin]], e.g.                                    | No       |
| FieldType | String. Values must be one of: String, DateTime, Double, Long, Boolean | No       |
| Unit      | String, e.g. `m` for meter or `m2` of squared meter.                   | Yes      |

A typical summary of all rules is provided in the table below.
In your configuration, you can load these as a CSV-file, or into your data warehouse.

Note that for the combination rule (the last line in the table), the individual from patterns that are combined, are written together and separated by a ','.

| Disciplin | CommodityPatternFrom | CommodityPatternTo | AddReverse | Comment                                                                    |
| --------- | -------------------- | ------------------ | ---------- | -------------------------------------------------------------------------- |
| E         | HS:\*:               | HS:\*:             | true       |                                                                            |
| E         | HS:\*:               | MS:\*:             | true       | Only allowed at installations.                                             |
| E         | HS:\*:\*             | MS:\*:\*           | true       | Only allowed at installations.                                             |
| E         | MS:\*:               | MS:\*:             | true       |                                                                            |
| E         | MS:\*:               | LS:\*:             | true       | Only allowed at installations.                                             |
| E         | MS:\*:\*             | LS:\*:\*           | true       | Only allowed at installations.                                             |
| E         | LS:\*:               | LS:\*:             | true       |                                                                            |
| E         | LS:\*:               | OV:\*:             | false      | Only allowed at ignition installations.                                    |
| E         | LS:\*:\*             | OV:\*:\*           | false      | Only allowed at ignition installations.                                    |
| E         | ::ABC                | ::A                | false      |                                                                            |
| E         | ::ABC                | ::B                | false      |                                                                            |
| E         | ::ABC                | ::C                | false      |                                                                            |
| E         | ::ABC                | ::U                | false      |                                                                            |
| E         | ::ABCN               | ::A                | false      |                                                                            |
| E         | ::ABCN               | ::B                | false      |                                                                            |
| E         | ::ABCN               | ::C                | false      |                                                                            |
| E         | ::ABCN               | ::N                | false      |                                                                            |
| E         | ::ABCN               | ::U                | false      |                                                                            |
| E         | ::ABCN               | ::ABC              | true       | We assume the reverse, because the neutral is often not inserted properly. |
| E         | ::A                  | ::U                | false      |                                                                            |
| E         | ::B                  | ::U                | false      |                                                                            |
| E         | ::C                  | ::U                | false      |                                                                            |
| E         | ::A,::B,::C          | ::ABC              | false      | Three phase ABC can be combined into one.                                  |
