---
title: NetConQL - Specification
description:
permalink:
aliases:
draft: false
date: 2024-12-19
tags:
---
# NetConQL - Specification

This pages provides the query language specification.
In this language, one can optionally use braces '(' and ')' to clarify the scope. If no braces are provided, the interpretation will be quite normal, in that NOT is applied to the predicate it is in front of, then OR, and then AND.


	<Query> ::= <SelectQuery> [ UNION <SelectQuery> ]
	
	<SelectQuery> ::= SELECT <SelectClause> FROM <FromClause> [ WHERE <WhereClause>] [ LIMIT <MaxResults> ]
	
	<SelectClause> ::= '*' | <FieldClause> { ',', <FieldClause> }
	
	<FieldClause> ::= <FieldIdentifier>
	
	<FromClause> :: <NetworkTableClause> | <FunctionClause>

	<NetworkTableClause> :: <Network> '.' <TableClause>
	
	<TableClause> ::= Connection | IsolatableSection:Connection | ControlSection:Connection | OperatedSection:Connection | Path:Connection

	<FunctionClause> ::= TRACE [ '(' ] [ <TraceOptions> ]
				START <StartClause> 
				[ BLOCK <BlockClause> ] 
				[ YIELD <YieldClause> ] 
				[ STOP <StopClause> ] [ ')' ]

	<WhereClause> ::= <Predicate>

	<StartClause> :: = <Predicate>
	
	<BlockClause> :: = <Predicate>
	
	<YieldClause> :: = <Predicate>
	
	<StopClause> :: = <Predicate>
	
	<Predicate> ::= [ <ScopeClause> ] <Predicate>
				| [ '(' ] <Predicate>  [ ')' ]
				| <AndPredicate> | <OrPredicate> | <NotPredicate>
		        | <InPredicate> | <LikePredicate> | <EqualsPredicate> | <NotEqualsPredicate>
		        | <GreaterThanPredicate> | <GreaterPredicate> | <SmallerThanPredicate> | <SmallerPredicate>
	
	<ScopeClause> ::= ANY | ALL
	
	<AndPredicate> ::= <Predicate> AND <Predicate>

	<OrPredicate> ::= <Predicate> OR <Predicate>

	<NotPredicate> ::= NOT <Predicate>

	<InPredicate> ::= <FieldIdentifier> IN <ValueList>
	
	<LikePredicate> ::= <FieldIdentifier> LIKE <Pattern>

	<EqualsPredicate> ::= <FieldIdentifier> '=' <Value>
		
	<NotEqualsPredicate> ::= <FieldIdentifier> '!=' <Value>
		
	<GreaterThanPredicate> ::= <FieldIdentifier> '>=' <NumberValue>
		
	<GreaterPredicate> ::= <FieldIdentifier> '>' <NumberValue>
		
	<SmallerThanPredicate> ::= <FieldIdentifier> '<=' <NumberValue>
		
	<SmallerPredicate> ::= <FieldIdentifier> '<' <NumberValue>
		
	<FieldIdentifier> ::= [ <DrillDownClause> ] | FieldName
	
	<Pattern> ::= <WildCardPattern> | <RegExPattern>
	
	<WildCardPattern> ::= String with *, ?, ',' or ';'
	
	<<TraceOptions>> ::= [ SmartStart '=' Boolean ] [ MaxCost=<MaxCost> ] [ MaxStep=<MaxStep> ]

	<MaxResults> ::= Integer >= 0
	
	<MaxDepth> ::= Integer >= 0
	
	<MaxCost> ::= Double >= 0
	
	<Value> ::= <Numbervalue> | Date | String | Boolean
	
	<NumberValue> ::= Integer | Long | Double

## Optimizations performed by the NetConQL query parser:

The predicate

	BlockBarring=true

Is automatically translated into:

	Barrier>=Barring

The predicate

	SmartStart=true

In a query:

	SELECT * FROM TRACE (\[E\].Connection SmartStart=true START (AssetTableName=lv_cable AND AssetId=123) BLOCK Barrier>=Barring AND STOP (Commodity->Net=LV))

Is automatically translated into:

	SELECT * FROM TRACE (\[E\].Connection START (AssetTableName=lv_cable AND AssetId=123) BLOCK (Barrier>=Barring AND NOT (AssetTableName=lv_cable AND AssetId=123)) AND STOP (Commodity->Net=LV AND NOT (AssetTableName=lv_cable AND AssetId=123)))


## Usage of Flags:
See [[./NetConQL - Enumerator Flags|NetConQL - Enumerator Flags]].

