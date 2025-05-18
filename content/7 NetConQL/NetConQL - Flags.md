---
title: NetConQL - Flags
description: 
permalink: 
aliases: 
draft: false
date: 2025-01-17
tags: 
---
# NetConQL - Flags

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
