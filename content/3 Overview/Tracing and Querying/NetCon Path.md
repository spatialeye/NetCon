---
title: NetCon Path
description:
permalink:
aliases:
draft: false
date: 2025-02-23
tags:
---
[[./Shortest path or Dijkstra algorithm|previous]] [[./Basic network tracing|next]]
# NetCon Path

Typically, during a trace, it is possible just to return [[../../8 API/Results/Search Or Trace Results/Connections (Result)|Connections (Result)]], and in case the [[./Shortest path or Dijkstra algorithm|previous]] is applied, also the cost at arriving at a connection or node.

In NetCon, [[../../8 API/Results/Search Or Trace Results/Paths (Result)|Paths (Result)]] are returned. In addition to a connection, this provides:
* [[../../8 API/Results/Connection Or Path Results/Depth|Depth]]
* [[../../8 API/Results/Connection Or Path Results/SumCost|SumCost]]
* [[../../8 API/Results/Connection Or Path Results/TraceMarker|TraceMarker]]

The paths that belong to graph below are:
```mermaid
---
title: Shortest path, finished
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: id=11<br/>Role=Source } --> node1((n1<br/>$0))
    node1 <-- id=12<br/>cost=1 --> node2((n2<br/>$1))
    node2 <-- id=23<br/>cost=2 --> node3((n3<br/>$3))
    node3 <-- id=34<br/>cost=3 --> node4((n4<br/>$6))
    node2 <-- id=25<br/>cost=4 --> node5((n5<br/>$5))
    node5 <-- id=45<br/>cost=5 --> node4
    node4 <-- id=46<br/>cost=1 --> node6((n6<br/>$7))
    node6 --> con66@{ shape: text, label: id=66<br/>Role=Consumer }
    node5 <-- id=57<br/>cost=6 --> node7((n7<br/>$11))
    node7 <-- id=78<br/>cost=2 --> node8((n8<br/>$13))
    node8 --> con88@{ shape: text, label: id=88<br/>Role=Prosumer }
    node8 <-- id=89<br/>cost=3 --> node9((n9<br/>$16))
    node9 --> con99@{ shape: text, label: id=99<br/>Role=Consumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

Simple path notation, *not* used in NetCon:

| FromId | In between | ToId | Depth | SumCost | TraceMarker |
| ------ | ---------- | ---- | ----- | ------- | ----------- |
| 1      | -          | 2    | 1     | 1       | Start       |
| 1      | -2-        | 3    | 2     | 3       | -           |
| 1      | -2-        | 5    | 2     | 5       | -           |
| 1      | -2-3-      | 4    | 3     | 6       | -           |
| 1      | -2-3-4-    | 6    | 4     | 7       | Stop        |
| 1      | -2-5-      | 7    | 3     | 11      | -           |
| 1      | -2-5-7-    | 8    | 4     | 13      | Stop        |
| 1      | -2-5-7-8-  | 9    | 5     | 16      | Stop        |
## NetCon Path notation

Instead of having an arbitrary length 'in between' attribute, in NetCon, the paths refer to a **previous** path in a trace to arrive at the outcome with the [[../../8 API/Results/Connection Or Path Results/PreviousId|PreviousId]].
Also, if 'some asset' is present at a node, they are inserted as [[../../8 API/Results/Connection Or Path Results/EdgeType|self-loops]], i.e. going from and to the same NodeId.
This way, we can insert them when encountered at the start, during or at the end of a trace.
For simplicity, in the example provided, let the connection between two nodes have the id that is made up from putting the two NodeIds together, e.g. the connection from n3 to n4 has an id=34.
The same table now looks like this:

| LastConnectionId | PreviousId | FromId  | ToId    | Depth   | SumCost  | TraceMarker |
| ---------------- | ---------- | ------- | ------- | ------- | -------- | ----------- |
| 11               | -          | 1       | 1       | 1       | 0        | Start       |
| 12               | 11         | 1       | 2       | 2       | 1        | -           |
| 23               | 12         | 1       | 3       | 3       | 3        | -           |
| 25               | 12         | 1       | 5       | 3       | 5        | -           |
| 34               | 23         | 1       | 4       | 4       | 6        | -           |
| 46               | 34         | 1       | 6       | 5       | 7        | -           |
| 66               | 46         | 1       | 6       | 6       | 7        | Stop        |
| ***45***         | ***25***   | ***1*** | ***4*** | ***4*** | ***10*** | -           |
| 57               | 25         | 1       | 7       | 4       | 11       | -           |
| 78               | 57         | 1       | 8       | 5       | 13       | -           |
| 88               | 78         | 1       | 8       | 6       | 13       | Stop        |
| 89               | ***88***   | 1       | 9       | 7       | 16       | -           |
| 89               | 99         | 1       | 9       | 8       | 16       | Stop        |
Several observations can be made:
* The connections at the start and end are inserted as [[../../8 API/Results/Connection Or Path Results/EdgeType|self-loops]];
	* This increases the depth compared to the simple path notation used before;
* The connection Id=45 is also modelled as a path, with a SumCost of 10, even though it may not be used in a shorted path;
	* It may still be of interested in NetCon output:
		* For a start, meshed networks behave different and need to be operated in a different way;
		* It is still transporting the commodity and as such is *live*;
* The connection at n8 is inserted as a self-loop into the path leading to n9 - here the PreviousId=88 and not PreviousId=78;
	* Basically, if self-loops are encountered on the way, they *have* to be used (unless those are [[./Basic network tracing#Block criteria|blocked]] of course);
	* This increases the depth, and may increase the cost.
