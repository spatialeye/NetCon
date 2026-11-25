---
title: states
description: Returns state records of the execution of processes of the network engines.
permalink:
aliases:
draft: false
date: 2024-09-30
tags:
  - States
  - ApiMetaCall
  - ApiCall
---
# Engine Process States

The Search Call `states` retrieves the all state information of initialisation and other tasks performed by the network engine.

In this information, one can see if the initialisation has been completed, how long it took, the size of the networks, and possible failures.

> [!Note] At this moment the services are only available on the server after full initialisation, for compatibility when running Warehouse batches.
> For the desktop they are immediately available. This may change in the future. As long as that is the case, the `WaitTillInitialized` and `WaitMilliSeconds` parameters below are irrelevant.

## Parameters
| File                                                                                    | type    | mand  | description                                                                                                                                                                                         |
| --------------------------------------------------------------------------------------- | ------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Parameters/Progress State/WaitTillInitialized\|WaitTillInitialized]] | boolean | false | Optional parameter, the default value is 'false'. If 'true', the call will wait for the initialization to complete before returning.                                                                |
| [[../Parameters/Progress State/WaitMilliSeconds\|WaitMilliSeconds]]       | integer | false | Optional parameter, the default value is '-1'. This second parameter will specify the maximum of milliseconds that the call will wait before returning, if he WaitTillInitialized parameter is set. |


## Results
| File                                                                   | type     | unique | description                                                                                                                                                                                                                               |
| ---------------------------------------------------------------------- | -------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[../Results/Progress State/ProcessName\|ProcessName]]   | string   | false  | Name identifying the subprocess or task that has been started and for which a state is being logged and monitored.                                                                                                                        |
| [[../Results/Progress State/ProcessState\|ProcessState]] | string   | false  | State of the process, which is 'initialisation' when it is a start up process, 'executing' when it is a normal process, 'finished' when the task or the subprocesses have completed, and 'failed' if the process has raised an exception. |
| [[../Results/Progress State/StartTime\|StartTime]]       | datetime | false  | The moment that the process or computation was started. Universal date + time.                                                                                                                                                            |
| [[../Results/Progress State/Duration\|Duration]]         | timespan | false  | Specifices the time it took to perform the process or computation. Time span in seconds. Only available when completed.                                                                                                                   |
| [[../Results/Progress State/Message\|Message]]           | string   | false  | Last message provided as logging information for this result or state. If a query has been performed well, this is the NetConQL description of the optimized query.                                                                       |
| [[../Results/Progress State/PeakMemory\|PeakMemory]]     | long     | false  | The *total* memory that the server is consuming measured during the execution of this process. This is *not* the memory consumed by the process.                                                                                          |




Example query to retrieve the state information: 

    https://server.domain.local/api/v2/netcon/v1/states

Example query to retrieve the state information and wait maximum 60 seconds for initialisation:

    https://server.domain.local/api/v2/netcon/v1/states?WaitTillInitialized=true&WaitMilliSeconds=60000
