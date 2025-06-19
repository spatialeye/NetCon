---
title: Introduction
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
---
[[./Copyright and Usage|previous]] [[../2 Version And Release Information/Version Information|next]]
# Introduction

The NetCon model and its logic have been created by Spatial Eye to **reason about networks** and provide **a single source of truth for network information** in the organisation. Networks can be electricity, gas, water, heath, sewage or telecom networks, or other commodities that can be transported.

![[../Zimages/example_electricty_network.png|example_electricty_network.png]]

Examples of reasoning about a network are:
- **Digital twin:** does continuous calculations to know the current state of the network and which simulates new states of the network;
- **Advanced Distribution Management System: (ADMS)** is used for daily operation of the grid;
- **Outage Management System:** is used for monitoring, fault diagnoses and service restoration.

Typically, networks are represented as a graph. Below an example is shown. This graph is non-directed and 'single' in nature (a radial network) as opposed to 'multi' graphs that have several connections between nodes forming loops (for meshed networks).

```mermaid
---
title: Example graph
---
mindmap
s((substation S))
  MV station A0
    LV station A1
    MV station A2
      LV station A3
    MV station A4
      LV station A5
  MV station B0
    MV station B1
      LV station B2
    MV station B3
      MV station B4
        LV station B5
      LV station B6
    LV station B7
  MV station C0
    MV station C1
      MV station C2
        LV station C3
        LV station C4
        LV Station C5

```

Please note that the text and programs in NetCon are protected by [[./Copyright and Usage|previous]].