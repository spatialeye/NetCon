---
title: NetCon Portal - Observation
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 3.3 Outage Analysis & Monitor panel|previous]] [[./NetCon Portal - 5. Barrier State Change|next]]

# NetCon Portal - 4. Observation
Observation is an object that reports observed events (e.g. gas leak) on the network.   
## Add Observation
The action button Add Observation is available on the Feature property panel or on the context menu for most selected assets (e.g. a pipe). The button first prompts a user to enter a geometry and then launches a form where Observation attributes are set. Submitting the form stores the attributes in a new GeoNotes Observation record, with a link to the selected feature record as its parent (e.g. a pipe ID). 
![[../../Zimages/Observation_form.png|Observation_form.png]]

After creation, new Observation object will appear on the map (a warning symbol).
![[../../Zimages/Observation_created_on_map.png|Observation_created_on_map.png]]

## Update Observation 
The button Update Observation is available on the Feature property panel of an Observation record. It starts the same form as when creating the Observation. Submitting form updates the existing Observation record. 
## Update Observation Location 
The button Update Observation Location updates just the location of the existing Observation record. After clicking the button, user will be prompted to enter a new geometry for the observation. The location can be placed anywhere but it is recommended to place it near the location of the object that the observation event is being reported on. 