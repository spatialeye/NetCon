---
title: NetCon feature sources
description: 
permalink: 
aliases: 
draft: true
date: 2024-10-17
tags: 
---
# NetCon feature sources


| Name              | Purpose                                                                                                                                              |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| NetConBase        | Common behavior for inheritance. Abstract class that cannot be instantiated.                                                                         |
| NetConExtract     | To build NetConConnections from an arbitrary sources                                                                                                 |
| NetConExtractVMDS | To build NetConConnections from a VMDS sources                                                                                                       |
| NetConTrace       | To build & expose tracing behavior on top of NetConConnections.<br>This will also cluster/section the network into Isolatable and Operated Sections. |

