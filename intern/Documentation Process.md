---
title: DocumentationProcess
description: Steps to product and publish the documentation
permalink: 
aliases: 
draft: true
date: 2024-09-30
shared: false
tags: 
---
# Documentation Process

The documentation process should be:

* Trustable
* Have the documentation content registered in the git version control with the source code
* Be built on standard components
	* The file format that has been chosen is MarkDown
* Support:
	* Branding
	* Search
	* Translation
	* Reuse of shared content
	* Collaborating
* Scale

The process that has been currently drafted is depicted below:

```mermaid
graph LR
  subgraph Develop
    code([Source Code])
    doc([Documentation Content])
    sg[(Solution Git)]
  end
  doc-->|enveloppe|pgm
  subgraph Layout
    pgm([v4/Obisidian yyyy.MM.dd])-->|automerge|pg4([Content + Styling in v4])
    pg[(Publish Git)]
  end
  pg4-->|quartz auto deploy|web
  subgraph Host
    web([Documentation Web Site])
  end
```

## Remarks from team discussion

- We need to be able to collaborate or working together. For this we need to agree on how we avoid conflicts.
- Because the documentation is in mark down text format and in Git, conflicts are relatively easy to solve. 
