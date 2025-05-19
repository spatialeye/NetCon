---
title: Section Model configuration
description: 
permalink: 
aliases: 
draft: false
date: 2024-10-02
tags: 
---
# Section Model configuration

Sections are produced by the Cluster feature source. The Cluster feature source takes 1 parameter:

| Parameter | Value | Meaning |
| --------- | ----- | ------- |
| Query or business collection | 'Connection' | A query or business collection must be defined in the project with the name provided which is used as input for the sectioning. The advantage of providing a query over a collection is that it can be ordered ascending on 'ConnectionId'. This provides a slight performance benefit.
| Other parameter | N/A | Previously provided parameters are deprecated and will be ignored.

A ready-to-go template seProject file is provided for clustering or sectioning the network. It will take care of producing Isolatable Sections that consist of Connections.
Optionally, in the same batch process, one can generate higher order sections that consist of Isolatable Connections. See also (up ToDo).

The configuration for additional sections is stored under the seProject file in a file with the pathname: `.\Data\SuperSections.json`

The meaning of section clustering options is explained in the table below:

| Option | Meaning  |
| ------ | -------- |
| Id                | Increasing, unique order number identifying the definition.
| SsInternalName    | Internal collection name of the section table that appears under the clustering feature source.
| SsExternalName    | External collection name of the section table that appears under the clustering feature source.
| NamingCutterField | Every connection that clusters the sections can possibly provide its 'name' or 'label' to the downstream cluster that follows it. Optionally this parameter can provide the name of a boolean field that tells if a name is provided by this collection. For example, 'IsSuperCutter' on 'Connection' can be true when it is barring or is a LV/MV transformer.
| CutterField | Name of the boolean field that denotes if the resulting section is barring. E.g. 'IsSuperBarrier' is true just when it is barring.
| MergeStrategy | 'None', which is the default meaning that every Isolating Section is part of at most one higher order section, or 'CopyCutterToNeighbours' which is provided for compatibility reasons and deprecated now. When the 'MergeStrategy' is set to 'CopyCutterToNeighbours', the Isolated Section cutting up the cluster, i.e. a transformer, is made part of its neighbors as well. To denote which is the neighbor addition, 'referenceType' is set to '1' for those relations.
| CalcUpstream | Boolean to denote if you want to obtain a upstream relation table linking each section to the previous one that is feeding it. It is computed breadth first starting from the source.
| CalcDownstream | Boolean to denote if you want to obtain a downstream relation table linking each section to the next one that is fed from it. It is computed breadth first starting from the source.
| OmitEmpty | False by default. If true, then sections without a 'name' will be omitted from the result. Typically, because names are provided by the labels of the important barring objects, having no name means it is something that is not fed, has no source, meaning it is an island.

The 'SuperSections.json' file specifies one group of entries have one item for each additional section type that is generated.

        [
           {
             "Id": 1,
             "SsInternalName": "super",
             "SsExternalName": "Super Section",
             "NamingCutterField": "IsSuperCutter",
             "CutterField": "IsSuperBarrier",
             "MergeStrategy": "None",
             "CalcUpstream": "True",
             "CalcDownstream": "False",
             "OmitEmpty": "False"
           },
           {
             "Id": 2,
            ...
           }
         ]

As described in the options table above, the deprecated merge strategy is:

             "MergeStrategy": "CopyCutterToNeighbours",

If you want the upstream relationship to be present:

             "CalcUpstream": "True",
             "CalcDownstream": "False",

If you want the downstream relationship to be present:

             "CalcUpstream": "False",
             "CalcDownstream": "True",

If you are using labels for naming sections and are not interested to have sections that are not fed:

             "OmitEmpty": "True"

The cluster feature source will produce a number of tables.

#### Isolatable Section

This is a mandatory table. For compatibility this table is called 'NetConSection'.

| Field | Meaning |
| ----- | ------- |
| SectionId | Unique id, generated as Min(ConnectionId) of its contents. |
| From Id | Node Id where isolatable section starts from. |
| To Id | Node Id where isolatable section goes to. |
| Role | Enumerator denoting rol of isolated section in network. See also [Role](Section%2520Model%2520configuration.md##netcon-role). |
| Is Barrier | Enumerator. 0 if not a barrier, 1 if barring and section is 'off', -1 if it can be barring but connection is 'on', i.e. conducting. Other values reserved for the future. |
| Label | Identifies a name for the section, typically the barrier asset through which it is fed. |

#### SectionToConnection

This is a relation table, that links active (in use, i.e. 0 <= StatusCode <= 10) connections to Isolatable Sections:

| Field | Meaning |
| ----- | ------- |
| SectionId | Id of the Isolated Section. |
| Connection Id | Id of the connection where connection starts from. The 'Id' of the Connection table is a field generated by Spatial Warehouse and looks like 'se_history_rootid.' |

#### Operated Section

This is an optional table that is strongly recommended. For compatibility this table is called 'NetConSuperSection'.

| Field | Meaning |
| ----- | ------- |
| SuperSectionId | Unique id, generated as Min(SectionId) of its contents. |
| From Id | Node Id where operated section starts from. |
| To Id | Node Id where operated section goes to. |
| Role | Enumerator denoting rol of operated section in network. See also [Role](Section%2520Model%2520configuration.md##netcon-role). |
| Is Barrier | Enumerator. 0 if not a barrier, 1 if barring and section is 'off', -1 if it can be barring but connection is 'on', i.e. conducting. Other values reserved for the future. |

#### SuperSectionToSection

This is a relation table, that Isolatable Sections their Operated Section:

| Field | Meaning |
| ----- | ------- |
| Super Section Id | Id of Operated Section. |
| Section Id | Id of the Isolated Section. |
| Reference Type | '0' in normal cases, '1' for Isolated Sections distributed to their neighbors. See also 'CopyCutterToNeighbours'. |

