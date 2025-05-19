---
title: Welcome to NetCon
description: Starting page for the NetCon documentatation
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

Welcome to the online Spatial Eye NetCon© Help site. 
Here you will find information about the why, what and how of reasoning about your network with NetCon.
Also, it provides information on how to install, configure and use NetCon, and its related components such as the [[./8 API/NetCon API Introduction|TraceAPI]] or Flow Calculation export.

Check out [[./1 Introduction/Copyright and Usage|Copyright and Usage]].

Currently this site is in English only.
## Introduction
This section provides a short [[./1 Introduction/Introduction|Introduction]] to the agnostic NetCon model for connectivity (also known as topology) for networks.

## Latest news
Around September 2024 there will be a pre-release to test out some new API's and the Net Congestion tooling.

## Version information

This section provides [[./2 Version And Release Information/Version Information#Releases|Version Information]], [[./2 Version And Release Information/Version Information#Release Notes|Release Notes]] and a [[./2 Version And Release Information/Roadmap|Roadmap]].

## Overview - Read me first

We recommend you take notice of the following introduction:
1. [[./3 Overview/Use Cases|Use Cases]]
2. [[./3 Overview/Purpose and Examples|Purpose and Examples]]
3. [[./3 Overview/Solution Architecture|Solution Architecture]]
4. [[./3 Overview/Sources of Connectivity|Sources of Connectivity]]
5. [[./3 Overview/Commodity Networks|Commodity Networks]]
6. [[./3 Overview/Network Ontology|Network Ontology]]
7. Tracing and Querying
	1. [[./3 Overview/Tracing and Querying/Shortest path or Dijkstra algorithm|Shortest path or Dijkstra algorithm]]
	2. [[./3 Overview/Tracing and Querying/NetCon Path|NetCon Path]]
	3. [[./3 Overview/Tracing and Querying/Basic network tracing|Basic network tracing]]
8. [[./3 Overview/Life Cycle Status|Life Cycle Status]]
9. [[./3 Overview/Barrier or Operational State|Barrier or Operational State]]
10. [[./3 Overview/Referential Information|Referential Information]]
11. [[./3 Overview/Network Sections|Network Sections]]

## Getting started

If you are new to NetCon, implement the basics by following the steps below

1. [[./4 Getting started/Download and Install NetCon|Download and Install NetCon]]
2. [[./4 Getting started/Connectivity Extraction Process|Connectivity Extraction Process]]
3. [[./4 Getting started/Viewing Connectivity|Viewing Connectivity]]
4. [[Querying Connectivity|Querying Connectivity]]
## Configuration

Please follow the these steps

1. Configuring the Asset Registration for Extraction
	1. [[./5 Configuration/Extraction/Base Connectivity Extraction|Base Connectivity Extraction]]
	2. [[./5 Configuration/Extraction/Atomic Model configuration|Atomic Model configuration]]
	3. [[./5 Configuration/Extraction/Section Model configuration|Section Model configuration]]
	4. [[./5 Configuration/Extraction/Templates for Connectivity Extraction|Templates for Connectivity Extraction]]
2. [[Clustering the Network into Sections|Clustering the Network into Sections]]
	1. [[./5 Configuration/Sectioning and Tracing/Sections/Isolatable Sections|Isolatable Sections]]
	2. [[./5 Configuration/Warehouse/Operated Sections Model|Operated Sections Model]]
	3. [[./5 Configuration/Sectioning and Tracing/Sections/Control or NetCongestion Section|Control or NetCongestion Section]]
	4. [[./5 Configuration/Sectioning and Tracing/Sections/Custom Sections|Custom Sections]]
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
