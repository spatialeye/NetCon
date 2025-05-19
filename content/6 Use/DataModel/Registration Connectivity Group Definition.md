---
title: ConnectivityRuleGroupDefinition
description: 
permalink: 
aliases:
  - Manifold Definition
draft: false
date: 2024-10-02
tags: 
---
# Registration Connectivity Group Definition

Old name: Manifold Definition

List of the source systems topology interaction groups. All objects with the same group, which is called a **connectivity rule group** or **manifold**, can topologically interact, i.e. share nodes and links. The definition of the table contents is standard and should not be altered.

| Field | Type    | Description                                                                                                                 |
| ----- | ------- | --------------------------------------------------------------------------------------------------------------------------- |
| Id    | integer | Positive integer representing the Id of a `connectivity rule` or `manifold` in the source system. Old name: `ManifoldCode`. |
| Name  | string  | String internal name of the connectivity rule or topology interaction group in the source system.                           |
