---
title: NetCon API
description: 
permalink: NetConApi
aliases: 
draft: false
date: 2024-09-30
tags:
  - Wildcard
---
# NetCon API Introduction

The NetCon API provides RESTful to interact with NetCon data via the tracing engine. These services will use the engine in exactly the same way as [[NetCon|NetCon]].

The [[./NetCon API Calls|NetCon API Calls]] can be split into four categories:

- Meta information, about the API and the server
- Look up and search, that will return connections,
- Trace and network following, that will return paths,
- Network manipulation, that will change the state and create data patches.  

To see and play with the services, the OpenAPI / SwaggerUI provided by the server can be used.

    https://servername.domain.local/swagger-ui/#/

    https://servername.domain.local/openapi

The NetCon API browser user interface should look like this:

![[../Zimages/netcon_trace_api_in_browser.png|NetCon_Trace_API in browser]]

  
By clicking on one of the GET boxes above, you'll get the interaction screen:

![[../Zimages/netcon_trace_api_in_browser_trace_isolatable_section.png|NetCon_Trace_Isolatable Section API in browser]]
