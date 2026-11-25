---
title: Network Topology Types
description:
permalink:
aliases:
draft: false
date: 2026-02-10
---
[[./Graph Theory - History and Context|previous]] [[../2 Version And Release Information/2.2 Version Information|next]]
# Network Topology Types

This page summarizes common network topology types and how they show up in real-world utility and infrastructure networks.

## Common topology types

- **Bus:** all nodes share a common backbone. [Bus network](https://en.wikipedia.org/wiki/Bus_network)
- **Ring:** each node connects to two neighbors, forming a loop. [Ring network](https://en.wikipedia.org/wiki/Ring_network)
- **Radial (Star):** nodes connect to a central hub or a main feeder with branches. [Star network](https://en.wikipedia.org/wiki/Star_network)
- **Extended star (Tree):** star-like branches with multiple levels. [Tree network](https://en.wikipedia.org/wiki/Tree_(graph_theory))
- **Hierarchical:** multiple tiers with aggregation at higher levels. Often implemented as a tree with local rings or meshes.
- **Mesh:** many nodes have multiple paths between them. [Mesh network](https://en.wikipedia.org/wiki/Mesh_networking)

In practice, networks are hybrids. You can mix a hierarchical backbone with meshed areas and radial feeders depending on reliability, cost, and operational needs.

## Examples by domain

- **Electricity:** typically hierarchical with radial feeders (star-like) at distribution level, and meshed or ringed structures at higher voltage levels for redundancy.
- **Water:** dense urban areas historically used meshed networks for resilience. Rural areas are often radial. Many utilities are rebuilding toward more radial zones to improve self-cleansing and control.
- **Gas:** commonly ring-shaped in urban areas for resilience, with radial branches in low-density areas.
- **Telecom:** access networks are usually hierarchical and tree-shaped (for example PON). Backbone and metro networks are often ring or mesh. Traffic engineering often models links as directed for capacity and routing.
- **District heat:** typically radial with supply and return lines and limited meshing. Control valves and operating regimes can make flow effectively directed.
- **Roads:** graphs with strong locality and many cycles in cities. Direction is mixed; one-way streets are directed edges.
- **Railways:** often radial from hubs with ring or bypass lines in metros. Track direction and signaling can make segments effectively directed, even if the physical track is bidirectional.

## Direction and control

Water and gas networks are usually bidirectional in physical connectivity, but **control valves** can enforce direction. The same idea applies to heat networks (supply and return) and to electricity when switches or protection settings constrain flow. In telecom, physical links can be bidirectional, but routing and capacity planning are typically modeled as directed.

## Abstract examples
### Bus

```mermaid
flowchart LR
  B[Backbone / Bus]:::backbone
  N1((N1)) --- B
  N2((N2)) --- B
  N3((N3)) --- B
  N4((N4)) --- B
  N5((N5)) --- B

  classDef backbone fill:#f7f7f7,stroke:#333,stroke-width:2px;
```

### Ring

```mermaid
flowchart LR
  N1((N1)) --- N2((N2)) --- N3((N3)) --- N4((N4)) --- N5((N5)) --- N1
```

### Radial (Star)

```mermaid
flowchart TB
  H((Hub)):::hub
  N1((N1)) --- H
  N2((N2)) --- H
  N3((N3)) --- H
  N4((N4)) --- H
  N5((N5)) --- H

  classDef hub fill:#fff3cd,stroke:#333,stroke-width:2px;
```



### Extended star (Tree)

```mermaid
flowchart TB
  R((Root / Hub)):::hub
  R --- L1((L1))
  R --- L2((L2))
  R --- L3((L3))

  L1 --- L1a((L1a))
  L1 --- L1b((L1b))

  L2 --- L2a((L2a))
  L2 --- L2b((L2b))
  L2 --- L2c((L2c))

  L3 --- L3a((L3a))

  classDef hub fill:#fff3cd,stroke:#333,stroke-width:2px;
```

### Tree variant: “main feeder with branches”

```mermaid
flowchart LR
  S((Source)):::src --- F1[Feeder] 
  S((Source)):::src --- F2[Feeder] 
  S((Source)):::src --- F3[Feeder]

  F1 --- A1((A1))
  F1 --- A2((A2))
  F2 --- B1((B1))
  F2 --- B2((B2))
  F3 --- C1((C1))
  F3 --- C2((C2))

  classDef src fill:#e7f5ff,stroke:#333,stroke-width:2px;
```


### Hierarchical (multi-tier; tree with local rings/meshes)

```mermaid
flowchart TB
  C((Core)):::core
  D1((Dist 1)):::dist
  D2((Dist 2)):::dist
  A1((Access 1)):::acc
  A2((Access 2)):::acc
  A3((Access 3)):::acc
  A4((Access 4)):::acc

  C --- D1
  C --- D2

  D1 --- A1
  D1 --- A2
  D2 --- A3
  D2 --- A4

  %% Local rings at access tier (example)
  subgraph Local Ring Access 1
    direction LR
    A1 --- A1a((A1a)) --- A1b((A1b)) --- A1c((A1c)) --- A1
  end

  subgraph Local Mesh Access 3
    direction LR
    A3 --- A3a((A3a))
    A3 --- A3b((A3b))
    A3a --- A3b
    A3a --- A3c((A3c))
    A3b --- A3c
  end

  classDef core fill:#e7f5ff,stroke:#333,stroke-width:2px;
  classDef dist fill:#eaf7ea,stroke:#333,stroke-width:2px;
  classDef acc fill:#f7f7f7,stroke:#333,stroke-width:2px;
```

### Mesh

#### Full-ish mesh (small N)

```mermaid
flowchart LR
  N1((N1)) --- N2((N2))
  N1 --- N3((N3))
  N1 --- N4((N4))
  N2 --- N3
  N2 --- N4
  N3 --- N4
```

#### Partial mesh (more realistic)

```mermaid
flowchart LR
  N1((N1)) --- N2((N2))
  N2 --- N3((N3))
  N3 --- N4((N4))
  N4 --- N5((N5))
  N1 --- N3
  N2 --- N4
  N3 --- N5
  N1 --- N4
```

## Concrete examples

Some simplified descriptions of components used below:

* **Primary Substation** 
  Interface between the transmission (HV) network and the medium-voltage (MV) distribution network, providing voltage transformation, protection, and primary switching.

* **Busbar**
  Common electrical node within a substation that interconnects multiple feeders, breakers, and transformers at the same voltage level.

* **Main Feeder Trunk**
  The principal MV line segment that carries power outward from the substation before branching into laterals or secondary feeders.

* **MV Switching Node**
  A controllable MV connection point used to route, isolate, or reconfigure feeders, typically hosting switching and protection devices.

* **MV Aggregation**
  An intermediate MV level where multiple feeders or branches are collected, redistributed, or supplied from one or more upstream sources.

* **RMU (Ring Main Unit)**
  A compact, enclosed MV switchgear unit enabling safe switching, sectionalizing, and protection in ring or radial distribution networks.

* **Sectionalizer**
  A normally closed switching device used to isolate faulted sections of a feeder while keeping healthy sections energized.

* **CB (Circuit Breaker)**
  A protection device capable of interrupting fault currents and automatically disconnecting equipment under abnormal conditions.

* **TX (Distribution Transformer)**
  A transformer that steps voltage down from MV to LV to supply end users.

* **Line Segment**
  A physical section of conductor or cable connecting two network nodes, representing a continuous electrical path.

* **LV (Low Voltage)**
  The final distribution level supplying electricity directly to customers, typically downstream of distribution transformers.
### Power distribution examples

```mermaid
flowchart LR
  %% =========================
  %%  HV / Substation
  %% =========================
  HV((HV Grid)):::hv --> SS[Primary Substation HV/MV Transformer]:::ss

  %% =========================
  %%  MV Bus & Two Feeders
  %% =========================
  SS --> BUS[MV Busbar]:::bus

  BUS --> F1H[Feeder F1 Head CB/Relay]:::prot
  BUS --> F2H[Feeder F2 Head CB/Relay]:::prot

  %% =========================
  %%  Feeder F1 main trunk
  %% =========================
  F1H --> F1A[Line Segment F1-A]:::line --> R1[RMU-1]:::rmu --> F1B[Line Segment F1-B]:::line --> S1[Sectionalizer-1]:::sw --> F1C[Line Segment F1-C]:::line --> R2[RMU-2]:::rmu --> F1D[Line Segment F1-D]:::line

  %% Laterals off F1
  R1 --> L1[Laterals L1]:::line --> T11[TX-11 MV/LV]:::tx --> LV11[LV Feeder LV-11]:::lv --> H11((Loads: Homes/SME)):::load
  R1 --> L2[Laterals L2]:::line --> T12[TX-12 MV/LV]:::tx --> LV12[LV Feeder LV-12]:::lv --> H12((Loads: Homes)):::load

  R2 --> L3[Laterals L3]:::line --> T21[TX-21 MV/LV]:::tx --> LV21[LV Feeder LV-21]:::lv --> H21((Loads: Industrial)):::load
  S1 --> L4[Laterals L4]:::line --> T31[TX-31 MV/LV]:::tx --> LV31[LV Feeder LV-31]:::lv --> H31((Loads: Agriculture)):::load

  %% =========================
  %%  Feeder F2 main trunk
  %% =========================
  F2H --> F2A[Line Segment F2-A]:::line --> R3[RMU-3]:::rmu --> F2B[Line Segment F2-B]:::line --> S2[Sectionalizer-2]:::sw --> F2C[Line Segment F2-C]:::line --> R4[RMU-4]:::rmu --> F2D[Line Segment F2-D]:::line

  %% Laterals off F2
  R3 --> L5[Laterals L5]:::line --> T41[TX-41 MV/LV]:::tx --> LV41[LV Feeder LV-41]:::lv --> H41((Loads: Homes)):::load
  R4 --> L6[Laterals L6]:::line --> T51[TX-51 MV/LV]:::tx --> LV51[LV Feeder LV-51]:::lv --> H51((Loads: Mixed)):::load
  S2 --> L7[Laterals L7]:::line --> T61[TX-61 MV/LV]:::tx --> LV61[LV Feeder LV-61]:::lv --> H61((Loads: Commercial)):::load

  %% =========================
  %%  Normally-open tie between feeders (reconfiguration)
  %% =========================
  R2 -. Normally Open Tie .- R4:::tie

  %% =========================
  %%  Optional: local loop at MV (ring-like segment)
  %% =========================
  R1 ---|Alternate Path| R2

  %% =========================
  %%  Styles
  %% =========================
  classDef hv fill:#e7f5ff,stroke:#0b4f6c,stroke-width:2px;
  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef bus fill:#f3f4f6,stroke:#111827,stroke-width:2px;
  classDef prot fill:#fde68a,stroke:#92400e,stroke-width:2px;
  classDef line fill:#ffffff,stroke:#374151,stroke-width:1.5px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef sw fill:#fee2e2,stroke:#991b1b,stroke-width:2px;
  classDef tie fill:#fef3c7,stroke:#b45309,stroke-width:2px,stroke-dasharray: 5 5;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```


### Two outgoing points feeding a closed ring
```mermaid
flowchart LR
  HV((HV Grid)):::hv --> SS[Primary Substation HV/MV Transformer]:::ss --> B[MV Busbar]:::bus

  %% Two outgoing points feeding a closed ring
  B --> P1[Ring Point A CB/Relay]:::prot --> R1[RMU-1]:::rmu --> R2[RMU-2]:::rmu --> R3[RMU-3]:::rmu --> R4[RMU-4]:::rmu --> P2[Ring Point B CB/Relay]:::prot --> B

  %% Loads off RMUs
  R1 --> T1[TX-1 MV/LV]:::tx --> LV1[LV-1]:::lv --> L1((Loads A)):::load
  R2 --> T2[TX-2 MV/LV]:::tx --> LV2[LV-2]:::lv --> L2((Loads B)):::load
  R3 --> T3[TX-3 MV/LV]:::tx --> LV3[LV-3]:::lv --> L3((Loads C)):::load
  R4 --> T4[TX-4 MV/LV]:::tx --> LV4[LV-4]:::lv --> L4((Loads D)):::load

  classDef hv fill:#e7f5ff,stroke:#0b4f6c,stroke-width:2px;
  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef bus fill:#f3f4f6,stroke:#111827,stroke-width:2px;
  classDef prot fill:#fde68a,stroke:#92400e,stroke-width:2px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```

### Radial (Star) feeders

```mermaid
flowchart TB
  SS[Primary Substation HV/MV Transformer]:::ss
  HUB[MV Switching Node / Hub]:::hub
  SS --> HUB

  %% Radial feeders
  HUB --> F1[Feeder F1]:::line --> R1[RMU-1]:::rmu --> T1[TX-1]:::tx --> LV1[LV-1]:::lv --> L1((Loads A)):::load
  HUB --> F2[Feeder F2]:::line --> S2[Sectionalizer-2]:::sw --> T2[TX-2]:::tx --> LV2[LV-2]:::lv --> L2((Loads B)):::load
  HUB --> F3[Feeder F3]:::line --> R3[RMU-3]:::rmu --> T3[TX-3]:::tx --> LV3[LV-3]:::lv --> L3((Loads C)):::load
  HUB --> F4[Feeder F4]:::line --> R4[RMU-4]:::rmu --> T4[TX-4]:::tx --> LV4[LV-4]:::lv --> L4((Loads D)):::load

  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef hub fill:#fff3cd,stroke:#333,stroke-width:2px;
  classDef line fill:#ffffff,stroke:#374151,stroke-width:1.5px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef sw fill:#fee2e2,stroke:#991b1b,stroke-width:2px;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```

### Extended star (Tree)

```mermaid
flowchart TB
  SS[Primary Substation HV/MV Transformer]:::ss --> F0[Main Feeder Trunk]:::line

  %% Level 1 branching
  F0 --> B1[Branch B1]:::line --> R1[RMU-1]:::rmu
  F0 --> B2[Branch B2]:::line --> R2[RMU-2]:::rmu
  F0 --> B3[Branch B3]:::line --> R3[RMU-3]:::rmu

  %% Level 2 branching
  R1 --> B1a[Branch B1a]:::line --> T1[TX-1]:::tx --> LV1[LV-1]:::lv --> L1((Loads A)):::load
  R1 --> B1b[Branch B1b]:::line --> T2[TX-2]:::tx --> LV2[LV-2]:::lv --> L2((Loads B)):::load

  R2 --> S2[Sectionalizer-2]:::sw --> B2a[Branch B2a]:::line --> T3[TX-3]:::tx --> LV3[LV-3]:::lv --> L3((Loads C)):::load
  R2 --> B2b[Branch B2b]:::line --> T4[TX-4]:::tx --> LV4[LV-4]:::lv --> L4((Loads D)):::load

  R3 --> B3a[Branch B3a]:::line --> R4[RMU-4]:::rmu --> T5[TX-5]:::tx --> LV5[LV-5]:::lv --> L5((Loads E)):::load
  R4 --> B3b[Branch B3b]:::line --> T6[TX-6]:::tx --> LV6[LV-6]:::lv --> L6((Loads F)):::load

  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef line fill:#ffffff,stroke:#374151,stroke-width:1.5px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef sw fill:#fee2e2,stroke:#991b1b,stroke-width:2px;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```

### Hierarchical (tiers + local rings/meshes)

```mermaid
flowchart TB
  %% Tiers
  CORE((Core / Transmission)):::core --> SS1[Primary Substation A HV/MV]:::ss
  CORE --> SS2[Primary Substation B HV/MV]:::ss

  %% Distribution (MV) tier
  SS1 --> MV1[MV Aggregation A]:::dist
  SS2 --> MV2[MV Aggregation B]:::dist

  %% Access tier (feeders)
  MV1 --> F1[Feeder A1]:::line
  MV1 --> F2[Feeder A2]:::line
  MV2 --> F3[Feeder B1]:::line
  MV2 --> F4[Feeder B2]:::line

  %% Local ring under Feeder A1
  subgraph Local_Ring_A1["Local Ring (MV) - A1"]
    direction LR
    F1 --> R1[RMU-1]:::rmu --> R2[RMU-2]:::rmu --> R3[RMU-3]:::rmu --> R1
  end

  %% Local partial mesh under Feeder B1
  subgraph Local_Mesh_B1["Local Partial Mesh (MV) - B1"]
    direction LR
    F3 --> M1[Node M1]:::rmu
    F3 --> M2[Node M2]:::rmu
    M1 --- M2
    M1 --- M3[Node M3]:::rmu
    M2 --- M3
  end

  %% Loads attached
  R2 --> T1[TX-1]:::tx --> LV1[LV-1]:::lv --> L1((Loads A)):::load
  R3 --> T2[TX-2]:::tx --> LV2[LV-2]:::lv --> L2((Loads B)):::load
  M2 --> T3[TX-3]:::tx --> LV3[LV-3]:::lv --> L3((Loads C)):::load
  M3 --> T4[TX-4]:::tx --> LV4[LV-4]:::lv --> L4((Loads D)):::load

  classDef core fill:#e7f5ff,stroke:#0b4f6c,stroke-width:2px;
  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef dist fill:#eaf7ea,stroke:#166534,stroke-width:2px;
  classDef line fill:#ffffff,stroke:#374151,stroke-width:1.5px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```

### Mesh (MV partial mesh with multiple alternative paths)

```mermaid
flowchart LR
  SS[Primary Substation HV/MV Transformer]:::ss --> B[MV Busbar]:::bus

  %% Feed-in nodes
  B --> A1[Node A1]:::node
  B --> A2[Node A2]:::node

  %% Mesh nodes
  A1 --- N1[RMU N1]:::rmu
  A1 --- N2[RMU N2]:::rmu
  A2 --- N3[RMU N3]:::rmu
  A2 --- N4[RMU N4]:::rmu

  %% Interconnections (multiple paths)
  N1 --- N2
  N2 --- N3
  N3 --- N4
  N1 --- N3
  N2 --- N4

  %% Additional mesh expansion
  N3 --- N5[RMU N5]:::rmu
  N2 --- N6[RMU N6]:::rmu
  N5 --- N6
  N4 --- N5

  %% Loads on various nodes
  N1 --> T1[TX-1]:::tx --> LV1[LV-1]:::lv --> L1((Loads A)):::load
  N3 --> T2[TX-2]:::tx --> LV2[LV-2]:::lv --> L2((Loads B)):::load
  N4 --> T3[TX-3]:::tx --> LV3[LV-3]:::lv --> L3((Loads C)):::load
  N6 --> T4[TX-4]:::tx --> LV4[LV-4]:::lv --> L4((Loads D)):::load

  classDef ss fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px;
  classDef bus fill:#f3f4f6,stroke:#111827,stroke-width:2px;
  classDef node fill:#fde68a,stroke:#92400e,stroke-width:2px;
  classDef rmu fill:#ecfccb,stroke:#3f6212,stroke-width:2px;
  classDef tx fill:#ede9fe,stroke:#5b21b6,stroke-width:2px;
  classDef lv fill:#f0fdf4,stroke:#166534,stroke-width:2px;
  classDef load fill:#fff7ed,stroke:#9a3412,stroke-width:2px;
```
