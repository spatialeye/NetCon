---
title: TraceForward
description: Normally, the trace-path goes against the direction of the network, typically to find a source. For unidirectional connections, that means it goes from [[ToId|ToId]] to [[FromId|FromId]], and the trace retrieves only unidirectional neighbors leading 'from' are retrieved. If TraceForward is set to true, the opposite direction is followed, and only unidirectional neighbors leading from [[ToId|ToId]] are retrieved. Typically, you do not need to specify this parameter.
Type: boolean
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2024-10-29
tags:
  - ApiParameter
  - TraceForward
---
# TraceForward

Type of: _boolean_
Unique: __

Normally, the trace-path goes against the direction of the network, typically to find a source. For unidirectional connections, that means it goes from [[ToId|ToId]] to [[FromId|FromId]], and the trace retrieves only unidirectional neighbors leading 'from' are retrieved. If TraceForward is set to true, the opposite direction is followed, and only unidirectional neighbors leading from [[ToId|ToId]] are retrieved. Typically, you do not need to specify this parameter.
