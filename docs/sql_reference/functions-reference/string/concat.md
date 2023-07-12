---
layout: default
title: CONCAT
description: Reference material for CONCAT function
grand_parent: SQL functions
parent: String functions
---

# CONCAT

Concatenates the strings listed in the arguments without a separator.

## Syntax
{: .no_toc}

```sql
CONCAT( <expression>[, ...n] );
```
**&mdash;OR&mdash;**

```sql
<expression> || <expression2> || [ ...n]
```

| Parameter | Description                         |Supported input types |
| :--------- | :----------------------------------- | :---------------------|
| `<expression>[, ...n]` | The string(s) to be concatenated. | `TEXT` |

NULL inputs to the `CONCAT` function are treated as empty strings and ignored. When all inputs are NULL, the result will be an empty string.

When using `||`, any NULL input results in a NULL output.

## Return Types
This function returns the `TEXT` type. 

## Example
{: .no_toc}

<!-- ```sql
SELECT
	CONCAT('Hello ', 'World!');
```

**Returns**: `Hello World!` -->
The following example combines the users' `nicknames` and `emails` from the players table, with the limit of `5`: 

```sql
SELECT
	CONCAT(nickname, ': ', email) as user_info
FROM players
LIMIT 5;
```

**Returns**:
| user_info                              |
| :--------------------------------------|
| steven70: daniellegraham@example.net   | 
| burchdenise: keith84@example.org       | 
| stephanie86: zjenkins@example.org      |
| sabrina21: brianna65@example.org       |
| kennethpark: williamsdonna@example.com |



