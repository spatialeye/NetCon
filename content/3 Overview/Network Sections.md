---
title: Network Sections
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Clustering
  - Section
  - Overview
  - NetCon2
---
[[./Referential Information|previous]] [[../index#Getting started|next]]
# Clustering the Network into Sections


Part of NetCon model is that the operated network is pre-traced into **isolatable_sections**. An isolatable section is a part of the network that is operated as one: there is no way of supplying the commodity to a smaller part of the network unless the network is broken or cut up. 

Examples of a network being cut up are when an overhead wire is broken by a falling tree, or when a gas network is operated by inserting a blocking balloon. Which connection can be `cut up` are specified by the `cut up` expression on the `NetConBase` feature source. A cut up network will still provide commodity service to the upstream network, whilst

```mermaid
---
title: Class diagram of the NetCon graph
---
classDiagram
    class Connection {
        Connections ConnectsTo()
        Connections ConnectsFrom()
        Bool? IsBarrier()
        Bool IsBiDirectional()
        +String SourceKey
        +Long FromNodeId
        +Long ToNodeId
        +bool BiDirectional
        +Double Cost
        +Json Commodity
        +Enum EdgeType
        +Enum Role
        +Enum Status
        +Enum Barrier
        +MultiPoint GeometryP
        +MultiCurve GeometryL
        -String Label
        -String Owner
        -String OperatedBy
        -JSon AssetHierarchy
        -JSon Specification
    }
    
    class IsolatableSection {
        +Long IsolatableSectionId
        +Long FromNodeId
        +Long ToNodeId
        +bool BiDirectional
        +Enum Barrier
        +Enum Role
        +Double Cost
        -JSon Commodity
        -String Label
        -Long LowerOrderFromNodeId
        -Long LowerOrderToNodeId
        Sections ConnectsTo()
        Sections ConnectsFrom()
        Bool IsSource()
        Bool? IsBarrier()
    }
    
    Connection o-- IsolatableSection : Aggregates
    IsolatableSection *-- AbstractSuperSection
    AbstractSuperSection <|-- OperatedSection
    AbstractSuperSection <|-- ControlSection
    AbstractSuperSection <|-- CommoditySection
  end
```

## 1st level higher order or Isolatable Section Network

IsolatableSection is either:
* A cluster of connections that are not barriers nor bidirectional, or
* A singular path of connections that are barriers or unidirectional.

This way, the Isolatable Section Network forms a network in its own right. The non-barrier connection clusters have:
* FromNodeId = ToNodeId

Wherease for the paths of barriers or directed connections holds:
* FromNodeId ≠ ToNodeId

## 2nd level higher order or super sections

The AbstractSuperSection consist of subsets of 1 or more IsolatableSection:
* OperatedSection: Aggregates how the network is currently operated, i.e. determined by if a barrier is barring (a new Operated Section) or conducting (in one and the same Operated Section). Optionally the Operated Sections may split by a change commodity-subnetwork, such as HV -> MV or MV -> LV.
* ControlSection: Aggregates how the network is operated, and in addition it is split by the important barriers (e.g. switches) that follow a particular upstream condition, such as e.g. a busbar, installation, or block.
* CommoditySection: Aggregates how the network is operated, and in addition contains customs splits or upstream conditions.

## Storage into the database
The NetCon 2.0 way to store this in the database is the following:

```mermaid
erDiagram
  NetConConnection {
    long HistoryRootId PK "Aka the Id of the Connection"
    string HistorySourceKey UK "Original key of the Connection"
    long FromNodeId
    long ToNodeId
    bool BiDirectional
    double Cost
    enum Barrier
    enum Role
    enum EdgeType
    enum Status
    string Label
    Json Commodity
    MultiPoint GeometryP
    MultiCurve GeometryL
    string AssetTabelName FK
    long AssetId FK
    string CustomAssetId FK
    Json Specification
    Json AssetHierarchy
    string Owner
    string OperatedBy
  }
  
  NetConConnectionRelation {
    long Id PK
    long IsolatableSectionId FK
    long OperatedSectionId FK
    long ControlSectionId FK
    long CommoditySectionId FK
    enum Flow
  }
  
  NetConNode {
    long HistoryRootId PK "Aka the Id of the Node"
    string HistorySourceKey UK "Original key of the Node"
    long NodeId
    Point GeometryP
  }
  
  NetConIsolatableSection {
    long Id PK
    long FromNodeId
    long ToNodeId
    bool BiDirectional
    double Cost
    enum Barrier
    enum Role
    string Label
    Json Commodity
    long LowerOrderFromNodeId
    long LowerOrderToNodeId
    long PrimeConnectionId FK
  }
  
  NetConIsolatableSectionRelation {
    long Id PK
    long OperatedSectionId FK
    long ControlSectionId FK
    long CommoditySectionId FK
    enum Flow
  }
  
  NetConOperatedSection {
    long Id PK
    long FromNodeId
    long ToNodeId
    bool BiDirectional
    double Cost
    enum Barrier
    enum Role
    string Label
    Json Commodity
    long LowerOrderFromNodeId
    long LowerOrderToNodeId
    long PrimeConnectionId FK
  }
  
  NetConControlSection {
    long Id PK
    long FromNodeId
    long ToNodeId
    bool BiDirectional
    double Cost
    enum Barrier
    enum Role
    string Label
    Json Commodity
    long LowerOrderFromNodeId
    long LowerOrderToNodeId
    long PrimeConnectionId FK
  }

  NetConCustomSection {
    long Id PK
    long FromNodeId
    long ToNodeId
    bool BiDirectional
    double Cost
    enum Barrier
    enum Role
    string Label
    Json Commodity
    long LowerOrderFromNodeId
    long LowerOrderToNodeId
    long PrimeConnectionId FK
  }

  NetConConnection }|--|| NetConNode : connects_from
  NetConConnection }|--|| NetConNode : connects_to

  NetConConnection ||--|o NetConConnectionRelation : part_of
  NetConConnectionRelation }|--|| NetConIsolatableSection : has
  NetConConnectionRelation }|--o| NetConOperatedSection : has
  NetConConnectionRelation }|--o| NetConControlSection : has

  NetConIsolatableSection o|--|o NetConIsolatableSectionRelation : part_of
  NetConIsolatableSectionRelation }|--o| NetConOperatedSection : has
  NetConIsolatableSectionRelation }|--o| NetConControlSection : has
  NetConIsolatableSectionRelation }|--o| NetConCustomSection : has

  NetConConnectionRelation }|--o| NetConCustomSection : has
```



