---
title: Enrichment or Specification Queries
description:
permalink:
aliases:
draft: false
date: 2024-10-01
tags:
---
# Enrichment or Specification Queries

It is good practice to make the information stored in the asset_hierarchy field of the connection readily accessible, since each connection can contain 0, 1 or more items in the asset hierarchy field in the format <table_name1>.<fieldname1>=<id1>[,<table_name2>.<fieldname2>=<id2>]. In the future, this can be altered into an indexed JSON string, however, for the moment, it is a normal string. In the UserTools table, direct, indexed, relation can be created between _table_name_ with _id1_ and the _connection id_, the _section id_ and _supersection id_.

Examples are work in progress.

