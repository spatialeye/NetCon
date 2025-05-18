---
title: NetCon Expressions
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - ToDo
---
# NetCon Expressions

#ToDo Revise the text below.

The expression language in GeoSpatial Analysis or Spatial Workshop has been extended with many functions to interact with the NetCon tracing engine. These function will use the engine in exactly the same way as the [NetCon API](NetCon%2520Expressions.md##netcon_api).

The expressions can be ordered into four categories:

1. Retrieve a property of a connection;
2. Perform a trace function and yield a trace result;
3. Get information out of a trace result:
    - Properties;
    - Methods that perform an operation;  
    - Join expressions to retrieve detailed results.  
4. Manipulate the network: _work in progress_
    - Change barrier state information;
    - Disable connections;
    - Create new connections.

Some examples of the above:

1. `NetConFlow()` retrieves the flow for a connection, which can be used to display a downstream on the map;
2. `NetConTraceOutDownStream()` performs a downstream trace to find paths to specific network elements;
3. The `.Count` property returns the number of connections or paths in the trace result.
4. The `NetConSetBarrier()` manipulates the barrier state of a connection or asset.

About the parameters of the Spatial Workshop Expressions.

* Many parameters are optional and they have default values.
* Some parameter have `pattern` appended to their name. Those are support [[../8 API/Wildcards|Wildcards]] patterns.
 
#ToDo Write content here.


---
## Top level expressions
  
Bla bla

| File                                                                             | description                                                                                                                          |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| [[./Toplevel Expressions/NetworkMatch()\|NetworkMatch()]] | Creates a predicate to use on [[Connections|Connections]] to filter them.                                                                        |
| [[./Toplevel Expressions/Network()\|Network()]]           | An expression that provides a handle to the network, which contains [[Connections|Connections]] and knows about their [[Sections|Sections]] and [[Flow|Flow]]. |



---
## Network predicate expressions

| File                                                                   | description                                                                                         |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [[./NetworkPredicate Expressions/Or()\|Or()]]   | Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if one of the combined predicates is true. |
| [[./NetworkPredicate Expressions/Not()\|Not()]] | Creates a new [[NetworkPredicate|NetworkPredicate]] that returns true if the receiving predicate is false.           |
| [[./NetworkPredicate Expressions/And()\|And()]] | Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if all combined predicates are true.       |



