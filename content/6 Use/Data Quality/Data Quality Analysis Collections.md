---
title: Data Quality Analysis Collections
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags:
  - ToDo
---
# Data Quality Analysis Collections

NetCon provides four analysis collections to asset the data quality of the network.

## IslandsCount

Count the number of separate network in the data.
Each separate network consists of one or more connections that are not connected to another separate network.

#ToDo Add table structure here.
## MissingNodes

The Missing Nodes collection reports nodes that do not have an Asset attached to it, assuming that the network has the shape `Point-Asset`  `Line-Asset` `Point-Asset`.
Note that a Point-Asset is expressed by [[../../8 API/Results/Connection Or Path Results/EdgeType|EdgeType]] Self-Loop and a Line-Asset by EdgeType Line.

#ToDo Add table structure here.
## SupernumeraryNodes

Supernumerary expresses a redundant or even undesired data.

Note that a Point-Asset is expressed by [[../../8 API/Results/Connection Or Path Results/EdgeType|EdgeType]] Self-Loop.
This collection reports where two or more `Point-Assets` are sharing the same Node, so there are two Self-Loop connections 'on top of each other'.

#ToDo Add table structure here.
## SupernumeraryLinks

Supernumerary expresses a redundant or even undesired data.

Note that a Line-Asset is expressed by  [[../../8 API/Results/Connection Or Path Results/EdgeType|EdgeType]] Line.
This collection reports where two or more `Line-Assets` are sharing the same Nodes, as expressed by their [[../../8 API/Results/Connection Or Path Results/FromId|FromId]] and [[../../8 API/Results/Connection Or Path Results/ToId|ToId]], so there are two connections 'on top of each other'.

Of course, from and two can be swapped.
If two connections are swapped and they are unidirectional (not the default [[../../8 API/Results/Connection Or Path Results/BiDirectional|BiDirectional]]), then they are not supernumerary.

#ToDo Add table structure here.