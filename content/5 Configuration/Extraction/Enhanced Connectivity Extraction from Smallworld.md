---
title: Enhanced Connectivity Extraction from Smallworld
description: 
permalink: 
aliases: 
draft: false
date: 2024-10-01
tags:
  - VMDS
  - Smallworld
  - Connectivity
  - Extraction
---
# Enhanced Connectivity Extraction from Smallworld

  
## Combining topologies from different datasets

In case one has several datasets containing connectivity, these can be combine into a single connectivity model, as long as all the base tables are combined. This is the case when someone has both gas transmission and distribution networks.

So, for GDO and GTO, one can decide to combine these into a single one. For this to be connected, a hyperlink table has to be created (using the template described above). This hyperlink table combines GDO and GTO hypernodes.

## Electric Office

Special support is required for the `eo_isolating_equipment_installation`.
## PNI

