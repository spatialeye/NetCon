---
title: NetCon EdgeType Enumerator
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# NetCon EdgeType Enumerator

Enumerator encoding the edge types as used in NetCon.
The definition and contents of the table is standard and should not be altered.

| EdgeType | EdgeTypeValue | Description                                                                                                                                  |
| -------: | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
|        0 | SelfLoop      | Originated from a point asset. FromId and ToId will be the same. Typically geometryp is set.                                                 |
|        1 | Link          | Originated from a line asset. FromId and ToId cannot be the same. Typically geometryl is set.                                                |
|        2 | Terminal      | Generated between point and line asset for point asset that needs terminals. FromId and ToId cannot be the same. Typically without geometry. |

