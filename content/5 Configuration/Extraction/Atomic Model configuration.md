---
title: Atomic Model configuration
description: 
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# Atomic Model configuration

The atomic model is not intended for customization. In due time the seProject will be replaced by software, so changes that you will do make will forfeit in the future.

These items need to be configured:

- Name of the target warehouse model. For this, open the 'target' feature source, create the logical target model with the right coordinate system (same as other logical warehouse models that are used for assets), and set it as a target.
- Names of the input tables. The convention is that the first letter denotes the [[Disciplin|Disciplin]].
  - Rewire these by using the change feature source table function to the output of the NetConBase Output objects. E.g. the netcon_basenode table is called e_netcon_basenode, g_netcon_basenode, eo_netcon_basenode or gdo_netcon_basenode, hence the business collections are adapted.
- Name of the output table:
  - E.g. the netcon_connection table is adapted to the output, analogue to the input tables used. E.g. e_netcon_connection, g_netcon_connection, eo_netcon_connection or gdo_netcon_connection respectively.

The atomic model provides a single, but most important table: the [[../../6 Use/DataModel/NetCon Connection|NetCon Connection]].
