---
title: Data Flow Example 4
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Overview
  - Example
  - CIM
  - ADMS
  - Terminal
---
[[./Data Flow Example 3|previous]] [[./Sources of Connectivity|next]]
# Data flow example IV: From GIS T-piece to Common Information Model

The example below is almost the same as the [[./Data Flow Example 3|previous]]. The (gas or water) pipes are now replaced by cables. This time, the network is not exported to a calculator, but towards an ADMS system by means of the CIM format. The CIM format requires terminals between cables and joints, which are called terminals or connectors.

Sometimes, terminals 1a-T and terminals 1b-T are remove from the export. The Spatial Eye Network Reduction can perform network transformation, aggregation and reduction functions based on asset, edge_type, etc. in order to fulfill these requirements.

```mermaid
---
title: One cable branching of another written to CIM.
---
flowchart TD
  gis[GIS: as previous example]:::outerStyle --> model[Atomic Model: as previous example]:::outerStyle --> sections:::outerStyle --> flow:::outerStyle
  subgraph sections [Isolatable Sections: as previous example]
    subgraph sectionpic1 [section cluster 1]
      direction LR 
      secnode2((n1)) --- secpipe1[cable 1.1]
      secpipe1 --- secterm1([terminal 3.1]) --- secnode3((n3)) --- secterm32([terminal 3.2])
      secterm32 --- secpipe2[cable 1.2] --- secnode4((n2))
      secnode3 --- secterm33([terminal 3.3]) --- secpipe3[cable 2] --- secnode5((n5))
    end
    sectionpic1:::sectionStyle
  end
  subgraph flow [Load flow calculation]
    subgraph flowpic [format depends on calculator]
      direction LR 
      flownode2((n1)) --- flowpipe1[cable 1.1]
      flowpipe1 --- flowterm1([connector 3.1]) --- flownode3((n3)) --- flowterm32([connector 3.2])
      flowterm32 --- flowpipe2[cable 1.2] --- flownode4((n2))
      flownode3 --- flowterm33([connector 3.3]) --- flowpipe3[cable 2] --- flownode5((n5))
    end
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf
```

---
Example 4: One cable branching of another.
![[../Zimages/example4_tjoint_cim.png|example4_tjoint_cim.png]]
