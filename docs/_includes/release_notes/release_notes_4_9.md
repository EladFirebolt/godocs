# Firebolt Release Notes - Version 4.9

There's not much that we are ready to show this time, but behind the scenes, we are hard at work to bring you tons of new features and performance improvements in upcoming releases. For now, this is what's coming your way in version 4.9.

## New Features

<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the `enable_result_cache` setting for controlling query result caching during benchmarking
We added the setting `enable_result_cache`. You can use this setting during benchmarking to ensure query results are not served from the cache.
### Added `LAG`/`LEAD` support for negative offsets.
The 2nd `LAG`/`LEAD` parameter can now accept negative numbers. Given a negative number, a `LAG` will become a `LEAD` and vice versa. For example `LAG(x,-5,3)` is the same as `LEAD(x,5,3)`.
