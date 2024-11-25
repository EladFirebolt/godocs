---
name: New function template
about: Use this template to add new SQL functions
title: "[NEW FUNCTION]"
labels: ''
assignees: nanimal-fb, arushi-firebolt

---

---
layout: default
title: <FUNCTION>
description: Reference material for <FUNCTION> function
parent: SQL functions
---

# <FUNCTION>
Define what the function does without assuming prior knowledge, and without using the function to define itself. For example, if you want to define the Manhattan distance, do not define the function by saying that it calculates the Manhattan distance. State how the Manhattan distance is calculated using the simplest terms possible, and write the definition in terms that a 10th grader can follow. Do not use jargon which doesn't translate well, or parenthesis unless it's to define an abbreviation, or latinisms such as i.e. or e.g., or etc. Do not use personal pronouns including "we". Avoid passive voice if possible. If you add a link to our internal documentation, use this format as an example: [BIT_OR example](% link {sql_reference/functions-reference/aggregation/bit_or.html %}#examples).

## Syntax
{: .no_toc}

```sql
FUNCTION(<exp1>, <exp2>)
```

### Aliases (Optional)

```sql
FUNCTION_ALIAS(<exp1>, <exp2>)
```

## Parameters

{: .no_toc}

| Parameter | Description |
| :-------- | :---------- |
| `<parameter1>` | <The description of the parameter as a full sentence containing a noun and a verb that ends with a period.> |

## Return Type(s)

The `FUNCTION` function returns a result of type `DATATYPE`.

## Example(s) (Optional if there are several examples)

**Example**

The following code example (insert a one-sentence complete description of what the code does. You can use AI to help you generate this.) Provide a code example that is simple to follow. For example, instead of calculating the median over a range of 10,000 numbers, calculate it over 4 numbers. Use several examples to illustrate end cases.

```sql
SELECT
	 AS ;
```

**Returns** (make sure there is a carriage return after this line so that the text renders correctly)

``

(Optional) The previous code example returns (insert what and why it returns what it does, if necessary for understanding.) 