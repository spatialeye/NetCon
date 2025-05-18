---
title: Shortest path or Dijkstra algorithm
description: 
permalink: 
aliases: 
draft: false
date: 2025-02-22
tags: 
---
[[../Network Ontology|previous]] [[./NetCon Path|next]]
# Shortest path or Dijkstra algorithm

Excellent explanations can be easily found on the internet, e.g. [on wikipedia](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm).

Here we will show the shortest paths for an example network that is slight adopted from the one used in [[./Basic network tracing|Basic network tracing]] in order to illustrate the behaviour.

```mermaid
---
title: Shortest path, not started
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } --> node1((n1))
    node1 <-- cost=1 --> node2((n2))
    node2 <-- cost=2 --> node3((n3))
    node3 <-- cost=3 --> node4((n4))
    node2 <-- cost=4 --> node5((n5))
    node5 <-- cost=5 --> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

We start at the [[../Sources|Source]], which is connected to n1. The cost will be $0.
```mermaid
---
title: Shortest path, step 1
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1(((n1<br/>$0)))
    node1 <-- cost=1 --> node2((n2))
    node2 <-- cost=2 --> node3((n3))
    node3 <-- cost=3 --> node4((n4))
    node2 <-- cost=4 --> node5((n5))
    node5 <-- cost=5 --> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

In the second step, we look at all the candidates. There is only one: we can travel to n2 with a cost of 1. Hence, the cost of going to n2 is $1.
```mermaid
---
title: Shortest path, step 2
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2(((n2<br/>$1)))
    node2 <-- cost=2 --> node3((n3))
    node3 <-- cost=3 --> node4((n4))
    node2 <-- cost=4 --> node5((n5))
    node5 <-- cost=5 --> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

In the thirth step, we have two candidate. It takes $3 to go to n3, and it takes $5 to go to n5. The shortest path algorithm dictates that we always take the minimum. That is the only guarantee to arrive at minimal costs at the target (aka sink).
By the way, in NetCon the sink is not known at the start of the trace; instead, it is denoted by a predicate, which will satisfy a condition to stop at or yield a result.
```mermaid
---
title: Shortest path, step 3
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3(((n3<br/>$3)))
    node3 <-- cost=3 --> node4((n4))
    node2 <-- cost=4 --> node5((n5))
    node5 <-- cost=5 --> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```
In the fourth step, we have two candidates again. The previous candidate still exists, and since we have added n3, all the nodes we can travel to from there are considered. The new candidate is to arrive at n4 for $6, so we take the other one instead.
```mermaid
---
title: Shortest path, step 4
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <-- cost=3 --> node4((n4))
    node2 <== "cost=4" ==> node5(((n5<br/>$5)))
    node5 <-- cost=5 --> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

At step five, we have two candidates to arrive at n4, and one to got to n7. We take the minimum again.
```mermaid
---
title: Shortest path, step 5
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <== "cost=3" ==> node4(((n4<br/>$6)))
    node2 <== "cost=4" ==> node5((n5<br/>$5)):::sectionStyle
    node5 <-. cost=5 .-> node4
    node4 <-- cost=1 --> node6((n6))
    node6 --> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```
The remaining steps are straightforward; there is not much too choose in this network, apart from the last step.
```mermaid
---
title: Shortest path, step 6
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <== "cost=3" ==> node4((n4<br/>$6)):::sectionStyle
    node2 <== "cost=4" ==> node5((n5<br/>$5)):::sectionStyle
    node5 <-. cost=5 .-> node4
    node4 <== "cost=1" ==> node6(((n6<br/>$7)))
    node6 ==> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- cost=6 --> node7((n7))
    node7 <-- cost=0 --> node8((n8))
    node6 <-- cost=3 --> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

```mermaid
---
title: Shortest path, step 7
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <== "cost=3" ==> node4((n4<br/>$6)):::sectionStyle
    node2 <== "cost=4" ==> node5((n5<br/>$5)):::sectionStyle
    node5 <-. cost=5 .-> node4
    node4 <== "cost=1" ==> node6((n6<br/>$7)):::sectionStyle
    node6 ==> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-- "cost=6" --> node7((n7))
    node7 <-- cost=0 --> node8(((n8<br/>$10)))
    node6 <== "cost=3" ==> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

```mermaid
---
title: Shortest path, step 8
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <== "cost=3" ==> node4((n4<br/>$6)):::sectionStyle
    node2 <== "cost=4" ==> node5((n5<br/>$5)):::sectionStyle
    node5 <-. cost=5 .-> node4
    node4 <== "cost=1" ==> node6((n6<br/>$7)):::sectionStyle
    node6 ==> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-. "cost=6" .-> node7(((n7<br/>$10)))
    node7 <== "cost=0" ==> node8(((n8<br/>$10)))
    node6 <== "cost=3" ==> node8
    node8 --> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

```mermaid
---
title: Shortest path, finished
---
graph LR
  subgraph example network 1
    direction LR
    con11@{ shape: text, label: transformer 1<br/>Role=Source } ==> node1((n1<br/>$0)):::sectionStyle
    node1 <== "cost=1" ==> node2((n2<br/>$1)):::sectionStyle
    node2 <== "cost=2" ==> node3((n3<br/>$3)):::sectionStyle
    node3 <== "cost=3" ==> node4((n4<br/>$6)):::sectionStyle
    node2 <== "cost=4" ==> node5((n5<br/>$5)):::sectionStyle
    node5 <-. cost=5 .-> node4
    node4 <== "cost=1" ==> node6((n6<br/>$7)):::sectionStyle
    node6 ==> con66@{ shape: text, label: servicepoint 1<br/>Role=Consumer }
    node5 <-. "cost=6" .-> node7(((n7<br/>$10)))
    node7 <== "cost=0" ==> node8((n8<br/>$10)):::sectionStyle
    node6 <== "cost=3" ==> node8
    node8 ==> con88@{ shape: text, label: servicepoint 2<br/>Role=Prosumer }
  end
  classDef outerStyle fill:#eee, stroke:#eee
  classDef sectionStyle fill: #eec, stroke #eec
  classDef barrierStyle fill:#bbf, stroke #000
```

