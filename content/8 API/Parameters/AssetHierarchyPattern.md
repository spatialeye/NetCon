---
title: AssetHierarchyPattern
description: "[[NetConQL - Specification|NetConQL - Specification]] expression for AssetHierarchy properties, for example `substation.id=3,4 OR installation.id=17`. If enrichment is used, for other properties may be added such as substation.name, and the expression could be `substation.name=*FIELDS OR installation.id=17` which will match any substation whose name ends in FIELDS or has installation.id=17."
Type: string
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2025-01-17
tags:
  - ApiParameter
  - AssetHierarchyPattern
  - AssetHierarchy
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
# AssetHierarchyPattern

Type of: _string_
Unique: __

[[NetConQL - Specification|NetConQL - Specification]] expression for AssetHierarchy properties, for example `substation.id=3,4 OR installation.id=17`. If enrichment is used, for other properties may be added such as substation.name, and the expression could be `substation.name=*FIELDS OR installation.id=17` which will match any substation whose name ends in FIELDS or has installation.id=17.
