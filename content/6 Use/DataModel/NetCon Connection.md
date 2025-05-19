---
title: NetCon Connection
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags:
  - Connection
---
# NetCon Connection

The NetCon Connection table represents a network graph. One table can exist per discipline, e.g. electricity, gas, water or telecom. If a network is connected, it should be in a single NetCon Connection table, e.g. gas high pressure and low pressure (connected by a regulating station), or industry and household water (connected by a filtering plant), telecom fibre, coax and ethernet (connected by signal converters) should each be in a single table for their discipline.

(Note that this is different from Smallworld manifold.)

The definition of the table contents is standard and may not be altered.

| Field          | Name             | Description                                                                                                                                                                                                                                              |
| -------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| se_history_id* | Meta History Id  | Optional hidden Spatial Warehouse Key, will be ignored. See also [User Data in Spatial Warehouse](https://documentation.spatial-eye.com/swh/2021_2/en/143117a0-d822-42f1-ae69-a484a2db0efa.htm)                                                          |
| id*            | Id               | Identifier of the connection, also known as [[../../8 API/Results/Connection Or Path Results/ConnectionId|ConnectionId]]. Often the Spatial Warehouse key is used, which external name is `Meta History Root Id`; the internal name is `se_history_rootid`.                                                          |
| fromid*        | [[../../8 API/Results/Connection Or Path Results/FromId|FromId]]       | Node Id where connection starts from.                                                                                                                                                                                                                    |
| toid*          | [[../../8 API/Results/Connection Or Path Results/ToId|ToId]]         | Node Id where connection goes to.                                                                                                                                                                                                                        |
| role           | [[../../8 API/Results/Connection Or Path Results/Role|Role]]         | Enumerator denoting rol of connection in network. See also [[../Enumerators/NetCon Role Enumerator|NetCon Role Enumerator]].                                                                                                                                                                       |
| bidrectional   | Bidirectional    | 0 if just going from fromid to toid, 1 if this connection also represents the reverse going from toid to fromid.                                                                                                                                         |
| barrier        | [[../../8 API/Results/Connection Or Path Results/Barrier|Barrier]]      | Enumerator. 0 if not a barrier; 1 if barring and the commodity is not transported; -1 if it can be barring but the commodity is let through, i.e. conducting. See also [[../Enumerators/NetCon Barrier Enumerator|NetCon Barrier Enumerator]]. Other values reserved for the future.                  |
| edgetype       | Edge Type        | Enumerator that say something about what type of connection this is. 0 = loop (geometryp is set), 1 = link (geometryl is set), 2 = terminal (no geometry). See also [[../Enumerators/NetCon EdgeType Enumerator|NetCon EdgeType Enumerator]].                                                          |
| cost           | Cost             | Double precision indicating cost, impedance or resistance.                                                                                                                                                                                               |
| label          | Label            | Optional string value that provides additional information about this connection.                                                                                                                                                                        |
| commodity      | Commodity        | The item being transported, e.g. HV, MV, LV for high voltage, and `abc` or '123' for the phases, or ‘u’ (1 unknown phase), combined, e.g. 'LV:abc'. Similarly, this could be HP or LP (high or low pressure) followed by the type of gas CH4 or H2, etc. |
| statuscode     | Status Code      | Enumerator indicating the status life cycle time dimension. See also [[../Enumerators/NetCon Status Enumerator|NetCon Status Enumerator]].                                                                                                                                                           |
| geometryl      | Geometry Line    | Multiple Line geometry (for links and hyperlinks).                                                                                                                                                                                                       |
| geometryp      | Geometry Point   | Multiple Point geometry (for points and long hyperlinks).                                                                                                                                                                                                |
| assettablename | Asset Table Name | Name of the table representing the assets in the registration system as it is ETL-ed into Spatial Warehouse. Hence, if the name is translated or corrected for typo's in the warehouse repository, the same name should be used here.                    |
| assetid        | Asset Id         | Positive long value denoting the Id of the original record this data came from in the source system. Note that for various reason this Id is by far not unique in the connection table.                                                                  |
| specification  | Specification    | Pointing to an entry in the specification table for asset table name.                                                                                                                                                                                    |
| assethierarchy | Asset Hiearchy   | Information about containers and related data to the connection. E.g. 'substation.id=123' or 'ean.id=456,ean.id=457' to denote a connection is in a particular substation or is connected to two smart meters with ean id.                               |
| customassetid  | Custom Asset Id  | String key relating to an enterprise wide reference present in the registration system.                                                                                                                                                                  |
| owner          | Owner            | String value denoting if this connection has a deviating owner, <null> otherwise.                                                                                                                                                                        |
| operatedby     | [[Operate|Operate]]      | String value denoting if this connection is not operated by default party, but by a deviating party, <null> otherwise.                                                                                                                                   |
| manifoldcode   | Manifold Code    | To be replaced by [[./Registration Connectivity Group Definition|Registration Connectivity Group Definition]]. Enumerator referring back to the source system, see [Manifold](NetCon%2520Connection.md##manifold-definition).                                                                                                  |
| rwocode        | RwoCode          | To be replaced by [[./Registration Asset Table Definition|Registration Asset Table Definition]]. Enumerator referring back to the source system, see [Real-world Object](NetCon%2520Connection.md##rwo-definition). To be replaced by the Id of the Asset Table Definition of the registration system.                  |
| geomappcode    | GeomAppCode      | To be replaced by [[./Registration Geometry Definition|Registration Geometry Definition]]. Enumerator referring back to the source system, see [Geom App Code](NetCon%2520Connection.md##geom-attribute-definition).                                                                                                 |

