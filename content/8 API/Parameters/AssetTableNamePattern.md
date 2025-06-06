---
title: AssetTableNamePattern
description: Name of the asset table in the NetConConnection table. It may contain [[Wildcards|Wildcards]] if you want to search more than one table. If this parameter is kept empty (no name and no pattern), it will change the interpretation of the [[AssetId|AssetId]] parameter.
Type: string
Mandatory: false
Order: 10
permalink: 
aliases:
  - Parameters/AssetTableNameWildCard
draft: false
date: 2025-02-20
tags:
  - ApiParameter
  - AssetTableName
  - AssetTableNamePattern
---
# AssetTableNamePattern

Type of: _string_
Mandatory: __

Name of the asset table in the NetConConnection table. It may contain [[Wildcards|Wildcards]] if you want to search more than one table. If this parameter is kept empty (no name and no pattern), it will change the interpretation of the [[AssetId|AssetId]] parameter.

## Examples
Let's consider that the following assettablename(s) exist:
* e_lv_cable
* e_mv_cable
* e_pl_cable

| Example input         | Meaning it will match                            |
| --------------------- | ------------------------------------------------ |
| e_lv_cable            | Only the `e_lv_cable`                            |
| e_?v_cable            | Both `e_lv_cable` and `e_mv_cable`.              |
| e_\*_cable            | All `e_lv_cable`, `e_mv_cable` and `e_pl_cable`. |
| e_lv_cable,e_pl_cable | Both `e_lv_cable` and `e_pl_cable`.              |

