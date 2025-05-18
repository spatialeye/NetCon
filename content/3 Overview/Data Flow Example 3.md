---
title: Data Flow Example 3
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Overview
  - Example
  - FlowCalculator
  - Terminal
---
[[./Data Flow Example 2|previous]] [[./Data Flow Example 4|next]]
# Data flow example III: From GIS T-piece to simple flow calculation

In the example below, we have a single continuous asset in the GIS, pipe 1, which is punctured so it can branch off into a different direction, which is pipe 2.

In the atomic layer, the T-piece will split the network. Also, the way that the GIS stores the data, pipe 1 could potentially be stored in more parts introducing unnecessary nodes (sometimes called dummy nodes). It is decided for standardization reasons, which is actually the case by the electric CIM, that terminals are generated for the T-piece.

At the section model, we experience that all of this network is literally glued together and that there is nothing to be isolated, or switched, so this part of the network is all clustered into the same section.

Finally, when exporting to a particular calculator, just the pipes are required. In this case, the calculator is able to derive itself that a T-piece is in place between pipe 1a, pipe 1b and pipe 2.

```mermaid
---
title: One cable or pipe branching of another written to flow calculator
---
flowchart TD
  gis:::outerStyle --> model:::outerStyle --> sections:::outerStyle --> flow:::outerStyle
  subgraph gis [GIS: Point & curve assets]
    subgraph gispic [gas or water network]
      direction LR 
      gisnode2((n1)) --- gispipe1a[pipe 1] --- gisnode3((n3)) --- gispipe1b[pipe 1] --- gisnode4((n2))
      gisnode3((n3)) --- gispipe2[pipe 2] --- gisnode5((n4))
    end
  end
  subgraph model [Atomic Model: connections]
    subgraph modelpic [Commodity network]
      direction LR 
      modnode2((n1)) --- modpipe1[pipe 1.1] --- modterm31([terminal 3.1]) --- modnode3((n3)) --- modterm32([terminal 3.2]) --- modpipe2[pipe 1.2] --- modnode4((n2))
      modnode3((n3)) --- modterm33([terminal 3.3]) --- modpipe3[pipe 2] --- modnode5((n5))
    end
  end
  subgraph sections [Isolatable Sections]
    subgraph sectionpic1 [section cluster 1]
      direction LR 
      secnode2((n1)) --- secpipe1[pipe 1.1]
      secpipe1 --- secterm1([terminal 3.1]) --- secnode3((n3)) --- secterm32([terminal 3.2])
      secterm32 --- secpipe2[pipe 1.2] --- secnode4((n2))
      secnode3 --- secterm33([terminal 3.3]) --- secpipe3[pipe 2] --- secnode5((n5))
    end
    sectionpic1:::sectionStyle
  end
  subgraph flow [Load flow calculation]
    subgraph flowpic [format depends on calculator]
      direction LR 
      flownode1((n1)) --- flowpipe1[pipe 3] --- flownode3((n3)) --- flowpipe4[pipe 4] --- flownode2((n2))
      flownode3 --- flowpipe2[pipe 2] --- flownode5((n5))
    end
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf
```

---
Example 3: One pipe branching of another.
![[../Zimages/example3_tpiece.png|example3_tpiece.png]]