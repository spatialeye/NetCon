---
title: Wildcards
description: 
permalink: 
aliases: 
draft: false
date: 2025-01-01
tags: 
---
# Wildcards

Some parameters can be supplied as an exact string value as well as a pattern supporting wildcards. The wildcard pattern works the same way as the Microsoft Windows supports file search: '?' must match one character, '\*' can match any character. 
Note that this is different from the SQL wildcards, so don't use their interpretation.
In addition, the comma (`,`) can be used to supply a list of values.

For example, this is denoted by the name of the parameter, e.g. [[./Parameters/AssetTableNamePattern|AssetTableNamePattern]] is the string or pattern that must match the `AssetTableName`. 

Patterns are matched by regular expression(s), in short regex(es). 
In a query recipe, these are written as `LIKE` expression.
For example, `label=*3456*` is translated by the compiler to `label LIKE *3456*`. 

When list type of wildcards are used, they are translated to to `IN` expressions.
For example, `label=34,56` is translated by the compiler to `label IN 34,56`. 

Typically, the search with the exact value may be faster than the wildcard matching, but it is tried to evaluate the wildcards to possible values before starting the search.
For example, if you use a wildcard pattern with [[./Parameters/AssetTableNamePattern|AssetTableNamePattern]], the pattern translates to a list of matching names.
For example, `assettablename=e_?v_cable` is translated by the compiler to `assettablename IN e_lv_cable,e_mv_cable` (assuming those are the only two matching tables). 

In addition, an overall search parameter [[PatternIsRegex|PatternIsRegex]] parameter can be provided which will change the type of pattern matching that is done.
If this set to `true` than regex wildcards can be used instead of the '?', '\*' en ',' described above.
NetCon uses the [dotNet regex syntax](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expressions).

> [!tip]
> Changing the [[./Default parameters in the API|Default parameters in the API]] overrides the default for all users for all [[./NetCon API Calls|NetCon API Calls]].

The default pattern is to use simple wildcard matching instead of regular expressions, and you can override that by providing the parameter [[PatternIsRegex|PatternIsRegex]] for each API call.

