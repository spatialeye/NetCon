---
title: NetCon Status Enumerator
description: Encodes the statuses that are encountered in the asset registration as used in NetCon.
permalink: 
aliases: 
draft: false
date: 2025-04-18
tags: 
---
# NetCon Status Enumerator

Enumerator encoding the statuses that are encountered in the asset registration as used in NetCon.
The definition and contents of the table is standard and should not be altered unless consulted with Spatial Eye. In case you encounter a new status value that needs to be plotted on the asset life cycle time dimension, please contact us so we can keep the interpretation and usage consistent across all implementations.

| StatusCode | StatusValue         | Description                                                                                         |
| ---------: | ------------------- | --------------------------------------------------------------------------------------------------- |
|          0 | unknown             | Unknown, which mostly likely is 'in service'.                                                       |
|          1 | in service          | Normal operating mode.                                                                              |
|          2 | in service revision | Normal operating mode, ongoing registration.                                                        |
|          5 | temporary           | Connected to the network, hence in service, as a temporary fix.                                     |
|          7 | data hot fix        | Missing in the registration but known to be there.                                                  |
|          8 | to relocate         | Proposed to be relocated, but still in service now.                                                 |
|         10 | decommissioned      | Proposed to be abandoned, but still in service now.                                                 |
|         13 | rejected            | In service but rejected because of a data quality problem.                                          |
|         15 | inactive            | Built, has been in service but not now, and is still connected.                                     |
|         20 | reserved            | Designated capacity that is reserved for a specific purpose.                                        |
|         25 | spare               | Spare capacity that is reserved to extend the network quickly.                                      |
|         30 | out of service      | Disconnected from the network, but not removed, could be attached again.                            |
|         40 | to remove           | Proposed to be removed from the network, needs to be excavated or physically removed.               |
|         45 | incapacitated       | Made unusable, e.g. by filling or burning out. 'Gedemmered' in Dutch, which means it is closed off. |
|         50 | junk                | Never to be in service again.                                                                       |
|         -2 | built never used    | Not in service yet, needs to be connected.                                                          |
|         -4 | to install          | Proposed to install, detailed design has been created and approved.                                 |
|         -5 | commissioned        | Approved to be built by a contractor, but not realized yet.                                         |
|        -10 | planned             | Planned as a design to be realized, but not yet commissioned.                                       |
|        -25 | designed            | Designed and approved, not planned or commissioned.                                                 |
|        -40 | envisioned          | Part of the long term vision to realize capacity.                                                   |
|        -50 | sketched            | Preliminary first draft of design.                                                                  |


