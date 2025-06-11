---
title: Flow Transition Rules
description: 
permalink: 
aliases: 
draft: false
date: 2025-06-05
tags: 
---
# Flow Transition Rules

If no Flow Transition Rules are provided, it is assumed that every connection / asset may feed every other connection / asset. 
In that case, the only restriction is what the registration system allows to be entered.

## When to use flow transition rules

If you registration system is setup in such a way, that there are many redundancies or inappropriate connections going to/from the same now, then Flow Transition Rules can be your helping hand to straighten out the transitions. 

Imagine a system where substation internals, schematic diagrams and in-place map locations are all modelled in a single data model, and are all connected. 
If no preventions are taken, every cable that is both in a schematic representation as well as in a in-place location will create a cycle in the graph, hence making it 'meshed', while it is only a double registration of the same asset.

Another situation where this may occur is when cables have mostly overview locations, but in some situations they have have detailed locations. These may also call cycles.

## Defining flow transition rules

The NetConFlowTransitionRule collection has the following definition:

| FieldName     | FieldType                                                                                                                                                                                                   | Optional |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Disciplin     | Letter denoting [[../../3 Overview/Networks/Disciplin|Disciplin]], e.g.                                                                                                                                                                         | No       |
| Block         | Boolean, denoting this is a rule that will block a flow (forbidden transition) or will explicitly enable a flow (in which case connections matching the PredicateFrom have to find a matching PredicateTo). | No       |
| PredicateFrom | [[../../7 NetConQL/NetConQL - Network Connection Query Language|NetConQL - Network Connection Query Language]] predicate that is evaluatad on a connection where we transition from.                                                                                      | No       |
| PredicateTo   | [[../../7 NetConQL/NetConQL - Network Connection Query Language|NetConQL - Network Connection Query Language]] predicate that is evaluatad on a connection where we transition to.                                                                                        | No       |
| AddReverse    | If *true*, the reverse rule is added as well, i.e. from PredicateTo to PredicateFrom. The default is *false.*                                                                                               | Yes      |

Example content of a simple rule set is provided in the table below.
In your configuration, you can load these as a CSV-file, or into your data warehouse.

The first rule makes sure cables and connections (matching lv, mv and hv) will not connect from the schematic kind to the 'in place' kind.

The second rule ensures that we cannot go back from a public lighting starting point to a lv schematic connection. Note that this second rule can typically also be solved by using [[./Commodity Rules|Commodity Rules]].

| Disciplin | Block | PredicateFrom                                                   | PredicateTo                                                 | AddReverse |
| --------- | ----- | --------------------------------------------------------------- | ----------------------------------------------------------- | ---------- |
| E         | true  | AssetTableName=e\_?v_schematic_cable,e\_?v_schematic_connection | AssetTableName=e\_?v_inplace_cable,e\_?v_inplace_connection | true       |
| E         | true  | AssetTableName=e_pl_ignition_point                              | AssetTableName=e_lv_schematic_connection                    | false      |
