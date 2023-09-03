---
layout: default
title: ROW_NUMBER OVER
description: Reference material for ROW_NUMBER function
grand_parent: SQL functions
parent: Window functions
great_grand_parent: SQL reference
---

# ROW\_NUMBER

Returns a unique row number for each row within the requested window.

For more information on usage, please refer to [Window Functions](./window-functions.md).

## Syntax
{: .no_toc}

```sql
ROW_NUMBER() OVER ([PARTITION BY <partition_by>] ORDER BY <order_by> [ASC|DESC] )
```

## Parameters 
{: .no_toc}

| Parameter | Description                                      |Supported input types | 
| :--------- | :------------------------------------------------ | :------------| 
| `<partition_by>`   | The expression used for the `PARTITION BY` clause.                                                                | Any |
| `<order_by>`   | The expression used in the `ORDER BY` clause. This parameter determines what value will be used for `ROW_NUMBER`. | Any |

## Return Type
`INTEGER`

## Example
{: .no_toc}

In this example below, students in each grade level are assigned a unique number.

```sql
SELECT
	first_name,
	grade_level,
	ROW_NUMBER() OVER (PARTITION BY grade_level ORDER BY grade_level ASC ) AS student_no
FROM
	class_test;
```

**Returns**:

```
+------------+-------------+------------+
| first_name | grade_level | student_no |
+------------+-------------+------------+
| Frank      |           9 |          1 |
| Humphrey   |           9 |          2 |
| Iris       |           9 |          3 |
| Sammy      |           9 |          4 |
| Peter      |           9 |          5 |
| Jojo       |           9 |          6 |
| Brunhilda  |          12 |          1 |
| Franco     |          12 |          2 |
| Thomas     |          12 |          3 |
| Gary       |          12 |          4 |
| Charles    |          12 |          5 |
| Jesse      |          12 |          6 |
| Roseanna   |          11 |          1 |
| Carol      |          11 |          2 |
| Wanda      |          11 |          3 |
| Shangxiu   |          11 |          4 |
| Larry      |          11 |          5 |
| Otis       |          11 |          6 |
| Deborah    |          10 |          1 |
| Yolinda    |          10 |          2 |
| Albert     |          10 |          3 |
| Mary       |          10 |          4 |
| Shawn      |          10 |          5 |
+------------+-------------+------------+
```
