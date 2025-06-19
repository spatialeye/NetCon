---
title: Common parameters in the API
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags: 
---
# Common parameters in the API

## Parameters
| File                                                                           | type    | mand  | description                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------ | ------- | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[./Parameters/MaxResults\|MaxResults]]                         | integer | false | Maximum number of results you want to retrieve, 0 if you want to provide none.This can be used to avoid overflow in the receiving application if very large results are produced.                                                                                                            |
| [[./Parameters/IncludeGeoms\|IncludeGeoms]]                     | boolean | false | If false (default and faster), no geometries are returned. This is much faster.                                                                                                                                                                                                              |
| [[./Parameters/MergeGeoms\|MergeGeoms]]                         | boolean | false | If false (default) no additional geometries are retrieved. If true, one set of geometries is retrieved for all points in the result and one set for the lines (multi curve). This saves a lot of overhead in the result and can be convenient for highlighting in the receiving application. |
| [[./Parameters/GeomsAsArea\|GeomsAsArea]]                       | boolean | false | If false (default) no area geometry is returned. If true, one area geometry is returned (multi polygon) which is a buffer around all points and lines in a single geometry.                                                                                                                  |
| [[./Parameters/EnrichAssetInformation\|EnrichAssetInformation]] | boolean | false | This parameter became redundant. If enrichment data has been configured, it can be queried and will be returned.                                                                                                                                                                             |


For these common parameters you can set [[./Default parameters in the API|default values]].