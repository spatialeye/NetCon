---
title: SmartStart
description: If true, then the Start connections will be exempted from Block and Stop predicates, avoiding them from starting at all, or returning the obvious.
Type: boolean
Order: 999
Mandatory: false
permalink:
aliases:
draft: false
date: 2025-02-18
tags:
  - ApiParameter
  - SmartStart
---
# SmartStart

Type of: _boolean_
Unique: __

If true, then the Start connections will be exempted from Block and Stop predicates, avoiding them from starting at all, or returning the obvious.

Note that since behavior changed in version [[../../2 Version And Release Information/2.2 Version Information|Spatial Eye NetCon 2025.3.2.6]] .
In earlier versions the Start connections would be exempted from the Yield as well. This is no longer the case, which means a Yield can also result in a start element being returned. This will affect the [[../Calls/TracePath|TracePath]] call, which stops after finding the first path.
In case this is undesired, the user can add the start criteria to be excluded from the yield, where applicable.