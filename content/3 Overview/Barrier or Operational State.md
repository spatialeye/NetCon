---
title: Barrier or Operational State
description: 
permalink: 
aliases:
  - Barrier
  - Operational State
draft: false
date: 2025-04-17
tags:
  - Barrier
  - OperationalState
  - Overview
---
[[./Life Cycle Status|previous]] [[./Referential Information|next]]
# Barrier or Operational State

Connections can be conducting or barring/blocking the flow of the [[./Commodity|Commodity]], i.e. opened or closed. The flow is assumed to be barred when isbarrier > 0, and conducting/flowing isbarrier < 0. Normal connections that are not operated have isbarrier = 0.

Typical values are -1 (can be barrier) and 1 (is barring). Other values are reserved 'mostly barring' behavior (-2) for trickle throughput (so it is conducting a little bit, a bit like traffic in a traffic jam. This is used to avoid contaminations is mazed water networks.

Autonomous switching can also be designated. The value -10 means conducting is the default, but an autonomous system can switch the flow off, and 10 means barring is the default but it can be switched on autonomously.

See also [[../6 Use/Enumerators/NetCon Barrier Enumerator|NetCon Barrier Enumerator]] for the list of all values.
