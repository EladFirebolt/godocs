# Firebolt Release Notes - Version 4.9

## Behavior Changes

## New Features

<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the `enable_result_cache` setting for controlling query result caching during benchmarking
We added the setting `enable_result_cache`. You can use this setting during benchmarking to ensure query results are not served from the cache.


<!-- Auto Generated Markdown for FIR-37680 - Owned by Max Reinsel -->
### Added new `async_token` column to the `information_schema.engine_running_queries` table to track asynchronous query status
The `information_schema.engine_running_queries` table now has a new column: `async_token`. If a query is asynchronous, this column contains the token. You can use this token to check the query's status through `call fb_GetAsyncStatus(<token>)`.


## Performance Improvements
