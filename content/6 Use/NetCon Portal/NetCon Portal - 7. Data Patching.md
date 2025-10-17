---
title: NetCon Portal - 7. Data Patching
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[./NetCon Portal - 6. Trace Form|previous]] [[./NetCon Portal - 8. Full-text search|next]]

# NetCon Portal - 7. Data Patching
Data patching functionality is available only for the NetCon layer. Data Patching allows updating the network and thus changing the tracing capabilities. Data Patching can be activated only when one feature is selected (update action) or two features are selected (add new link). 
The Data Patch form can be started from the Data patch button on the top button bar. The form provides different entry fields according to the selected action (update or create). Beside fields related to the Connection record, Action Id and Data patch reason can be entered as well. All these values will be stored in the DQOutput GeoNotes table. 
After the Data patch is processed, the network is recalculated (flow and sections). 
## Add Link
Select two existing nodes or links and then click Data patch button. From Id and To Id fields will be prefilled based on the selected features. Asset Table Name field offers a list of all asset table names recorded in the Connection table. Select appropriate value (e.g. a LV cable if patching a LV network) to proceed. 
## Cut Link
Select a connection (usually it will be a link) and hit the Data patch button. Check the Remove box. Hit Process patch to mark the Connection record as removed. This will remove the selected Connection record from the trace calculations. 
>[!info] Info
>This does not remove the Connection record nor the source asset record from the DB. 
## Change Barrier State
Select a connection record that is a barrier and hit the Data patch button. For barrier connections, the field Barrier state is enabled with the list of all barrier states. The list is set to the current value. Change it to a new state. After processing the patch, barrier state will be changed.
## Deleting the Data patches
Data patches are records in the DQOutput table. These records override the original Connection records. To revert the changes, the data patches can be simply deleted. You can list all data patches by running a predefined query *Data patches* or by browsing the DQOutput table. Click on a specific Data patch and use the Lite's standard tools for deleting a GeoNote record. 
After deleting a data patch, the network will recalculate again and redraw the map. 