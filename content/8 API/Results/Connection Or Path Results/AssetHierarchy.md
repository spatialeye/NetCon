---
title: AssetHierarchy
description: List of name=value pairs that provide more information. Name may point to another assettablename+key, e.g. `station.id=79,installation.id=783`. The order of the pairs does not matter. The asset hierarchy can be used to identify or complete parts of the network in a single step and to link to structural information that is not part of the connectivity, but relevant for the network operation. If enrichment information has been configured, a whole range of additional [[asset hierarchy enrichment|asset hierarchy attributes]] can be retrieved. See also
Type: string
Order: 999
Unique: false
permalink: 
aliases: 
draft: false
date: 2025-04-03
tags:
  - ApiResult
  - AssetHierarchy
---
# AssetHierarchy

Type of: _string_
Unique: __

List of name=value pairs that provide more information. Name may point to another assettablename+key, e.g. `station.id=79,installation.id=783`. The order of the pairs does not matter. The asset hierarchy can be used to identify or complete parts of the network in a single step and to link to structural information that is not part of the connectivity, but relevant for the network operation. If enrichment information has been configured, a whole range of additional [[asset hierarchy enrichment|asset hierarchy attributes]] can be retrieved. See also

## Enrichment

Information in the AssetHierarchy can be enriched by providing so called enrichment tables, see [[../../../5 Configuration/Enrichment/Asset Hierarchy Enrichment|Asset Hierarchy Enrichment]].
## Examples

| AssetTableName | AssetId | Connection | AssetHierarchy     | Meaning                                                 | Further enrichment possible?                        |
| -------------- | ------- | ---------- | ------------------ | ------------------------------------------------------- | --------------------------------------------------- |
| busbar         | 3       | yes        | installation.id=10 | This busbar is part of the installation with the id 10. | Yes, e.g. build year.                               |
| installation   | 10      | no         | station.id=7       | This installation is part of station with the id 7.     | Yes, e.g. an installation number and serial number. |
| station        | 7       | no         |                    |                                                         | Yes, e.g. a station name and address.               |

When the asset hierarchy string input is parsed, the type of the value is [[../../../5 Configuration/Properties/Property Type Determination|determined according to rules]].
