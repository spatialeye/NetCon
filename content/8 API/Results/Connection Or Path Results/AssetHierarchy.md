---
title: AssetHierarchy
description: List of name=value pairs that provide more information. Name may point to another assettablename+key, e.g. `station.id=79,installation.id=783`. The order of the pairs does not matter. The asset hierarchy can be used to identify or complete parts of the network in a single step and to link to structural information that is not part of the connectivity, but relevant for the network operation. If enrichment information has been configured, a whole range of additional asset hierarchy attributes can be retrieved.
Type: string
Order: 999
Unique: false
permalink:
aliases:
draft: false
date: 2025-06-05
tags:
  - ApiResult
  - AssetHierarchy
---
# AssetHierarchy

Type of: _string_

List of name=value pairs that provide more information. Name may point to another assettablename+key, e.g. `station.id=79,installation.id=783`. The order of the pairs does not matter. The asset hierarchy can be used to identify or complete parts of the network in a single step and to link to structural information that is not part of the connectivity, but relevant for the network operation. If enrichment information has been configured, a whole range of additional asset hierarchy attributes can be retrieved.

## Enrichment

Information in the [[AssetHierarchy|AssetHierarchy]] can be enriched by providing so called enrichment tables, see [[../../../5 Configuration/Configuration - 5. Enrichment/Asset Hierarchy Enrichment|Asset Hierarchy Enrichment]].
## Examples

| AssetTableName | AssetId | Connection | AssetHierarchy     | Meaning                                                 | Further enrichment possible?                        |
| -------------- | ------- | ---------- | ------------------ | ------------------------------------------------------- | --------------------------------------------------- |
| busbar         | 3       | yes        | installation.id=10 | This busbar is part of the installation with the id 10. | Yes, e.g. build year.                               |
| installation   | 10      | no         | station.id=7       | This installation is part of station with the id 7.     | Yes, e.g. an installation number and serial number. |
| station        | 7       | no         |                    |                                                         | Yes, e.g. a station name and address.               |

When the asset hierarchy string input is parsed, the type of the value is [[../../../5 Configuration/Configuration - 6. Properties/Property Type Determination|determined according to rules]].

If several values are listed in a single string input, then additional rules apply:
For each reference, the first field is used as key, and the other fields supply additional values.
For one particular AssetHierarchy reference, the last value is kept and stored at the reference that belongs with the key.

For example: 

| Occurence | InputString                                                                                                          | Meaning                                                                                                                                                         |
| --------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1         | station.id=7, name=A                                                                                                 | The asset is in Station 7. Station with Id 7 and name "A" is created.                                                                                           |
| 2         | station.id=7, name=B                                                                                                 | The asset is in Station 7. Station with Id 7 is referred to. Name remains "A".                                                                                  |
| 3         | station.id=7, installation.id=10, installation.type="double-rail", installation.id=11, installation.type="mono-rail" | The asset is in Station 7, and it is also part of installations 10 and 11. Installation 10 is of type "double-rail" and installation 11 is of type "mono-rail". |

Note that to avoid redundant information on connections, it is wise to put just the keys only in the Asset Hierarchy, and load all other data with [[../../../5 Configuration/Configuration - 5. Enrichment/Asset Hierarchy Enrichment|Asset Hierarchy Enrichment]].