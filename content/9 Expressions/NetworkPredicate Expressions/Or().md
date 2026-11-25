---
title: Or()
description: Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if one of the combined predicates is true.
Type: NetworkPredicate
Order: 999
Unique: false
permalink:
aliases:
draft: false
date: 2024-10-02
tags:
  - Or
  - Expression
  - NetworkPredicateExpression
---
# Or()

Type of: _NetworkPredicate_
Unique: __

Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if one of the combined predicates is true.


## Parameters
| File                                                                   | type             | mand  | description                                                                                |
| ---------------------------------------------------------------------- | ---------------- | ----- | ------------------------------------------------------------------------------------------ |
| [[../Parameters/OtherPredicate\|OtherPredicate]] | NetworkPredicate | false | Another [[NetworkPredicate|NetworkPredicate]] that is to be combined with the one that receives the method. |


## Results
| File                                                                    | type             | unique | description                                             |
| ----------------------------------------------------------------------- | ---------------- | ------ | ------------------------------------------------------- |
| [[../Results/NetworkPredicate\|NetworkPredicate]] | NetworkPredicate | false  | A predicate that can be used to filter [[Connections|Connections]]. |


