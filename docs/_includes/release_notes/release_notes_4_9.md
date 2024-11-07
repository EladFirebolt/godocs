# Firebolt Release Notes - Version 4.9

There's not much that we are ready to show this time, but behind the scenes, we are hard at work to bring you tons of new features and performance improvements in upcoming releases. For now, this is what's coming your way in version 4.9.

## New Features

<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the `enable_result_cache` setting for controlling query result caching during benchmarking
You can set `enable_result_cache` to `FALSE` to disable the use of Firebolt's result cache, which is set to `TRUE` by default. Disabling result cashing can be useful for benchmarking query performance. When `enable_result_cache` is disabled, resubmitting the same query will recompute the results rather than retrieving them from cache. For more information, see [Result Cache](../../Reference/system-settings#result-cache).

### Added `LAG` and `LEAD` support for negative offsets.
[LAG](../../sql_reference/functions-reference/window/lag) and [LEAD](../../sql_reference/functions-reference/window/lead) window functions now support negative offsets as the second argument.
