---
title: Flow
description: Direction of commodity. 'DownStream' if the commodity flows from FromId towards ToId, 'Meshed' if the networks barriers are such that the flow can go both ways, i.e. from sources at either side, 'NoFlow' if no connected path to a Source exists. Upstream, when streaming from ToId to FlowId. Note that you should never see 'UpStream' in API call results since it swaps the FromId and ToId so the flow is 'DownStream' instead.
Type: string
Order: 999
Unique: false
permalink:
aliases:
draft: false
date: 2025-06-11
tags:
  - ApiResult
  - Flow
---
# Flow

Type of: _string_

Direction of commodity. 'DownStream' if the commodity flows from FromId towards ToId, 'Meshed' if the networks barriers are such that the flow can go both ways, i.e. from sources at either side, 'NoFlow' if no connected path to a Source exists. Upstream, when streaming from ToId to FlowId. Note that you should never see 'UpStream' in API call results since it swaps the FromId and ToId so the flow is 'DownStream' instead.

The flow is computed as downstream seen from Connections with the [[./Role|Role]] = [[../../../3 Overview/3.5 Commodity Networks/Sources|Source]].

The flow describes the direction of the flow of the [[../../../3 Overview/3.5 Commodity Networks/Commodity|Commodity]] in a connection, or how the connection is used in the network:

| Code | Value     | Meaning                                                                                                                  |
| ---- | --------- | ------------------------------------------------------------------------------------------------------------------------ |
| 0    | none      | The connection is not fed from a source. Possible some [[./Barrier|Barrier]]s are barring, or may be there is no source connected. |
| 1    | down      | The connection is used from FromId to ToId.                                                                              |
| 2    | up        | The connection is used from ToId to FromId.                                                                              |
| 3    | meshed    | Up as well as down; which means the connection is fed from a [[../../../3 Overview/3.5 Commodity Networks/Sources\|Source]] at either side.                         |
| 4    | violation | Not used. A violation would be if a non [[./BiDirectional|BiDirectional]] connection is used up. The software prevents this.             |
| 8    | no engine | The flow could not be computed since the engine has not been initialized.                                                |
## Rules

Flow is affected by [[../../../5 Configuration/Configuration - 4. Commodities/Commodity Rules|Commodity Rules]] as well as [[../../../5 Configuration/Configuration - 4. Commodities/Flow Transition Rules|Flow Transition Rules]].

## Meshed

If several sources are feeding the same parts of the network, this could also lead to [[Flow#Meshed|Meshed]] networks. In NetCon, `Meshed` means that it is unclear from which direction a source is feeding the connection.

It is quite common from water and gas networks to be fed in a Meshed fashion; for electricity this is more rare. Typically, a Meshed network is more resilient to outages and it can balance out its load more easily. This comes at a cost: it is harder to manage. E.g. a Meshed water network needs regular cleaning.

## Tracing with flow
The flow can be used for more efficient tracing. Whereas normal tracing goes in all direction, using [[../../../9 Expressions/NetworkResult Expressions/TraceOutUp()|TraceOutUp()]], [[../../../9 Expressions/NetworkResult Expressions/TraceOutDown()|TraceOutDown()]] follow the pre-dermined flow. This makes it more efficient.

When you want to trace over a Meshed network only, you can use [[../../Calls/TraceMeshed|TraceMeshed]].