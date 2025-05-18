---
title: Data Flow Example 2
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Overview
  - Example
---
[[./Data Flow Example 1|prevous]] [[./Data Flow Example 3|next]]
# Data Flow Example 2: From ambiguous GIS valves information to flow calculation

The picture below illustrates a variation from the previous example. In this case, in the GIS, two network switching assets are on top of each other, and they are sharing the same location and node. This is not uncommon. It is a data mistake that often occurs, but also, it is an allowed situation for water networks, where a small valve can be used the get the pressure of a large volume stream so a large valve next to it can be operated. In this example, the GIS would just put both valves on top of each other and not model the actual T-joints and extra pipes that are in place to make this work. Let's just say, if it was not required for the registration, often it will not be there.

At the atomic model layer, you see here that the valves are being separated. This is an attribute that can be set in the base extraction configuration. In this case, each of the valves is required to have its own network nodes, and as a consequence, the generated terminals will go to different nodes in the graph.

At the isolatable section layer, between the two sections of pipes that can be isolated individually, now there is an additional section for the second valve - compared to the previous example. Each of the valves(-sections) can be used to create a connection.

Finally, when this exported to a load flow calculator, the pipes become simplified pipes again. At their ends, two T-joints are used to connect to the two valve(-lines). The exporter can just ask every node how many (in- or outgoing) lines are connected to it, and based on that, it can decide to generate a T-joint on the spot; after all, such an object may be needed to split traffic in three ways.  

```mermaid
---
title: Two valves on the same location ambiguously connecting two pipes
---
flowchart TD
  gis:::outerStyle --> model:::outerStyle --> sections:::outerStyle --> flow:::outerStyle
  subgraph gis [GIS: Point & curve assets]
    subgraph gispic [gas or water network]
      direction LR 
      gisnode2((n1)) --- gispipe1[pipe 1] --- gisnode3((valve a)) --- gispipe2[pipe 2] --- gisnode4((n2))
      gispipe1 --- gisnode5((valve b)) --- gispipe2
      gisnode3:::barrierStyle
      gisnode5:::barrier2Style
    end
  end
  subgraph model [Atomic Model: connections]
    subgraph modelpic [Commodity network]
      direction LR 
      modnode2((n1)) --- modpipe1[pipe 1] --- modterm1([terminal a-1]) --- modnode3((valve a)) --- modterm2([terminal a-2]) --- modpipe2[pipe 2] --- modnode4((n2))
      modpipe1[pipe 1] --- modterm3([terminal b-1]) --- modnode5((valve b)) --- modterm4([terminal b-2]) --- modpipe2[pipe 2]
      modterm1:::barrierStyle
      modnode3:::barrierStyle
      modterm2:::barrierStyle
      modterm3:::barrier2Style
      modnode5:::barrier2Style
      modterm4:::barrier2Style
    end
  end
  subgraph sections [Isolatable Sections]
    direction LR 
    subgraph sectionpic1 [section cluster 1]
      secnode2((n1)) --- secpipe1[pipe 1]
    end
    subgraph sectionpic2a [section barrier a]
      secpipe1[pipe 1] --- secterm1([terminal a-1]) --- secnodea((valve a)) --- secterm_a2([terminal a-2])
    end
    subgraph sectionpic2b [section barrier a]
      secpipe1[pipe 1] --- secterm3([terminal b-1]) --- secnodeb((valve b)) --- secterm_b2([terminal b-2])
    end
    subgraph sectionpic3 [section cluster 2]
      secterm_a2([terminal a-2]) --- secpipe2[pipe 2] --- secnode4((n2))
      secterm_b2([terminal b-2]) --- secpipe2[pipe 2]
    end
    sectionpic1:::sectionStyle
    sectionpic2a:::barrierStyle
    sectionpic2b:::barrier2Style
    sectionpic3:::sectionStyle
  end
  subgraph flow [Load flow calculation]
    subgraph flowpic [format depends on calculator]
      direction LR 
      flownode1((n1)) --- flowpipe1[pipe 1] --- flownode3((n3)) --- flowvalvea[valve a] --- flownode4((n4)) --- flowpipe2[pipe 2] --- flownode2((n2))
      flownode3((n3)) --- flowvalveb[valve b] --- flownode4((n4))
      flowvalvea:::barrierStyle
      flowvalveb:::barrier2Style
    end
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf
  classDef barrier2Style fill:#bfb
```

---
Example 2: Two valves on the same location connecting two pipes.
![[../Zimages/example2_twovalvesontop.png|example2_twovalvesontop.png]]
