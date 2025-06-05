---
title: Download and Install NetCon
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-30
tags:
  - GettingStarted
  - ToDo
---
[[../index#Getting started|previous]] [[./Connectivity Extraction Process|next]]
# Download and Install NetCon

NetCon version 2.0 is compatible with Spatial Workshop and XY Server of version 2024.1.  
Versions still supported are .
Versions no longer supported are 2022.3, 2022.4, 2023.1, 2023.2.
### Download

You may download the Spatial Eye software from the support website (see links at the bottom of this page).
The NetCon software can be downloaded from [SharePoint](https://spatialeyecloud.sharepoint.com/:f:/s/SpatialEyeTransfer/ElHpBNHtxlhCiRIktCS_S1gBME9nh09Gix8f3FpkT_q4vg) if you have been granted access.

Install Spatial Workshop Ultimate and XY Server with Warehouse on your application server. The Spatial Eye service team has described best practices that you could use for the installation.

For example:

- It is recommended to work with an `environment_var.bat` file to facilitate DTAP-deployment (development -> test/ quality assurance -> user-acceptance -> production environment);
- Using a project store named after the environment to avoid mistakes;
- Using source control or data warehouse `seProject` naming conventions enables going back and seeing what changed, when. Maintain a log of changes in the accompanying `rtf` information file that will open on startup. In particular, after an ETL spatial warehouse batch has run, the version number should be incremented and the `seProject` file should not be changed anymore;

### Memory requirement

The memory required to run NetCon for generating sections or to run the in-memory NetConTrace API is dependent on the size of your network #ToDo
### Installation of the DLLs

Note that Spatial Eye has developed the add-ins mechanism in order to support faster releases for specific solutions; this is also the case for NetCon which has more releases than the underlying base products.

> [!Tip] Unblock download files
> After download, first `unblock` the downloaded files (or entire zip-file) in Windows Explorer | Properties (Alt-Enter). DLLs that are blocked by the operating system cannot be used by the software and will give weird exceptions.

The installation is simply done by copying the DLLs into the add-ins directory. See also the [[../2 Version And Release Information/Previous releases/NetCon 1.0 DLLs|previous version installation]].

|                            | Desktop                                                                                     | Server                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **DLLs**                   | NetworkTraceBase.dll                                                                        | NetworkTraceBase.dll<br>NetworkTraceServices.dll<br>SpatialWarehouseTimestampTask.dll      |
| **Prerequisites**          | ZeroFormatter.dll<br>ZeroFormatter.Interfaces.dll<br>Microsoft.Bcl.HashCode.dll             | ZeroFormatter.dll<br>ZeroFormatter.Interfaces.dll<br>Microsoft.Bcl.HashCode.dll            |
| **Installation directory** | C:\\Program Files\\Spatial Eye\\Spatial Workshop\\AddIns | C:\\Program Files\\Spatial Eye\\XY Server\\AddIns |

### Installation of the styles

For NetCon 2.0 additional themed styles are provided as a style library document. Please install this as well.

|                            | Desktop                                                                                             | Server                                                                                             |
| -------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Style library**          | seExtended.seStyles                                                                                 | seExtended.seStyles                                                                                |
| **Installation directory** | C:\\Program Files\\Spatial Eye\\Spatial Workshop\\StyleLibraries | C:\\Program Files\\Spatial Eye\\XY Server\\StyleLibraries |

### Additional configuration for large networks

If your network is large (> 48.8 million network connections), besides having plenty internal memory in your system you will need to configure the .Net Framework to allow large data structures. In the `*.config` files (both for XY Server and Spatial Workshop Ultimate and GSA or XY Server), enable "AllowVeryLargeObjects". Make a backup of the *.config file, open the *.config files with an XML-editor (or plain text editor), locate the configuration/runtime node, and enable gcAllowVeryLargeObjects (note, other configuration is in place, only add the ```<gcAllowVeryLargeObjects>``` node):

```xml
<configuration>
  <runtime>
    <!-- Allow for large networks ( > ~48 million connections) -->
    <gcAllowVeryLargeObjects enabled="true" />
  </runtime>
</configuration>
```

This allows the .Net runtime (64-bit) to create larger data blocks, exceeding the limits of some 32-bit runtime settings which it uses by default.
Without this setting you may encounter the following error:

> [!Error] OutOfMemoryException
> System.OutOfMemoryException: Array dimensions exceeded supported range.

See also https://learn.microsoft.com/en-us/dotnet/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element
