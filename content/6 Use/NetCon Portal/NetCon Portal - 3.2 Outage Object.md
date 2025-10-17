---
title: NetCon Portal - 4. Outage Object
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 3.1 Outage Impact Analysis|previous]] [[./NetCon Portal - 3.3 Outage Analysis & Monitor panel|next]]

# NetCon Portal - 3.2 Outage Object
After running the Outage Impact Analysis trace, the results can be stored in as an object Outage. 
## Save Outage
The button Save Outage can be found on the Outage Analysis panel, available only after Outage Impact Analysis was run. The button starts a form where attributes are set for the stored Outage object: Status, Valid from, Valid to and Description. 
Form checks if time is set correctly (e.g. cannot set past time). 
![[../../Zimages/Outage_save.png|Outage_save.png]]
Submitting form will create a new Outage GeoNotes record with the attributes set in the form as well as with additional information from the Outage Impact Analysis trace (start connection ID values, affected customers etc.). 
After creation, Outage area will appear on the map. Color is dependent on the saved Status value. 
![[../../Zimages/Outage_on_map.png|Outage_on_map.png]]

## Update Outage
The button Update Outage is available from the Feature property panel of the selected Outage record. The button launches the same form as for creation, however now with the option to update the Outage area enabled. 
## Re-run Outage Analysis
The button Re-run Outage is available from the Feature property panel of the selected Outage record. The button runs Outage Impact Analysis trace from an existing Outage object with stored (pre-defined) connection ID values. 
In case the circumstances of the network change, this action might return new results (area, list of barriers, list of service points). In this case, it is recommended to update the Outage object. 
## Outage pop-up bubble
Hovering over an Outage record in the map will display a pop-up bubble that shows a brief description and selected fields of the outage object. This bubble has a Select button which selects the record and opens the Feature property panel. Additionally, join fields Affected Customers and Valves To Close (or other name appropriate to the type of network commodity) will display the records related to the Outage in the Query result dialog. 
Pop-up bubble is set up in the Portal, Features section, Preview tab. 
![[../../Zimages/Outage_popup_bubble.png|Outage_popup_bubble.png]]