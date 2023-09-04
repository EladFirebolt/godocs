---
layout: default
title: JSON_EXTRACT
description: Reference material for JSON_EXTRACT function
grand_parent: SQL functions
parent: Semi-structured data functions
great_grand_parent: SQL reference
---

# JSON_EXTRACT

Takes an expression containing a JSON document, a JSON pointer expression, and an expected data type parameter. If the key specified using the JSON pointer expression exists, and its type conforms with the expected data type parameter, `JSON_EXTRACT` returns the value of the data type specified. Otherwise, returns NULL.

## Syntax
{: .no_toc}

```sql
JSON_EXTRACT(<json>, '<json_pointer_expression>', '<data_type>')
```
## Parameters 
{: .no_toc}

| Parameter                   | Description           | Supported input types                                                         |
| :--------------------------- | :-------------- | :------------------------------------------------------------------------------------------------- |
| `<json>`                    | The JSON document from which the value is to be extracted.        |    `TEXT`                                |
| `<json_pointer_expression>` | A JSON pointer to the location of the array in the JSON. For more information, see [JSON pointer expression syntax](./index.md#json-pointer-expression-syntax).                                 | `TEXT` |
| `<data_type>`           | The expected data type of the key indicated by `<json_pointer_expression>`, such as `TEXT` or `INTEGER`. For more information, see [supported type parameters](./index.md#supported-type-parameters). | Any data type | 

# Return Types 
* If key is provided, returns the value of the data type specified 
* If no key is provided, returns `NULL`

## Example
{: .no_toc}

For the JSON document indicated by `<json_common_example>` below, see [JSON common example](./index.md#json-common-example). The **Returns** result is based on this example.

```sql
SELECT
    JSON_EXTRACT(<json_common_example>, '/value/dyid', 'INTEGER')
```

**Returns**: `987`

```sql
SELECT
    JSON_EXTRACT(<json_common_example>, '/value/no_such_key', 'TEXT')
```

**Returns**: `NULL`

```sql
SELECT
    JSON_EXTRACT(<json_common_example>, '/value/uid', 'INTEGER')
```

**Returns**: `NULL` since the JSON type under that key is a string.

```sql
SELECT
    JSON_EXTRACT(<json_common_example>,'/value/keywords', 'ARRAY(TEXT)')
```

**Returns**: `["insanely","fast","analytics"]`
