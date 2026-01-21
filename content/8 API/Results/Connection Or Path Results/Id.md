---
title: Id
description: Id for the NetCon connection as described in this document, unique per network.
Type: long
Order: 10
Unique: true
permalink: Connection-Or-Path-Results/Id
aliases:
draft: false
date: 2025-06-05
tags:
  - ApiResult
  - ConnectionId
  - GettingStarted
---
# Id

Type of: _long_

Id for the NetCon connection as described in this document, unique per network.

In case this is a path, it is the unique id for last the connection used in the result path. This can also be used as a unique id for the path in a particular trace, since the same connection will not be returned twice. The [[./PreviousId|PreviousId]] points to the Id of the path leading to this one (in the same trace).

Previously this result attribute was called `ConnectionId`.

