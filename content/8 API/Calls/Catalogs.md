---
title: Catalogs
description: Returns all NetCon catalogs and enumerator values.
permalink:
aliases:
draft: false
date: 2025-01-17
tags:
  - "#ApiMetaCall"
  - ApiCall
  - Catalogs
  - ApiMetaCall
---
# Catalogs

Future function that will return all catalogs and enumerators in the NetCon network.
Part of the [[../../2 Version And Release Information/2.3 Roadmap|2.3 Roadmap]].

The following catalogues with their values and descriptions will be returned:
* [[../../3 Overview/3.5 Commodity Networks/Disciplin|Network Disciplin]]
* [[../../6 Use/Enumerators/NetCon Status Enumerator|NetCon Status Enumerator]]
* [[../../6 Use/Enumerators/NetCon Role Enumerator|NetCon Role Enumerator]]
* [[../../6 Use/Enumerators/NetCon Barrier Enumerator|NetCon Barrier Enumerator]]
* [[../../6 Use/Enumerators/NetCon Flow Enumerator|NetCon Flow Enumerator]]
* [[../../6 Use/Enumerators/NetCon EdgeType Enumerator|NetCon EdgeType Enumerator]]
* [[../../6 Use/Enumerators/NetCon TraceFunction Enumerator|NetCon TraceFunction Enumerator]]
* [[../../6 Use/Enumerators/NetCon TraceMode Enumerator|NetCon TraceMode Enumerator]]
* [[../../6 Use/Enumerators/NetCon TraceMarker Enumerator|NetCon TraceMarker Enumerator]]
* [[../../6 Use/Enumerators/NetCon TraceResultExpandPathsMode Enumerator|NetCon TraceResultExpandPathsMode Enumerator]]
## Parameters
| File                                                     | type   | mand  | description                                                                                                                                                               |
| -------------------------------------------------------- | ------ | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/NetworkName\|NetworkName]] | string | false | Optional name of the network, in case the server hosts more than one. For default see [[Default parameters in the API|Default parameters in the API]]. For example `E`, `E_DQ`, `E_NRT` or `E_Plan_St`. |

