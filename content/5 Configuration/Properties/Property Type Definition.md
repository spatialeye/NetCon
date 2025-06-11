---
title: Property Type Definition
description: 
permalink: 
aliases: 
draft: false
date: 2025-06-05
tags: 
---
# Property Type Definition

It is possible to fix property types for certain property names.
Optionally, such a name may include a parent reference.

The business collection must have a fixed name, namely `NetConPropertyTypeDefinition`.

The NetConPropertyTypeDefinition collection has the following definition:

| FieldName | FieldType                                                              | Optional |
| --------- | ---------------------------------------------------------------------- | -------- |
| FieldName | String, e.g. `buildyear` or `length` or `eancode.id`                   | No       |
| FieldType | String. Values must be one of: String, DateTime, Double, Long, Boolean | No       |
| Unit      | String, e.g. `m` for meter or `m2` of squared meter.                   | Yes      |
Fieldnames without a '.' will apply to all properties with that name.
If the fieldname contains a '.', it is assumed that the first part denotes the parent.

## Specifying the rules

For the configuration, you can model this as a csv file and open it with the Excel feature source, or have it stored in the database.
## Loading the rules

The rules are loaded once upon opening the feature source.