---
title: DataQuality
description: Return counts of islands, missing nodes, supernumerary nodes and supernumerary links in the network.
permalink:
aliases:
draft: false
date: 2025-04-18
tags:
  - DataQuality
  - ApiMetaCall
  - ApiCall
---
# DataQuality

The DataQuality API provides summaries of a set of data quality problems that can be found in the data.

See also [[../../6 Use/Data Quality/Data Quality Analysis Collections|Data Quality Analysis Collections]], which provide a detailed look into the problems.

## Parameters
| File                                                     | type   | mand  | description                                                                                                                                                               |
| -------------------------------------------------------- | ------ | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/NetworkName\|NetworkName]] | string | false | Optional name of the network, in case the server hosts more than one. For default see [[Default parameters in the API|Default parameters in the API]]. For example `E`, `E_DQ`, `E_NRT` or `E_Plan_St`. |
| [[../Parameters/Aspect\|Aspect]]           | string | false | Enum to select what data quality aspect will be computed. If none is provided, all are computed.                                                                          |

