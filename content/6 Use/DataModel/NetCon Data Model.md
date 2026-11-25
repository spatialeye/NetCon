---
title: NetCon Data Model
description:
permalink:
aliases:
draft: false
date: 2024-10-02
tags:
---
# NetCon Data Model


### NetCon Base Model Tables


> [!Warning] Deprecated Tables
> 
The NetConBase tables are just for transferring the information from one processing phase to the next and are likely to disappear in the future. Hence, you should _never_ use them for other usages that data quality inspection and data lineage research.

The NetConBase tables are just for transferring the information from one processing phase to the next and are likely to disappear in the future. Hence, you should _never_ use them for other usages that data quality inspection and data lineage research.

Note that the NetConBase logical warehouse model is created with the option 'history' set to 'false'. In other words, for now, we do not process delta's going from NetConBase to NetConModel.

The output of the netcon-base ETL configuration is stored in several tables, that are described below.

Three connectivity extraction tables:

- NetConBaseNode: The unionized information from all node assets, combined with the topology model.
- NetConBaseLink: The unionized information from all link assets, combined with the topology model.
- NetConBaseHyperLink: The unionized information from all the hyperlinks.

Lookup tables and fields:

- Rwo Definition
- Manifold Definition
- Geom Attribute Definition

### NetCon Atomic Model Tables

Table storing all connectivity

* [[./NetCon Connection|NetCon Connection]]

Lookup tables and fields:

- [[./Registration Asset Table Definition|Registration Asset Table Definition]]
- [[./Registration Connectivity Group Definition|Registration Connectivity Group Definition]]
- [[./Registration Geometry Definition|Registration Geometry Definition]]

