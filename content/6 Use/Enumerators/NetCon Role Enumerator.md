---
title: NetCon Role Enumerator
description: Encoding the role types as used in NetCon.
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# NetCon Role Enumerator

Enumerator encoding the role types as used in NetCon.
These are actually bitflags and can be combined, e.g. 2+4=6.
The definition and contents of the table is standard and should not be altered.

| RoleType | RoleTypeValue | Description |
| -------: | ------------- | ----------- |
| 0        | Unknown       | Assumed to have a transport role. |
| 1        | Transport     | Designated to have a transport role. |
| 2        | Producer      | Origin of the commodity. In typical circum stances producers are the source. |
| 4        | Consumer      | Consumer or load or the network. Sink of the commodity. Flow towards here is considered downstream. |
| 6        | Prosumer      | Both a producer and a consumer, such as a service point that also has PH-panels. |
| 8        | Source        | Considered a start for tracing. Flow from here is regarded as upstream, typically where the commodity is produced in large quantities to determine downstream /  flow direction. The sources are often point objects and should match the users interpretation of flow. Typically these are power plants, either or hv-transformers, or circuit-breakers. |
| 10       | Factory       | Both source and producer, such a where the commodity is made. |
| 16       | Reservoir     | Facility that can store, hold or buffer the commodity, which is different from being a prosumer in terms of service. |
| 22       | Backup        | Both reservoir and prosumer such as a large battery facility that can assist powering the network. |

