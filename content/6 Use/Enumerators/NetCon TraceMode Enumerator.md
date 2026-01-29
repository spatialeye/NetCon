---
title: NetCon TraceMode Enumerator
description: Determines the way tracing algorithms can walk through the network.
permalink:
aliases:
draft: false
date: 2026-01-27
tags:
---
# NetCon TraceMode Enumerator

Enumerator that determines the way tracing algorithms can walk through the network.
The enumerator partially works as flags, e.g. normal+backwards=any and, down+up=meshed.

See also [[./NetCon Trace Function and Mode|NetCon Trace Function and Mode]] for the combination effect between Function and Mode.

| Mode Id     | Mode              | Description                                                                                                                                                              |
| ----------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1           | normal            | Follow connections in the order from FromId to ToId and reversed if bidirectional.                                                                                       |
| 2           | backwards         | Opposite of 'normal'; unidirectional connections are traversed in the opposite direction.                                                                                |
| 3           | any               | Ignore directionality of the connections.                                                                                                                                |
| 4           | down              | Follow flow downstream flow (as determined by barriers, commodity rules and flow restrictions).                                                                          |
| 8           | up                | Follow flow upstream flow (as determined by barriers, commodity rules and flow restrictions).                                                                            |
| 12          | meshed            | Follow flow upstream or downstream flow (as determined by barriers, commodity rules and flow restrictions).                                                              |
| 16          | barring           | Flag to indicate that barring barriers should be considered during the trace. Only makes sense in combination with 'down', 'up' and 'meshed'.                            |
| 20 (16+4)   | downInclBarring   | Follow the down flow, and pass through barring barriers. If a meshed flow exists beyond those, the down flow can continue, otherwise it stops at the barring barrier.(*) |
| 24 (16+8)   | upInclBarring     | Follow the up flow, and pass through barring barriers. If a meshed flow exists beyond those, the up flow can continue, otherwise it stops at the barring barrier.(*)     |
| 28 (16+8+4) | meshedInclBarring | Follow meshed flows, and pass through barring barriers. If a meshed flow exists beyond those, the down flow can continue, otherwise it stops at the barring barrier.(*)  |

(\*) It is only in very peculiar situations that flow is going towards a barring barrier, but those can exist if it 'by-passes' the barrier.
