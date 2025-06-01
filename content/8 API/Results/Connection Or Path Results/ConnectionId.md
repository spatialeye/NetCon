---
title: Id
description: Id for the NetCon connection as described in this document.
Type: long
Order: 10
Unique: true
permalink: Connection-Or-Path-Results/Id
aliases: 
draft: false
date: 2024-09-27
tags:
  - ApiResult
  - ConnectionId
---
# Id

Type of: _long_
Unique: _true_

Id for the NetCon connection as described in this document.

In case this is a path, it is the unique id for last the connection used in the result path. This can also be used as a unique id for the path in a particular trace, since the same connection will not be returned twice.

Previously this result attribute was called `ConnectionId`.

