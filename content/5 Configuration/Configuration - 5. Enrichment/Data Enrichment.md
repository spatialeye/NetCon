---
title: Data Enrichment
description:
permalink:
aliases:
draft: false
date: 2024-10-01
tags:
---
# Data Enrichment

The NetCon models can work with data which is outside of its tables, by following a certain convention in business collection naming.
Enrichment is handled by the NetConTrace feature source, so for this to work, you must add this to your configuration (or use the template that is provided).

For specifications (typically references to type tables) and asset hiearchy objects (for example busbar or substation information), this information is read when the NetConTrace feature source starts up.
For additional asset information, this information is read when Trace results are produced (either by expressions or the TraceAPI).

NetCon support three types of enrichment:

* [[./Specification Enrichment|Specification Enrichment]]
* [[./Asset Hierarchy Enrichment|Asset Hierarchy Enrichment]]
* [[./Asset Enrichment|Asset Enrichment]]

These enrichment are delivering strong typed data.
That means if a field is a `String`, `Boolean`, `Long`, `Double` or `DateTime`, the property will get the same data type.