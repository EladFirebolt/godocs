---
layout: default
title: ARRAY_MAX_GLOBAL
description: Reference material for ARRAY_MAX_GLOBAL function
parent: Aggregate array functions
grand_parent:  SQL functions
---

# ARRAY\_MAX\_GLOBAL

Returns the maximum element from all the array elements in each group.

<!-- For more information and the sample data used in the example below, please refer to [Aggregate Array Functions](./aggregate-array-functions.md). -->

## Syntax
{: .no_toc}

```sql
ARRAY_MAX_GLOBAL(<array>)
```
## Parameters 
{: .no_toc}
| Parameter | Description                                                              | Supported input types   |
| :--------- | :-----------------------------------------------------------------------|:------------------------|
| `<array>`  | The function returns the maximum element from the provided array column | c  |


<!-- Create an example that uses the customer dataset -->

## Return Types 
`ARRAY`

## Example
{: .no_toc}

The example below uses the following table `Scores`:

| nickname        | recent_scores |
| :---------------| :-------------|
| steven70        | \[1,3,4]      |
| sanderserin     | \[3,5,6,7]    |
| esimpson        | \[30,50,60]   |

<!-- | Parameter | Description                                                               |
| :--------- | :------------------------------------------------------------------------- |
| `<arr>`   | The function returns the maximum element from the provided array column | -->

In this example, the function calculates the maximum score earned by each player's recent scores. For example, the user `esimpson` received a maximum score of `60`, so this value is returned in the `max_score` column. 

```sql
SELECT
	nickname,
	ARRAY_MAX_GLOBAL(recent_scores) AS max_score
FROM
	Scores
GROUP BY
	nickname;
```

**Returns**:

| nickname         | max_score     |
| :----------------| :------------ |
| steven70         | 4             |
| sanderserin      | 7             |
| esimpson         | 60            |


