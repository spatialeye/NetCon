---
title: Overview - 3. Solution Architecture
description:
permalink:
aliases:
draft: false
date: 2025-06-01
tags:
  - Overview
  - GettingStarted
---
[[./3.2 Data Flow Examples/Overview Examples - 1. Purpose and Examples|previous]] [[./Overview - 4. Sources of Connectivity|next]]
# Solution Architecture

The different functions of NetCon are:

* Extracting connectivity (also known as topology);
* Storing connectivity in a universal and open format;
* Enable inspecting and improving connectivity data quality dynamically;
* Enabling enrichment of connectivity with all relevant information;
* Providing an expression language and API calls to query connectivity;
* Simplifying networks by reducing or morphing query results;
* Enabling viewing and using what-if scenario's.

NetCon is built into / on top of the Spatial Eye products' Solution architecture:

* A desktop tool for creating configuration, Spatial Analysis and BI;
* A server tool for hosting (spatial) processes, APIs, and viewing applications, amongst which;
	* A self-maintaining and repairing Warehouse for providing time aware repositories.
	* A network design tool for maintaining future a timeline and scenarios of the network.

```mermaid
---
title: NetCon Solution Architecture with Spatial Eye products
---
graph TD
  subgraph Consumers
    direction LR
    app1([App 3])
    app2([App 1])
    app3([App 2])
    lite([Lite Viewer])
    oap([Outage Analysis Portal])
    np([NetPlan])
  end
  subgraph Servers
    direction LR
  app1 ---o custom
  app2 ---o server
  app3 ---o server
  lite ---o server
  oap ---o server
  np ---o server
    server@{ shape: rect, label: "XY- or GSA-Server" }
    seproj@{ shape: doc, label: "TraceApi / Viewer config"}
	seproj --> server
    custom@{ shape: rect, label: "Python Server" }
  end
  server --> netcondb
  server --> assetdb
  server --> futuredb
  server --> nrt
  server --> exports
  custom -.-> exports
  custom -.-> server
  subgraph Storage
    netcondb@{ shape: lin-cyl, label: "NetCon Warehouse" }
    assetdb@{ shape: lin-cyl, label: "Asset Warehouse" }
    futuredb@{ shape: lin-cyl, label: "Future Assets" }
    exports@{ shape: database, label: "Trace Exports" }
    nrt@{ shape: database, label: "Near Real Time" }
  end
  
```


Note that the usage of Warehouse as an batch mechanism providing extraction updates with high availability updates, will become optional in the future. For Small datasets, extraction can be done on the fly or by call exports tooling.