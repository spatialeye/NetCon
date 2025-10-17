---
title: Spatial Warehouse Best Practices
description:
permalink:
aliases:
draft: true
date: 2024-10-02
tags:
---
# Spatial Warehouse Best Practices

A complete training course exists to make you familiar with running Spatial Warehouse ETL batches in an optimal way. It is a time saver.

## Best practices for naming seProjects

A typical convention is to name your configurations like:

    <SourceAppName>_<Discipline>_model_yyyyMMdd.seProject

    gridos_elec_model_20231212.seProject

The warehouse can use the yyyyMMdd format for various purposes.
Every time you make changes to the file after it has been used to run a batch with, the yyyyMMdd should be increased. In other words, don't every update a file after it has been used for ETL batches, your meta data becomes useless.

For source control and automatic deployment, this is less handy, and people omit the yyyyMMdd. Still your meta data should be worth more.

- It is a good practice to maintain a change log file for every configuration. For this, you can create and maintain an rft file with the same name as the seProject file.

Keep a change log with your configurations, so it will using that opens on startup:
![[../../Zimages/keeping_configuration_changelog.png|keeping_configuration_changelog.png]]]
