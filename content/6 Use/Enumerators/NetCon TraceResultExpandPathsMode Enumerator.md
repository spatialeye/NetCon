---
title: NetCon TraceResultExpandPathsMode Enumerator
description: Encodes the way results are expanded in NetCon.
permalink:
aliases:
draft: false
date: 2025-04-19
tags:
---
# NetCon TraceResultExpandPathsMode Enumerator

Enumerator encoding the way results are expanded in NetCon.

| Id  | Name           | Description                                                                                                                                                                                                                    |
| --- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0   | unspecified    | It has not been specified how the query results will be returned. The default of the trace function will be used.                                                                                                              |
| 1   | connections    | Return the connections that match the results matching the 'yield' predicate only or the result of a reduced network. Default choice for 'get' queries, 'traceOutageImpact' and results that are reduced.                      |
| 2   | paths          | Expand the paths fully, thus any connection leading up to the last connection in the path - the one that matches the 'yield' predicate - is returned as well. Order undefined. Default for trace-path and trace-singular-path. |
| 3   | pathsCollapsed | Do not expand the paths, thus only the last connection in the path - the one that matches the 'yield' predicate - is returned. Order undefined. Default for trace-out and trace-meshed.                                         |
| 4   | pathsAscending | Expand the paths and sort them in ascending reading order (per path, duplicates omitted, slowest).                                                                                                                             |
| 5   | pathsShortened | Return the 'yield' paths only, and make previousId point to the paths that were 'yield' before.                                                                                                                                |
| 6   | network        | When reduce operations are performed on paths or connections, they become a network and the morphed connections are returned.                                                                                                  |
