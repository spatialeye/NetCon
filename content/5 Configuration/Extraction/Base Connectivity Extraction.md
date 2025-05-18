---
title: Base Connectivity Extraction
description: 
permalink: 
aliases: 
draft: false
date: 2024-10-02
tags:
  - ToDo
---
# Base Connectivity Extraction

#ToDo

This section describes how to configure NetCon network connectivity.

#### What is in the Smallworld topology

Please see Smallworld documentation.

#### Manifolds

Please see Smallworld documentation.

#### Internal Worlds

Also for using single World types outside the default Universe.
Please see Smallworld documentation.

#### Coordinate Systems

It is very important that for the base extraction the coordinate system is used that is also used to import the information in the GIS.

For example, if you GIS is using EPSG 27700, British National Grid, then use 27700 also to mark your dataset and in the extraction tables [NetCon base extraction for Smallworld](Base%2520Connectivity%2520Extraction.md##netcon-base-extraction-for-smallworld). The EPSG CS is in meters, so in case your data is in the "(SW) British National Grid (mm)" you need to provide a compensation factor:

    var ext_scale_factor = 0.001;

Please see Smallworld documentation.

#### Configuring topology bound assets

#### Relations inside asset objects

#### Configuring topology inside assets

#### Relations outside the manifold
