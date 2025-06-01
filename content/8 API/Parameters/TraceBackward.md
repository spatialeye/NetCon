---
title: TraceBackward
description: Normally, the trace-out and trace-neighbor follows the direction of the network. For unidirectional connections, that means it goes from [[FromId|FromId]] to [[ToId|ToId]], and the trace retrieves only unidirectional neighbors leading 'to' are retrieved. If TraceBackwards is set to true, the opposite direction is followed, and only unidirectional neighbors leading from [[FromId|FromId]] are retrieved. Typically, you do not need to specify this parameter.
Type: boolean
Order: 999
Mandatory: false
permalink: 
aliases: 
draft: false
date: 2024-09-30
tags:
  - ApiParameter
  - TraceBackward
---
# TraceBackward

Type of: _boolean_
Unique: __

Normally, the trace-out and trace-neighbor follows the direction of the network. For unidirectional connections, that means it goes from [[FromId|FromId]] to [[ToId|ToId]], and the trace retrieves only unidirectional neighbors leading 'to' are retrieved. If TraceBackwards is set to true, the opposite direction is followed, and only unidirectional neighbors leading from [[FromId|FromId]] are retrieved. Typically, you do not need to specify this parameter.
