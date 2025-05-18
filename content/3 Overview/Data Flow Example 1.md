---
title: Data Flow Example 1
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Overview
  - Example
---
[[./Purpose and Examples|previous]] [[./Data Flow Example 2|Data Flow Example 2]]
# Data flow example I: From GIS valve to simple flow calculation


The picture below illustrates a situation where in the Geographic Information System (GIS, top layer) a valve is connecting two pipes.

In the next layer, the atomic model, which is part of NetCon, every element of the network is stored as a 'connection.' We see here that between the two pipes (now a connection of type 'line') and the valves (now a connection of type 'node') two new connections (of type 'terminal') have been injected. These terminals are required when all switching behavior is done with connections. Another reason to ask for terminals is get nodes with _keys_. Thus, NetCon is used as a keying system.

In the third layer, isolatable sections, also part of NetCon, parts of the network that are switched as one, i.e. parts that can be isolated individually, are clustered together in sections. So, all pipes to the left of the valve will comprise one section, and also all pipes to the right.

Finally, at the bottom layer, is what the output to the load flow calculation program will look like. From pipe 1 and 2, all unnecessary nodes will be removed. And in this case, valve _A_ will be represented as a line, no longer a node, since this particular calculator requires every network switching element to be line, not a node.

```mermaid
---
title: One valve connecting two pipes
---
flowchart TD
  gis:::outerStyle --> model:::outerStyle --> sections:::outerStyle --> flow:::outerStyle
  subgraph gis [GIS: Point & curve assets]
    subgraph gispic [gas or water network]
      direction LR 
      gisnode2((n1)) --- gispipe1[pipe 1] --- gisnode3((valve a)) --- gispipe2[pipe 2] --- gisnode4((n2))
      gisnode3:::barrierStyle
    end
  end
  subgraph model [Atomic Model: connections]
    subgraph modelpic [Commodity network]
      direction LR 
      modnode2((n1)) --- modpipe1[pipe 1] --- modterm1([terminal a-1]) --- modnode3((valve a)) --- modterm2([terminal a-2]) --- modpipe2[pipe 2] --- modnode4((n2))
      modterm1:::barrierStyle
      modnode3:::barrierStyle
      modterm2:::barrierStyle
    end
  end
  subgraph sections [Isolatable Sections]
    direction LR 
    subgraph sectionpic1 [section cluster 1]
      secnode2((n1)) --- secpipe1[pipe 1]
    end
    subgraph sectionpic2 [section barrier a]
      secpipe1[pipe 1] --- secterm1([terminal a-1]) --- secnodea((valve a)) --- secterm_a2([terminal a-2])
    end
    subgraph sectionpic3 [section cluster 2]
      secterm_a2([terminal a-2]) --- secpipe2[pipe 2] --- secnode4((n2))
    end
    sectionpic1:::sectionStyle
    sectionpic2:::barrierStyle
    sectionpic3:::sectionStyle
  end
  subgraph flow [Load flow calculation]
    subgraph flowpic [format depends on calculator]
      direction LR 
      flownode1((n1)) --- flowpipe1[pipe 1] --- flownode3((n3)) --- flowvalvea[valve a] --- flownode4((n4)) --- flowpipe2[pipe 2] --- flownode2((n2))
      flowvalvea:::barrierStyle
    end
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf
```

---
Example 1: One valve connecting two pipes.
![[../Zimages/example1_onevalve.png|example1_onevalve.png]]

