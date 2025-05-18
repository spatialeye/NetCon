---
title: Life Cycle Status
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - LifeCycleStatus
  - Overview
---
[[./Tracing and Querying/Basic network tracing|previous]] [[./Barrier or Operational State|next]]
# Life Cycle Status


A utility or telecom network is ever changing. In most registration systems, this is modelled via a **status** attribute of the asset representing the network to denote its lifecycle. Several different kind of status values can be stored, e.g. the operational state, which we store as **barrier**; When we talk about the status we mean the state of realization (planned, constructed, built, reserved, detached) of the asset, more precisely called the life cycle status.

The NetCon data model has two **time dimensions**. The first one is supplied by Spatial Eye Warehouse and Spatial Eye Design Repository to denote the fact date, which is of _history type II_ so every record has a from- and to- date. With the fact date is meant the date from which we know a fact to be true (i.e. from-date), till the date that we know this fact is replaced by a new fact about this asset, or removed (to-date).

The Spatial Eye Design Repository stores different designs and scenarios for the future network and provides a single consolidated time line in conjunction with Spatial Eye Warehouse. See also: [Warehouse User Meta Data](#https://documentation.geospatialanalysis.online/gsawarehouse/5_3_1/en/143117a0-d822-42f1-ae69-a484a2db0efa.htm).

The second time dimension has to do with the state of an asset that depicts the asset life cycle. Typically, a network asset such as a cable or substation is first 'envisioned,' then 'sketched,' then 'commissioned,' then 'built,' taken 'in service,' 'marked for removal,' 'removed,' 'reused' or 'dumped-as-junk.'

The enumerator storing the status has been constructed in such a way that it acts as a 'status dimension.' The value 0 means 'unknown' and is the default. We assume assets that are not labeled with a status to be 'in service,' however they are marked as 'unknown' with the value 0. The explicit value for 'in service' is 1.

On the negative scale, one finds planned assets, not realized yet. The further negative, the more away from realization. For exampled, 'commissioned' (to a contractor) is closer to being 'in service' than just 'envisioned.' On the positive scale, one finds assets that are realized and part of the network.

The more positive, the further away from being in service. For example, 'planned-to-be-detached' is larger than 'in service', and 'spare' is bigger even, while 'dumped-as-junk' is probably the largest.

Thus, all these different states of the asset life cycle can be depicted on an imaginary time scale, from planned (<0, unknown =0, in service >0 and <=10, to out of service >10). The more negative, the further away from realization. The closest to 1, the more in normal operation. This time scale has been designed this way so one can reason with a subset of the status time scale. Most of the times, one works just with the network as it is currently 'wired':

>	\>=0 and <= 10.

However, one may choose to reason with a future network that has been commissioned, without those parts of the network that are decommissioned:

>	= -10 and <= 1

By making the status a dimension, a range of values (start and end value) can be selected when doing a trace. This way one could also trace the network 'as if' (future scenarios, or when to include old assets in a restoration scenario). The default operation of the network is just to use status values >= 0 and <= 10, which are 'unknown', 'in service' and 'planned-to-be-detached'.

Typical values for the lifecycle are pre-populated as actual standard values in the [[../6 Use/Enumerators/NetCon Status Enumerator|NetCon Status Enumerator]]. In case you need to add values, please take care you insert the values in the proper timeline.

