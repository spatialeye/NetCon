---
title: Base Connectivity Extraction
description:
permalink:
aliases:
draft: false
date: 2024-10-02
tags:
---
# Base Connectivity Extraction

This section describes how to configure NetCon network connectivity.
Spatial Eye consultants have a standardized process of extracting network connectivity information from Smallworld.
It must be kept standard, because it will be replaced by more advanced software that can handle delta's. 

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

Assets in the GIS that have topology need to be denoted when 

#### Relations inside asset objects

#### Configuring topology inside assets

#### Relations outside the manifold

