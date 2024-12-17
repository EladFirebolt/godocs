---
layout: default
title: CONVERT_FROM
description: Reference material for CONVERT_FROM function
great_grand_parent: SQL reference
grand_parent: SQL functions
parent: Binary functions
published: true
---

# CONVERT_FROM

Converts a binary string from a specified encoding to the `TEXT` data type, using the database's encoding.

## Syntax

{: .no_toc}

```sql
CONVERT_FROM
(<bytes>, <src_encoding>)
```

## Parameters

{: .no_toc}

| Parameter        | Description                                                                                                                                                                          | Supported input types |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------|
| `<bytes>`        | A sequence of bytes representing text in `<src_encoding>`.                                                                                                                             | `BYTEA`               |
| `<src_encoding>` | The encoding from which the src `<bytes>` are derived, which must be constant. The supported source encoding aligns with those supported in the [ICU library](https://icu.unicode.org/). | `TEXT`                |  

## Return Type

`CONVERT_FROM` returns a value of type `TEXT`.

## Errors

If `<src_encoding>` is invalid, an error is thrown.
If `<bytes>` are malformed according to `<src_encoding>`, the behavior is undefined and may result in replacement characters or errors, depending on the encoding. For example, in `UTF-8` encoding, malformed bytes are replaced with the � character.

## Examples

{: .no_toc}

**Example**

The following code example uses `CONVERT_FROM` to convert the binary input `\x1212003100` of type `BYTEA` into a `TEXT` string using the `UTF-16` encoding. All results are displayed in `UTF-8` encoding:

```sql
SELECT CONVERT_FROM('\x1212003100'::BYTEA, 'utf16');
```

**Returns**

The result, `ሒ1�` consists of:
*  `ሒ`, the `UTF-16` representation of `1212`.
* `1`, the `UTF-16` representation of `0031`. 
* The replacement character `�`. Because `00` is a single byte, it does not form a valid `UTF-16` sequence.

**Example**

The following code example uses `CONVERT_FROM` to convert the binary input `\x31a031ffffffff` of type `BYTEA` into a `TEXT` string using the `windows-1252` encoding:

```sql
SELECT CONVERT_FROM('\x31a031ffffffff'::BYTEA, 'windows-1252');
```

**Returns**

The result, `1 1ÿÿÿÿ`, consists of:
* `1`, the windows-1252 representation of `31`.
* ` `, the windows-1252 representation of the ([non-breaking space character](https://en.wikipedia.org/wiki/Non-breaking_space)) a0.
* `ÿ`, the windows-1252 representation of `ff`.

**Example**

The following code example creates an external table with a `BYTEA` column that represents text data in a custom encoding that is specified during data loading:

```sql
CREATE EXTERNAL TABLE ext_table_bytea (
    col_bytea BYTEA
)
URL = 's3://my_bucket/my_folder/'
OBJECT_PATTERN = '*.parquet'
TYPE = PARQUET;
```

**Example**

The following code example creates an external table with `TEXT` columns in database encoding `UTF-8`:

```sql
CREATE EXTERNAL TABLE ext_table_text (
    col_text TEXT
)
URL = 's3://my_bucket/my_folder/'
OBJECT_PATTERN = '*.csv'
CREDENTIALS = (AWS_KEY_ID = 'your_key_id' AWS_SECRET_KEY = 'your_secret_key')
SKIP_HEADER = 1
ENCODING = 'UTF-8'
TYPE = CSV;
```

**Example**

The following code example converts the `BYTEA` column `col_bytea` into `TEXT` using the specified encoding `UTF-8`, and inserts it into `target_table`:

```sql
CREATE TABLE target_table (
    col_text TEXT
);
INSERT INTO target_table
SELECT CONVERT_FROM(col_bytea, 'UTF-8') AS col_text
FROM ext_table_bytea;
```

In the previous code example, you can replace the `UTF-8` encoding with another encoding supported by the [ICU library](https://icu.unicode.org/).