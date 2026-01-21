---
title: NetCon Portal - 1. Introduction
description:
permalink:
aliases:
draft: false
date: 2025-10-01
tags:
---
[[NetCon Portal - 2. Layers |next]]
# NetCon Portal - 1. Introduction
NetCon Portal is a web application based on product SE Lite. NetCon Portal serves as a frontend gateway to NetCon functionality, especially its traces capabilities. On top of that, in NetCon Portal users have the option to store objects that help with recording events on the network. The functionality of NetCon Portal can be divided into three main sections: Outage, Data patching and Tracing. 

**Outage** offers tailored functions for one specific type of trace - outage impact analysis. The result of this trace show the whole part of network that would be impacted if an outage (planned or unplanned) occurred on a specific network asset (e.g. a pipe). Furthermore, the list of affected customers and the list of operable barrier objects (such as a valve in water networks) is returned as well. These results can be stored in the DB. Further 'outage' functions offer saving an observed event on the network into the DB or changing a state of a barrier object (e.g. closing a valve). 

**Data patching** allows the user to fix the network 'on the fly' and shortly see how the network got recalculated. This way the flow of the commodity can be altered and thus modifying the trace results. With the functions of data patching, new connection links can be added, connections can be removed or the state of connections that are barriers can be changed. 
>[!note]
>Data patching works only with the Connection table, it is not patching the source GIS records. 

**Tracing** offers all tracing capabilities of NetCon in a user friendly form. The advantage of this functionality is that the results of a trace are highlighted in the map and the data it finds are listed in the Query result dialog from where the data can be exported to various data formats or reported using a predefined report template. There is also an option to store a specified trace criteria as a trace template for later repeated use.  

![[../../Zimages/NetConPortal_intro.png|NetConPortal_intro.png]]
