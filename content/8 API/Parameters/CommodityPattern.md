---
title: CommodityPattern
description: "[[NetConQL - Specification|NetConQL - Specification]] expression pattern to match [[commodity|commodity]] properties, which are net, function and details. For example `net=hv` matches high voltage, where `net=mv,lv` matches medium and low voltage. Also, `function>=10000` matches any commodity, 10.000 volts or higher. Furthermore, `details=ABCN` matches anything for subnetwork, any function and phases A,B, C as well N need to be present, and similarly `details=ABC*` has the neutral phase optional."
Type: string
Order: 999
Mandatory: false
permalink: 
aliases: 
draft: false
date: 2025-01-17
tags:
  - ApiParameter
  - CommodityPattern
  - Commodity
  - NetCon2
  - ToDo
---
# CommodityPattern

#ToDo In the current release only subnetwork matching is implemented.

Type of: _string_
Unique: __

[[NetConQL - Specification|NetConQL - Specification]] expression pattern to match [[commodity|commodity]] properties, which are net, function and details. For example `net=hv` matches high voltage, where `net=mv,lv` matches medium and low voltage. Also, `function>=10000` matches any commodity, 10.000 volts or higher. Furthermore, `details=ABCN` matches anything for subnetwork, any function and phases A,B, C as well N need to be present, and similarly `details=ABC*` has the neutral phase optional.
