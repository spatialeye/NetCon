---
title: Configuration of Connectivity Viewing
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-30
tags:
  - GettingStarted
  - ToDo
---
[[../../4 Getting started/Connectivity Extraction Process|previous]]
# Configuration of Connectivity Viewer


It is good practice to share a viewing application to see NetCon connectivity data, either by using the desktop or server. It is many times faster to see and understand the data graphically than in tabular form. Hence, much time has been dedicated in creating a viewer.seProject.

Typically the connectivity data is viewed:

- Classified from its origin, e.g. asset_table_name and or manifold. These can also be used in combination with business filter in the desktop tool;
- Classified by isolated section;
- Classified by operated section;
- Upstream and downstream flow indication.

#ToDo Insert examples of each seen in the viewer here.
Also, put in some examples of the web viewer.

Example of flow of an electric network
![[../../Zimages/sections_and_flow_in_elec_network.png|sections_and_flow_in_elec_network.png]]
Example of flow of an electric network. The flow is computed from the source of the commodity and will change .

Two types of configurations can be created:

- For viewing the NetCon data as stored in the database;
- For interacting with the NetCon data as used in Trace expressions and the Trace API.

#### Styling

The templates provided have examples of slicing the network on color, for the isolatable section (on GeometryLSection, GeometryPSection and MidPoint) as well as the operated section (on GeometryLSection, GeometryPSection and MidPointSection; the latter fields have been made hidden). The expressions for ColorCode and SectionColorCode are respectively:

    (SuperSectionId % 20).ToString()
    (SectionId % 20).ToString()

The styles slices are depicted below. Note that the style slice tree can be copied and pasted with Ctrl-C, Ctrl-V from the template configuration to your own. (Note that when this does not work, you will need to fix the internal field name in the expression. Checkout you clipboard in Notepad++ en checkout the internal field names with Ctrl-I.)

Thematic style for NetCon points assets:

![[../../Zimages/netcon_geometryp_style_slice.png|netcon_geometryp_style_slice.png]]

Thematic style for NetCon line assets:

![[../../Zimages/netcon_geometryl_style_slice.png|netcon_geometryl_style_slice.png]]

Thematic style for NetCon up- and downstream flow:

![[../../Zimages/netcon_flow_style_slice_down.png|netcon_flow_style_slice_down.png]]
![[../../Zimages/netcon_flow_style_slice_mazed.png|netcon_flow_style_slice_mazed.png]]
![[../../Zimages/netcon_flow_style_slice_no_source.png|netcon_flow_style_slice_no_source.png]]
![[../../Zimages/netcon_flow_style_slice_up.png|netcon_flow_style_slice_up.png]]

#### Relations

Relations between business objects facilitate data inspection.
NetCon has been designed to enable data lineage to the source, since data quality problems typically occur in networks.

In the template configuration for a `seProject` file the relations for ease of navigion have been configured.
You can find the definitions of the relations in that projectfile.
The following relations are found to be useful:

| From Table | To Table | Type | Relation name | Description |
| ---------- | -------- | :--: | ------------- | ----------- |
| NetConConnection | NetConConnection | n-m | Neighbor Connections | Retrieves neighbors of which the FromId or ToId are equal to the my FromId or ToId, excluding self. The reverse relationfield is hidden. |
| NetConConnection | NetConSection | n-0 | IsolatableSection | Retrieves the isolatable section to which this belongs. |
| NetConSection | NetConConnection | 0-n | Connections | Retrieves the connections that are in this isolatable section. |
| NetConSection | NetConSection | n-m | Neighbor Isolatable Sections | Retrieves neighbors of which the FromId or ToId are equal to the my FromId or ToId, excluding self. The reverse relationfield is hidden. |
| NetConConnection | NetConSuperSection | n-0 | OperatedSection | Retrieves the operated section to which this belongs. |
| NetConSuperSection | NetConConnection | 0-n | Connections | Retrieves the connections that are in this isolatable section. |
| NetConSuperSection | NetConSuperSection | n-m | Neighbor Operated Sections | Retrieves neighbors of which the FromId or ToId are equal to the my FromId or ToId, excluding self. The reverse relationfield is hidden. |
| NetConSection | NetConSuperSection | n-0 | OperatedSection | Retrieves the operated section to which this belongs. |
| NetConSuperSection | NetConSection | 0-n | Sections | Retrieves the sections that are in this isolatable section. |
| NetConConnection | \<AssetTable> | n-1 | Asset | Retrieves the original asset from which the connection as generated. This can be any of the tables that are refered to via the AssetTableName and AssetId of the connection, which are part of the connectivity of the network. Use the expression (1) below. |
| NetConConnection | \<AssetTable> | n-m | AssetHierarchy | Retrieves the original assets that have a hierarchy relation with the connection, i.e. they contain it or are contained by it. This should return one asset for each object that is mentioned in the asset hierarchy. Use the expression (2) below. |

Expression for Asset relationship (1):

    FeatureUrn(Concat("B|", Netconconnection.assettablename, "|", Netconconnection.assetid))

Expression for AssetHierachy relationship (2):

    {
        var any = Not (IsNullOrEmpty(Netconconnection.assethierarchy));
        # every business collection should be referred to as 'B|<collectionname>'
        var a = "B|" + Netconconnection.assethierarchy;
        var objectspath = a.Replace(".id=", "|").Replace(",", "^|^B|");
        
        return MultiFeatureUrn(objectspath);
    }

