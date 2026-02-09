---
title: NetConQL - Flags
description:
permalink:
aliases:
draft: false
date: 2026-01-29
tags:
---
# NetConQL - Enumerator Flags

## Role enumerator

The [[../8 API/Results/Connection Or Path Results/Role|Role]] property is an enumerator where values can be combine. In other word, its values are 'flags' that can be combined. Sometimes combinations have been given a better name, for example:

	Prosumer ::= Producer | Consumer

Hence, in NetConQL, the following is identical:

	role LIKE Producer | Consumer 
	role LIKE Prosumer

The result is, that this predicate expression will match with

* Consumer
* Producer
* Prosumer

The use of `LIKE` is here clearly different from '=' (equals). Thus:

	role=Prosumer

will matches only with

* Prosumer

## Barrier enumerator

The `BlockBarring` parameter in the Block clause is translated to an enumerator range:

| Input                 | Rewrite                  |
| --------------------- | ------------------------ |
| BlockBarring=true     | Barrier>=IsConducting    |
| NOT BlockBarring=true | Barrier<=NoBarrier       |
| BlockBarring=false    | *no barring restriction* |

The [[../6 Use/Enumerators/NetCon Barrier Enumerator|NetCon Barrier Enumerator]] uses ranges for convenience, to deal with many states with a simple predicate.

If you write `Barrier=IsConducting` this filters out just one value.

## Status enumerator

Typically the [[../6 Use/Enumerators/NetCon Status Enumerator|NetCon Status Enumerator]] is used in a range, e.g. by default all input connections for the TraceAPI are filtered on:

State>=unknown AND State<=decommissioned

If you load more connections with a bigger status range, you may want to restrict it per query, e.g. in the [[../8 API/Calls/PredicateQuery|PredicateQuery]] you can use as a [[../8 API/Parameters/BlockPredicate|BlockPredicate]]:

State>=builtneverused AND State<=torelocate AND BlockBarring=true



