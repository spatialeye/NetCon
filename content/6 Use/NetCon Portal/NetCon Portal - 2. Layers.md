---
title: NetCon Portal - 2. Layers
description:
permalink:
aliases:
draft: false
date: 2024-12-19
tags:
---
[[./NetCon Portal - 1. Introduction|previous]] [[./NetCon Portal - 3.1 Outage Impact Analysis|next]]

# NetCon Portal - 2. Layers
NetCon Portal provides two data layers: **Default** and **NetCon**. 
## Default
Default layer displays the source GIS objects, added GeoNotes objects such as Outage and Observation, as well as flow arrows (in the background) of the related Connection records. 
![[../../Zimages/Layers_default.png|Layers_default.png]]
## NetCon
NetCon layer displays only Connection records. Usually, the [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Control or NetCongestion Sections|Control or NetCongestion Sections]] or [[../../5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Operated Sections|Operated Sections]] are displayed. Sections are distinguished by a color. 
![[../../Zimages/Layers_NetCon.png|Layers_NetCon.png]] 
# Layer setting in admin portal
Because of the need to redraw recalculated flow and updated styles of modified objects, all layers are set as Dynamic with 0 minute refresh interval. 
![[../../Zimages/Layers_Portal_settings.png|Layers_Portal_settings.png]]
