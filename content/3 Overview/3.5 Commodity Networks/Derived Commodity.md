---
title: Derived Commodity
description:
permalink:
aliases:
draft: false
date: 2025-06-01
tags:
  - Overview
  - ToDo
  - GettingStarted
---
# Derived Commodity

[[./Commodity|previous]] [[./Network Ontology|next]]

#ToDo Note that deriving commodities is a [[../../2 Version And Release Information/2.3 Roadmap|2.3 Roadmap]] topic and not yet complete.

In the asset registration, it is not always clear - when dealing with asset records and their directly related records - what the direct commodity and its details are.

When the network is directionalized on flow, (partly) missing commodities will be derived.

So, reasoning from the source, if a connection has commodity 'MV:50000:ABCN', and the next connection does not have a commodity, it will be derived to be 'MV:50000:ABCN' as well.

Likewise, if a connection has 'MV:50000:ABCN', and the next connection is 'MV::A', then it will be completed to 'MV:50000:A'.


