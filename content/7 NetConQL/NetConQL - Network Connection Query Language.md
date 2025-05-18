---
title: NetConQL - Network Connection Query Language
description: 
permalink: 
aliases: 
draft: false
date: 2025-03-20
tags:
  - ToDo
---
# NetConQL - NetworkConnection Query Language

In order to solve use cases, the network must be queried. 
These can be simple select queries, traces, or network reductions.
In NetCon, all queries are expressed in [[NetConQL|NetConQL]].

N.B. ConQL as a language is in progress and will be driven by customer requirements.

In ConQL, one can use both the network properties (e.g. the graph), as well as asset properties (unlimited).
Hence, it is a language for a property graph.
It is designed to communicative to the end user, and to have simple integration with e.g. Python #ToDo.
Possibly, it will be replace by Cypher or another GraphQL language in the long run.

One can compare the [[Network|Network]] name to a schema name in SQL. 
Specifying the Network in a query will specify which network will be used (e.g. gas or elec, or an Near Realtime Overlay network).

Since the network is expressed in connections, every query will start with the connections, or sections of connections.
If [[Indices|Indices]] have been generated, and for those fields for which indices are always present, ConQL will automatically use indices; those do not need to be 'hinted' at.

A query returns connections or paths, where paths can only be returned for trace-queries.
Queries results can be union-ed with other queries.
The connections of a query can be treated as a network in its own right, which can be morphed into different networks, e.g. to be suitable for flow calculation.
