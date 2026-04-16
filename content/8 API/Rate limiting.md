---
title: Rate limiting
description: Hardening of the API using a Rate Limiter that queues jobs. Description and configuration options
permalink:
aliases:
draft: false
date: 2026-02-27
tags:
  - RateLimiting
  - Hardening
  - Job
  - GeometryRetentionMinutes
  - GeometryRetentionTime
---
#  Introduction

The NetCon API is hardened using a rate limiting mechanism. There is a maximum number of concurrent requests that are handled. Some core characteristics:
* All requests (synchronous and asynchronous) are queued as jobs, and a job dispatcher makes sure that they are handled concurrently without overloading the server.
* Synchronous jobs are placed in a high-priority queue, asynchronous jobs are placed in a low-priority queue.
* The dispatcher handles high-priority jobs first but will process some asynchronous jobs to prevent “denial of service” for asynchronous jobs (in case the server is overloaded with synchronous jobs). There is a maximum number of synchronous jobs that are processed before an asynchronous job is processed.
* There is a maximum time the server will wait for a synchronous job to be handled (e.g. 20 seconds), a maximum time an asynchronous job will live (e.g. 10 minutes), etc.
* Nearly all parameters are configurable to get an optimum performance, balancing the server capacities and the workload.
# Configurable parameters

| Parameter                      | Type | Default value | Description                                                                                                                                                                                                                          |
| ------------------------------ | ---- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Worker Count                   | int  | 8             | Global maximum number of concurrently executing jobs.                                                                                                                                                                                |
| Max Concurrent Sync Executions | int  | 4             | Cap for concurrently executing synchronous jobs.                                                                                                                                                                                     |
| Max Queued Sync Jobs           | int  | 20            | Maximum number of queued synchronous jobs                                                                                                                                                                                            |
| Max Queued Async Jobs          | int  | 50            | Maximum number of queued asynchronous jobs.                                                                                                                                                                                          |
| Max Total Queued Jobs          | int  | 50            | Maximum number of total queued jobs (sync + async).                                                                                                                                                                                  |
| Sync Max Total Wait            | int  | 25            | Maximum total time (in seconds) a synchronous request is allowed to spend waiting: this includes queue wait + execution time (best-effort).                                                                                          |
| Sync Burst Before Async        | int  | 5             | Number of consecutive synchronous jobs that may run before the scheduler attempts to run one asynchronous job (if any are queued). This avoids complete starvation of asynchronous work while still preferring synchronous requests. |
| Overload Http Status Code      | int  | 429           | Gets or sets the HTTP status code used for overload responses. Typical values are 429 (Too Many Requests) or 503 (Service Unavailable).                                                                                              |
| Retry After Seconds            | int  | 15            | Gets or sets the value (in seconds) to include in the Retry-After header on overload/timeout responses.                                                                                                                              |
| Async Job Ttl                  | int  | 60            | The TTL (in minutes) for asynchronous job status records stored in the job store.                                                                                                                                                    |
| Reject Async When Queue Full   | bool | true          | Whether asynchronous requests should be rejected when the async queue is full.                                                                                                                                                       |
![[../Zimages/RateLimiterConfiguration.png|RateLimiterConfiguration.png]]