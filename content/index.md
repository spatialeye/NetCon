---
title: Welcome to NetCon
description: Starting page for the NetCon documentation
permalink: index.html
aliases:
  - LandingPage
draft: false
tags:
  - Index
date: 2024-09-26
Version: 2024.1.3
Product: NetCon 2.0
srcLang: en-US
---
This is the NetCon 2.0 [documentation](https://kenkor.github.io/NetCon/Home).
# It is all about the Network: NetCon

Welcome to the online Spatial Eye NetCon Help site. 
Here you will find information about the why, what and how of reasoning about your network with NetCon.
Also, it provides information on how to install, configure and use NetCon, and its related components such as the [[./8 API/NetCon API Introduction|TraceAPI]] or Flow Calculation export.

Check out [[./1 Introduction/Copyright and Usage|Copyright and Usage]].

Currently this site is in English only.
## Introduction
This section provides a short [[./1 Introduction/Introduction|Introduction]] to the agnostic NetCon model for connectivity (also known as topology) for networks.

## Latest news
We had a release adding NetCongestion tooling; besides [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Isolatable Sections|Isolatable Sections]] and [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Operated Sections|Operated Sections]] it is now possible to define [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Control or NetCongestion Sections|Control or NetCongestion Sections]].
For the electricity domain, these look remarkable similar to what you see in FISR and the (A)DMS.
When switches are operated, by means of [[./5 Configuration/Configuration - 9. Overlay and Near Real Time Networks/Overlay - 2. Overlay Networks for Data Quality|an overlay network]], the new network state is reflected in new control sections and a new [[./8 API/Results/Connection Or Path Results/Flow|flow]] for all affected connections.
## Version information

This section provides [[./2 Version And Release Information/2.2 Version Information#Releases|Version Information]], [[./2 Version And Release Information/2.2 Version Information#Release Notes|Release Notes]] and a [[./2 Version And Release Information/2.3 Roadmap|2.3 Roadmap]].

## Overview - Read me first

We recommend you take notice of the following introduction:
1. [[./3 Overview/Overview - 1. Use Cases|Overview - 1. Use Cases]]
2. [[./3 Overview/3.2 Data Flow Examples/Overview Examples - 1. Purpose and Examples|Overview Examples - 1. Purpose and Examples]]
3. [[./3 Overview/Overview - 3. Solution Architecture|Overview - 3. Solution Architecture]]
4. [[./3 Overview/Overview - 4. Sources of Connectivity|Overview - 4. Sources of Connectivity]]
5. Networks
	1. [[./3 Overview/Overview - 5. Commodity Networks|Overview - 5. Commodity Networks]]
	2. [[./3 Overview/3.5 Commodity Networks/Network Ontology|Network Ontology]]
	3. [[./3 Overview/3.5 Commodity Networks/Life Cycle Status|Life Cycle Status]]
	4. [[./3 Overview/3.5 Commodity Networks/Barrier or Operational State|Barrier or Operational State]]
	5. [[./3 Overview/3.5 Commodity Networks/Referential Information|Referential Information]]
6. Tracing and Querying
	1. [[./3 Overview/Tracing and Querying/Shortest path or Dijkstra algorithm|Shortest path or Dijkstra algorithm]]
	2. [[./3 Overview/Tracing and Querying/NetCon Path|NetCon Path]]
	3. [[./3 Overview/Tracing and Querying/Basic network tracing|Basic network tracing]]
7. [[./3 Overview/Network Sections|Network Sections]]

## Getting started

If you are new to NetCon, implement the basics by following the steps below

1. [[./4 Getting started/Download and Install NetCon|Download and Install NetCon]]
2. [[Download and Install NetCon Portal|Download and Install NetCon Portal]]
3. [[./4 Getting started/Connectivity Extraction Process|Connectivity Extraction Process]]
4. [[./4 Getting started/Viewing Connectivity|Viewing Connectivity]]
5. [[Querying Connectivity|Querying Connectivity]]
## Configuration

Please follow the these steps

1. Configuring the Asset Registration for Extraction
	1. [[./5 Configuration/Configuration - 1. Extraction/Base Connectivity Extraction|Base Connectivity Extraction]]
	2. [[./5 Configuration/Configuration - 1. Extraction/Atomic Model configuration|Atomic Model configuration]]
	3. [[./5 Configuration/Configuration - 1. Extraction/Section Model configuration|Section Model configuration]]
	4. [[./5 Configuration/Configuration - 1. Extraction/Templates for Connectivity Extraction|Templates for Connectivity Extraction]]
2. [[Clustering the Network into Sections|Clustering the Network into Sections]]
	1. [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Isolatable Sections|Isolatable Sections]]
	2. [[./5 Configuration/Configuration - 2. Warehouse/Operated Sections Model|Operated Sections Model]]
	3. [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Control or NetCongestion Sections|Control or NetCongestion Sections]]
	4. [[./5 Configuration/Configuration - 7. Sectioning and Tracing/Sections/Custom Sections|Custom Sections]]
3. [[Configuring NetCon TraceAPI|Configuring NetCon TraceAPI]]
4. [[./9 Expressions/NetCon Expressions|Using NetCon Expressions]]
	1. [[Flow Calculation Export|Expressions for Flow Calculation exports]]
5. [[./6 Use/Long running queries/Materializing Long Running traces|Materializing Long Running traces]]

## User documentation

### NetCon data in Desktop Application or Web browser

* [[Viewing|Viewing]]
	* Styling of maps
	* Enriched data
	* Database relations
	* Asset relations
	* Expression relations
	* TraceDerivatives
	* Derived fields with [[./9 Expressions/NetCon Expressions|Using NetCon Expressions]] 

### NetCon API

* [[./8 API/NetCon API Introduction|TraceAPI]]
* API Calls
	* [[./8 API/NetCon API Calls#Look up and search calls, that will return connections|Search API]]
	* [[./8 API/NetCon API Calls#Trace and network following calls, that will return paths|Trace API]]
	* [[./8 API/NetCon API Calls#Network manipulation calls, that will change the state and create data patches|Operate API]]
	* [[./8 API/NetCon API Calls#Meta information calls|Meta API]]
* [[./8 API/Common parameters in the API|Common parameters in the API]]
* [[./8 API/Default parameters in the API|Default parameters in the API]]

