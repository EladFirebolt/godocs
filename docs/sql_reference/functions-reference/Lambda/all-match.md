---
layout: default
title: ALL_MATCH
description: Reference material for ALL_MATCH function
grand_parent: SQL functions
parent: Lambda functions
great_grand_parent: SQL reference
---

# ALL_MATCH

Returns `1` (true) when the Boolean expression `<condition>` performed on all elements of an array evaluate to true. Returns `0` (false) when any one comparison evaluates to false.

## Syntax
{: .no_toc}

```sql
ALL_MATCH(<expression> -> <condition>, <array>)
```
## Parameters
{: .no_toc}

| Parameter      | Description                                   | Supported input types | 
| :------------- |:--------------------------------------------- | :-----------| 
| `<expression>`  | A Lambda array variable that contains elements of the array specified using `<array>`. For more information, see [Manipulating arrays with Lambda functions](../../../Guides/working-with-semi-structured-data/working-with-arrays.md#manipulating-arrays-with-lambda-functions). |
| `<condition>` | A Boolean expression that evaluates each array value using a comparison operator. For available operators, see [Comparison operators](../../operators.md#comparison). |
| `<array>` | An expression that evaluates to an `ARRAY` data type. |

## Return Types
* Returns `1` if the condition is met
* Returns `0` if the condition returns false

## Examples
{: .no_toc}

Return `1` (true) if all elements in the array are greater than 0.

```sql
SELECT
	ALL_MATCH(x -> x > 0, [ 1, 2, 3, 9 ]) AS current_levels;
```

**Returns**: 

| current_levels |
|:-------------| 
| 1                  |



Return `1` (true) if `esimpson` does not appear in the `current_players` array. 

```sql
SELECT
	ALL_MATCH(x -> x <> 'esimpson', [ 'kennethpark', 'sabrina21', 'steven70']) AS current_players;
```

**Returns**: 

| current_players |
|:-------------| 
| 0                  |