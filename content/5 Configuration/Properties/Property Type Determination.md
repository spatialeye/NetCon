---
title: Property Type Determination
description: 
permalink: 
aliases: 
draft: false
date: 2025-03-20
tags:
  - ToDo
---
# Property Type Determination

When the type of a value has to be determined, e.g. in [[../../7 NetConQL/NetConQL - Network Connection Query Language|NetConQL - Network Connection Query Language]], this in done depended on the value.

## Property names with fixed types

Certain property names will have a type that is predetermined and cannot be changed. E.g.

| PropertyName   | Type                       |
| -------------- | -------------------------- |
| Role           | [[../../6 Use/Enumerators/NetCon Role Enumerator|NetCon Role Enumerator]]     |
| Barrier        | [[../../6 Use/Enumerators/NetCon Barrier Enumerator|NetCon Barrier Enumerator]]  |
| Flow           | [[../../6 Use/Enumerators/NetCon Flow Enumerator|NetCon Flow Enumerator]]     |
| Cost           | Double                     |
| AssetTableName | String                     |
| AssetId        | Long                       |
| CustomAssetId  | String                     |
| Status         | [[../../6 Use/Enumerators/NetCon Status Enumerator|NetCon Status Enumerator]]   |
| Label          | String or GUID (future)    |
| Owner          | String                     |
| OperatedBy     | String                     |
| EdgeType       | [[../../6 Use/Enumerators/NetCon EdgeType Enumerator|NetCon EdgeType Enumerator]] |
## Definition determined types

It is possible for a specific field name (optionally only in the context of a parent tree property).
See [[./Property Type Definition|Property Type Definition]].

## Enriched types

During enrichment, the type information is derived from the field type as configured in the Business Collection.
See [[../Enrichment/Asset Enrichment|Asset Enrichment]].
## Inferred types

When a value is being parsed, the following rules are used for inference of the type.

| Order | Pattern                                                                                | Type     |
| ----- | -------------------------------------------------------------------------------------- | -------- |
| 1     | Enclosed in single or double quotes                                                    | String   |
| 2     | Matching date or date/time format. See examples below                                  | DateTIme |
| 3     | Number that does contain a decimal separator `.`<br>Culture settings are ingnored.     | Double   |
| 4     | Number that does not contain a decimal separator `.`<br>Culture settings are ingnored. | Long     |
| 5     | True or False                                                                          | Boolean  |
| 6     | Other                                                                                  | String   |

#ToDo
Date examples

    "2005.09.14", 2005, 9, 14)] 
    "2005.9.14", 2005, 9, 14)
    "2005-09-14", 2005, 9, 14)
    "2005/09/14", 2005, 9, 14)
    "14-09-05", 2005, 9, 14)
    "14-09-2005", 2005, 9, 14)
    "2005 09 14", false, 2005, 9, 14)
    "2005 SEP 14", false, 2005, 9, 14)
