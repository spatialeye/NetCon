---
title: Geom Attribute Definition
description: 
permalink: 
aliases: 
draft: false
date: 2025-03-25
tags: 
---
# Registration Geometry Definition

Old name: Geom Attribute Definition.

List of Geometry Attributed Codes as definitions from the source system.
This table is filtered to depict only those geometry attributes that are part of a manifold, i.e. the ones without a manifold code are lett out.
The definition of the table contents is standard and should not be altered.

| Field                     | Type    | Description                                                                                                                                                                                                             |
| ------------------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Id                        | integer | Positive integer representing the Id of a geometry attribute for a particular table (or real-world object definition). Typically, the first spatial attribute is nr 1, the second is nr 2, etc. Old name `GeomAppCode`. |
| AssetTableId              | integer | Positive integer representing the Id of a table in the source system.                                                                                                                                                   |
| ConnectivityRuleGroupId   | integer | Positive integer representing the Id of a connectivity rule group (aka manifold) in the source system.                                                                                                                  |
| GeometryType              | string  | What kind of geometry is stored in the corresponding geometry attribute. This is one of Point, Line, Area, since all other geometry types are not part of a manifold and thus filtered out.                             |
| Name                      | string  | String internal name of the geometry attribute in the source system.                                                                                                                                                    |
| AssetTableName            | string  | String internal name of a table in the source system. Old name `RwoDefintion`.                                                                                                                                          |
| ConnectivityRuleGroupName | string  | String internal name of the topology interaction group in the source system.                                                                                                                                            |

