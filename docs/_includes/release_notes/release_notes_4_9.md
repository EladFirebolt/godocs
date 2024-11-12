# Firebolt Release Notes - Version 4.9

There's not much that we are ready to show this time, but behind the scenes, we are hard at work to bring you tons of new features and performance improvements in upcoming releases. For now, this is what's coming your way in version 4.9.

## New Features

<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the `enable_result_cache` setting for controlling query result caching during benchmarking
You can set `enable_result_cache` to `FALSE` to disable the use of Firebolt's result cache, which is set to `TRUE` by default. Disabling result cashing can be useful for benchmarking query performance. When `enable_result_cache` is disabled, resubmitting the same query will recompute the results rather than retrieving them from cache. For more information, see [Result Cache](../../Reference/system-settings#result-cache).

### Added `LAG` and `LEAD` support for negative offsets.
The second parameter in both [LAG](../../sql_reference/functions-reference/window/lag) and [LEAD](../../sql_reference/functions-reference/window/lead) can now accept negative numbers. Given a negative number, a `LAG` will become a `LEAD` and vice versa. For example, `LAG(x,-5,3)` is the same as `LEAD(x,5,3)`.

## Performance Improvements

<!-- Auto Generated Markdown for FIR-36922 - Owned by Ori Brostovski -->
### Faster string searches for case-insensitive simple regular expressions in `REGEXP_LIKE`
Simple regular expressions in [REGEXP_LIKE](../../sql_reference/functions-reference/string/regexp-like) with case-insensitive matching, using the `i` flag, now use the same optimized string search implementation as [ILIKE](../../sql_reference/functions-reference/string/ilike), achieving up to three times faster runtimes in observed cases.