---
title: Purpose and Examples
description: 
permalink: 
aliases:
  - single source of truth
  - data morphing
draft: false
date: 2024-09-27
tags:
  - single_source_of_truth
  - data_morphing
  - Overview
---
[[./Use Cases|previous]] [[./Data Flow Example 1|more]] [[./Solution Architecture|next]]
# Purpose and Examples

The *first* purpose of NetCon is to be the **single source of truth for network connectivity** - sometimes called network topology - to provide a vehicle for time-based working with any commodity network in a generic way, provisioning information exchanged with all consumers of the network connectivity data. As such, it provides a graph of atomic (indivisible) connections.

It is very hard to alleviate the data quality of a network's connectivity to a high level, or even to a sufficient level. By being a single source of truth for many specific purposes at the same time, every effort to increase data quality for one consumer system will increase the data quality for all. The *second* purpose of NetCon is to be the vehicle for increasing the data quality of the network connectivity.

The *third* purpose of NetCon is to facilitate the use the network connectivity in all consuming systems. Because no compromises can be made for a particular purposes, we have developed standard techniques to store, validate, query, trace, morph and report the network's connectivity.

> [!Important] First results
A remarkable result of the very first rollout of NetCon was, directly after the first implementation at the first customer, that the data quality in NetCon was overall 5% better (because it is using every source of connectivity) than in the previous extraction system, and also that is was 2.5% worse (because NetCon was set to limit the 'as serviced' network to just assets that are in use and excluded those that are planned or out of service. The 2.5% degradation was because of cases where the assets were stored in the source system with the wrong asset life cycle, which was easily fixable, because it was clear that the serviced customer were serviced via assets that were in service.

We have already seen much positive proof that a standard approach brings benefit and higher data quality to all consumers of NetCon. By being a standard model, many 'ready to go' applications can be developed that will be able to provide functionality for working with the network (see business cases). This is easily said, but not easily done, because the source data can be registered in quite different systems, in quite different ways. Therefore, NetCon is equipped with many options to morph or tailor the data to its consuming applications.

The following four examples illustrate this *third* purpose.
1. [[./Data Flow Example 1|more]] - Data flow example I: From GIS valve to simple flow calculation
2. [[./Data Flow Example 2|Data Flow Example 2]] - From ambiguous GIS valves information to flow calculation
3. [[./Data Flow Example 3|Data Flow Example 3]] - From GIS T-piece to simple flow calculation
4. [[./Data Flow Example 4|Data Flow Example 4]] - From GIS T-piece to Common Information Model

Please see here for [[./Tracing and Querying/Basic network tracing|Basic network tracing]] and here for the [[../7 NetConQL/NetConQL - Network Connection Query Language|NetConQL - Network Connection Query Language]].