---
title: Specification
description: Spec of type information of the asset, that provides relevant characteristics of the asset. E.g. for an electric network this could be the core diameter and impedance, for a gas or water network the diameter and resistance, and for a telecom network the light characteristics. If enrichment information has been configured, a whole range of additional [[specification-enrichment|specification attributes]] can be retrieved.
Type: string
Order: 999
Unique: false
permalink: 
aliases: 
draft: false
date: 2024-09-30
tags:
  - ApiResult
  - Specification
---
# Specification

Type of: _string_
Unique: __

Spec of type information of the asset, that provides relevant characteristics of the asset. E.g. for an electric network this could be the core diameter and impedance, for a gas or water network the diameter and resistance, and for a telecom network the light characteristics. If enrichment information has been configured, a whole range of additional [[specification-enrichment|specification attributes]] can be retrieved.

Note that if the specification contains a property with the key `id`, it will be renamed in the output to `Specification.Id` as not to conflict with the [[./ConnectionId|ConnectionId]] of the Connection.

When the specification string input is parsed, the type of the value is [[../../../5 Configuration/Properties/Property Type Determination|determined according to rules]].
