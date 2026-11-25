---
title: And()
description: Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if all combined predicates are true.
Type: NetworkPredicate
Order: 999
Unique: false
permalink:
aliases:
draft: false
date: 2024-10-02
tags:
  - And
  - Expression
  - NetworkPredicateExpression
---
# And()

Type of: _NetworkPredicate_
Unique: __

Combines two [[NetworkPredicate|NetworkPredicate]]s and only returns true if all combined predicates are true.


## Parameters
| File                                                                   | type             | mand  | description                                                                                |
| ---------------------------------------------------------------------- | ---------------- | ----- | ------------------------------------------------------------------------------------------ |
| [[../Parameters/OtherPredicate\|OtherPredicate]] | NetworkPredicate | false | Another [[NetworkPredicate|NetworkPredicate]] that is to be combined with the one that receives the method. |


## Results
| File                                                                    | type             | unique | description                                             |
| ----------------------------------------------------------------------- | ---------------- | ------ | ------------------------------------------------------- |
| [[../Results/NetworkPredicate\|NetworkPredicate]] | NetworkPredicate | false  | A predicate that can be used to filter [[Connections|Connections]]. |


