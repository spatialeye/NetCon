---
title: Admin portal configuration
description:
permalink:
aliases:
draft: false
date: 2025-10-03
tags:
---
[[./NetCon Portal - 1. Viewer Project configuration|previous]]
# Admin portal configuration
Recommended configuration of the NetCon Portal application in the admin portal. Only configuration that is different from the default setting will be mentioned. 
## Application configuration (e.g. Water Demo)
- Maps and layers > Layers > Visible as a side panel = uncheck
- Maps and layers > Layers > Popup-menu button on the map = check
- Maps and layers > Restrictions > Maximum zoom level = 23
- Maps and layers > Interaction > Enable map rotation = uncheck
- Maps and layers > Interaction > Enable map tilting = uncheck
- Searching > Search menu > All full-text search categories & All geocoders & WGS 84 Coordinate
- Features > Allowed GeoNotes > DQOutput (this will enable build-in GeoNotes update tools just for this table, other tables are handled via custom forms)
- Querying > Settings > Appearance = Query selector on map
- Miscellaneous > UI mode > UI mode = Collapsible floating panels
- Miscellaneous > Other > Enable downloads panel = uncheck
## General map layer configuration
This can be found under the Server settings. Set max zoom level of all layers to level 23 and set the layers to Dynamic with 1 minute refresh interval. 
## Full-text search population
If the viewer project has full-text business collections set up, then in Scheduling & tasks create a new Full-text search indexing task and run it to populate the search. 