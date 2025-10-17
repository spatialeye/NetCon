---
title: Download and Install NetCon Portal
description:
permalink:
aliases:
draft: false
date: 2025-09-30
tags:
  - GettingStarted
---
[[./Download and Install NetCon|previous]] [[./Connectivity Extraction Process|next]]
# Download and Install NetCon Portal

### Prerequisite
To use NetCon Portal you must [[./Download and Install NetCon|previous]] first. 
### Download
You may download the Spatial Eye software from the support website (see links at the bottom of this page).
The NetCon Portal software can be downloaded from [SharePoint](https://spatialeyecloud.sharepoint.com/:f:/s/SpatialEyeTransfer/ElHpBNHtxlhCiRIktCS_S1gBME9nh09Gix8f3FpkT_q4vg) if you have been granted access.
### Installation of the DLLs
Note that Spatial Eye has developed the add-ins mechanism in order to support faster releases for specific solutions; this is also the case for NetCon which has more releases than the underlying base products.

> [!Tip] Unblock download files
> After download, first `unblock` the downloaded files (or entire zip-file) in Windows Explorer | Properties (Alt-Enter). DLLs that are blocked by the operating system cannot be used by the software.

The installation is simply done by copying the DLLs into the add-ins directory. See also the [[../2 Version And Release Information/Previous releases/NetCon 1.0 DLLs|previous version installation]].

|                            | Desktop                                                                                                 | Server                                                                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **DLLs**                   | NetConPortal.dll                                                                                        | NetConPortal.dll<br>                                                                                                                                                     |
| **Prerequisites**          | NetworkTraceBase.dll<br>ZeroFormatter.dll<br>ZeroFormatter.Interfaces.dll<br>Microsoft.Bcl.HashCode.dll | NetworkTraceBase.dll<br>NetworkTraceServices.dll<br>SpatialWarehouseTimestampTask.dll<br>ZeroFormatter.dll<br>ZeroFormatter.Interfaces.dll<br>Microsoft.Bcl.HashCode.dll |
| **Installation directory** | C:\\Program Files\\Spatial Eye\\Spatial Workshop\\AddIns             | C:\\Program Files\\Spatial Eye\\XY Server\\AddIns                                                                               |
