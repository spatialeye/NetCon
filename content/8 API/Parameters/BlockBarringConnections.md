---
title: BlockBarringConnections
description: If true (default) then connections that are barring (blocking the commodity flow) will be blocking in the trace. If false then barring connections will be used in the trace as if they where conducting. Note that if [[StopAtBarringConnections|StopAtBarringConnections]] is true, then this parameter will be ignored, since it would undo the other.
Type: boolean
Order: 999
Mandatory: false
permalink: 
aliases: 
draft: false
date: 2024-10-02
tags:
  - ApiParameter
  - BlockBarringConnections
---
# BlockBarringConnections

Type of: _boolean_
Unique: __

If true (default) then connections that are barring (blocking the commodity flow) will be blocking in the trace. If false then barring connections will be used in the trace as if they where conducting. Note that if [[StopAtBarringConnections|StopAtBarringConnections]] is true, then this parameter will be ignored, since it would undo the other.
