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
---
# CommodityPattern

In the current release subnetwork matching is implemented, as well as querying on e.g. voltage level and phase information.
See also [[../../7 NetConQL/NetConQL - Network Connection Query Language|NetConQL - Network Connection Query Language]].

Type of: _string_
Unique: __

[[NetConQL - Specification|NetConQL - Specification]] expression pattern to match [[commodity|commodity]] properties, which are net, function and details. For example `net=hv` matches high voltage, where `net=mv,lv` matches medium and low voltage. Also, `function>=10000` matches any commodity, 10.000 volts or higher. Furthermore, `details=ABCN` matches anything for subnetwork, any function and phases A,B, C as well N need to be present, and similarly `details=ABC*` has the neutral phase optional.


