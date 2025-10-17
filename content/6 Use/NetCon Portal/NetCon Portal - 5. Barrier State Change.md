---
title: NetCon Portal - 5. Barrier State Change
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 4. Observation|previous]] [[./NetCon Portal - 6. Trace Form|next]]

# NetCon Portal - 5. Barrier State Change
In NetCon Portal the state of barriers can be changed. This change then affects the behavior of the Outage Impact trace and other functions. Barriers are objects that can stop the flow of the commodity, such as valve for water and gas networks or circuit breakers for electricity. 
## Change State
The button Change State is available on the Feature property of a selected barrier (e.g. a valve) or via a context menu. 
Simple form is opened. The state displays the current state of the barrier. Change the state to a new value. Additional information describing the reasoning behind the state change can be added. 
![[../../Zimages/BarrierChange_form.png|BarrierChange_form.png]]

**Available states**: 
- Open
- Closed
- Always Open (i.e. cannot be closed)
- Always Closed (i.e. cannot be opened) - only for electricity

>[!NOTE] Note 
>States Open and Closed for gas and water networks translate to isConducting and isBarrirng. For electricity this translates to the opposite, Open = isBarring and Closed = isConducting.
### Setting barrier to isAlwaysConducting (i.e. for water Always Open)
Barries set to isAlwaysConducting are not considered as an operable barrier during the Outage Impact trace. As a result, the trace continues past this barrier. 
Setting back the barrier to isConducting will make it operable again.
### Setting barrier to isBarring (i.e. for water to Closed)
Barries set to isBarring stop the flow of the commodity. This leads to re-calculation of the flow of the network. If there is no alternative source, then the part of the network beyond the isBarring barrier will have no flow (i.e. customers will be without a service). 

>[!Warning]- Functionality currently out of scope
>**Automatic Outage creation**: When barrier is set to isBarring, an active Outage object is created automatically around the affected area with no flow.
>**Automatic update of Connection History**: Every change of a barrier state is recorded in Connection History table. 
>**Automatic update of ServiceDownLog**: After barrier is set to isBarring, detected no-flow service points are stored in the ServiceDownLog table. 