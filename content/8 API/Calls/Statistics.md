---
title: Statistics
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags:
  - Statistics
  - ApiMetaCall
  - ApiCall
---
# Statistics

The Statistics API call will travel the network to retrieve how often certain aspects occur.

The results will be grouped by Network, Flow, or Property.

For each group of statics, it will report:

* Message: what has been counted
* Count: how many connections occur for `message`
* Percentage: how many as part of the total
* SumCost: the summed up cost of the connections with `message`
* CostPercentage: cost as part of the total

## Network

The total number of elements and their summed up cost of:

* [[../../6 Use/DataModel/NetCon Connection|Connection]] network
* [[../../5 Configuration/Sectioning and Tracing/Sections/Isolatable Sections|Isolatable Sections]] network
* [[../../5 Configuration/Sectioning and Tracing/Sections/Operated Sections|Operated Sections]] network
* [[../../5 Configuration/Sectioning and Tracing/Sections/Control or NetCongestion Section|Control or NetCongestion Section]] network
* [[../../5 Configuration/Sectioning and Tracing/Sections/Custom Sections|Custom Sections]] network

## Flow

Computes from the flow of the elements in the network:

| Flow          | Description                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------- |
| noFlowCount   | elements that are not connected to, or blocked from, a source                                   |
| directedCount | elements that are directed as down- or upstream                                                 |
| mazedCount    | elements that are marked as mazed-stream, i.e. the flow can come from both the from and to node |

## Properties

Statistics are reported for the following properties.
By default, the following statistics are returned:

* [[../Results/Connection Or Path Results/AssetTableName|AssetTableName]]
* [[../Results/Connection Or Path Results/Role|Role]]
* [[../Results/Connection Or Path Results/Barrier|Barrier]]
* [[../../3 Overview/Commodity|Commodity]]
* [[../Results/Connection Or Path Results/EdgeType|EdgeType]]
* [[../Results/Connection Or Path Results/Status|Status]]
* [[../Results/Connection Or Path Results/Owner|Owner]]
* [[../Results/Connection Or Path Results/OperatedBy|OperatedBy]]

In addition, you can provide your own `PropertyExpression` as a parameter.
If provided, only statistics for that expression are returned.

## Parameters
| File                                                                   | type   | mand  | description                                                                                                                                                               |
| ---------------------------------------------------------------------- | ------ | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/NetworkName\|NetworkName]]               | string | false | Optional name of the network, in case the server hosts more than one. For default see [[Default parameters in the API|Default parameters in the API]]. For example `E`, `E_DQ`, `E_NRT` or `E_Plan_St`. |
| [[../Parameters/PropertyExpression\|PropertyExpression]] | string | false | Optional expression that leads to a property. It is possible to use the drill down operator, e.g. Commodity->Net or Specification->CoreMaterial.                          |

