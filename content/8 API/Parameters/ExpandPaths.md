---
title: ExpandPaths
description: Enum that determines what to do with the results. 'connections' = only return connections matching 'yield' predicate or the result of a reduced network. 'paths' = return matching connections as well those leading up those as paths. (Default for trace-path and trace-singular-path; [[../Results/Connection Or Path Results/PreviousId|PreviousId]] will point to the previous connection, no order guaranteed). 'pathsCollapsed' = Do not expand the paths. (Default for trace-out and trace-mazed and trace-neighbor.) 'pathsAscending' = expand the paths and sort them in ascending reading order (per paths, duplicates omitted, slowest). 'pathsShortened' = return the 'yield' paths only, and make [[../Results/Connection Or Path Results/PreviousId|PreviousId]] point to the paths that were 'yielded' before.
Type: string
Order: 999
Mandatory: false
permalink: 
aliases: 
draft: false
date: 2025-02-18
tags:
  - ApiParameter
  - ExpandPaths
  - NetCon2
---
# ExpandPaths

Type of: _string_
Unique: __

Enum that determines what to do with the results. 'connections' = only return connections matching 'yield' predicate or the result of a reduced network. 'paths' = return matching connections as well those leading up those as paths. (Default for trace-path and trace-singular-path; [[PreviousId|PreviousId]] will point to the previous connection, no order guaranteed). 'pathsCollapsed' = Do not expand the paths. (Default for trace-out and trace-mazed and trace-neighbor.) 'pathsAscending' = expand the paths and sort them in ascending reading order (per paths, duplicates omitted, slowest). 'pathsShortened' = return the 'yield' paths only, and make [[PreviousId|PreviousId]] point to the paths that were 'yielded' before.

* **connections**: Return the connections that match the results matching the 'yield' predicate only or the result of a reduced network. Default choice for non-traces queries or those that are reduced such as [[../Calls/GetConnection|GetConnection]], [[../Calls/GetIsolatableSection|GetIsolatableSection]], [[../Calls/GetOperatedSection|GetOperatedSection]], [[../Calls/GetNeighbor|GetNeighbor]], [[../Calls/GetNeighborUpstream|GetNeighborUpstream]], [[../Calls/GetNeighborDownstream|GetNeighborDownstream]], [[../Calls/TraceOutageImpact|TraceOutageImpact]].
* **paths**: Expand the paths fully, thus any connection leading up to the last connection in the path - the one that matches the 'yield' predicate - is returned as well. Order undefined. Default for [[../Calls/TracePath|TracePath]], [[TraceSingularPath|TraceSingularPath]] and [[TraceOutageRootCause|TraceOutageRootCause]].
* **pathsCollapsed**: Do not expand the paths, thus only the last connection in the path - the one that matches the 'yield' predicate - is returned. Order undefined. Default for [[../Calls/TraceOut|TraceOut]] and [[../Calls/TraceMazed|TraceMazed]] and [[../Calls/TraceNeighbor|TraceNeighbor]]. In this case [[../Results/Connection Or Path Results/PreviousId|PreviousId]] may be dangling since the previous path may not be included.
* **pathsAscending**: Expand the paths and sort them in ascending reading order (per path, duplicates omitted, slowest).
* **pathsShortened**: Similar to `pathsCollapsed`, thus only the last connection in the path - the one that matches the 'yield' predicate - is returned. The attribute [[../Results/Connection Or Path Results/PreviousId|PreviousId]] point to the paths that were yield before.

Previous versions:
* Note that in the first version of NetCon this parameter used to be a boolean.
* Note that in the pre-release version of NetCon this parameter had different default.