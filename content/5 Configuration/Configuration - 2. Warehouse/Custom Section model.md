---
title: Custom Section model
description:
permalink:
aliases:
draft: false
date: 2024-10-01
tags:
---
# Custom Section model

By using the reducer, it is possible to generate area geometries for sections. This can be particular useful for purposes where one wants to make spatial relations to the network. The reason we don't provide area geometries to the Isolatable and Operated Sections, is that those are historized to do legal reporting and their design is kept minimal in order to keep changes low. The area geometry will change every time the network is updated and should rather not be historized since it will weigh on the spatial index.

Therefore, if you want area geometries for sections, use the aggregator feature source to produce those.

Example of sections with area geometries with NetCon
![[../../Zimages/section_areas_in_waternetwork.png|section_areas_in_waternetwork.png]]
