# Firebolt Release Notes - Version 4.9

## Behavior Changes

## New Features

<!-- Auto Generated Markdown for FIR-35668 - Owned by Kfir Yehuda -->
### Added support for the aggregate function `PERCENTILE_CONT`
Added support for the aggregate function `PERCENTILE_CONT`.


<!-- Auto Generated Markdown for FIR-36620 - Owned by Pascal Schulze -->
### Added support for the bit functions `BIT_SHIFT_RIGHT` and `BIT_SHIFT_LEFT`
Added support for the bit functions `BIT_SHIFT_RIGHT` and `BIT_SHIFT_LEFT`.


<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the `enable_result_cache` setting for controlling query result caching during benchmarking
We added the setting `enable_result_cache`. You can use this setting during benchmarking to ensure query results are not served from the cache.


<!-- Auto Generated Markdown for FIR-37680 - Owned by Max Reinsel -->
### Added new `async_token` column to the `information_schema.engine_running_queries` table to track asynchronous query status
The `information_schema.engine_running_queries` table now has a new column: `async_token`. If a query is asynchronous, this column contains the token. You can use this token to check the query's status through `call fb_GetAsyncStatus(<token>)`.


## Performance Improvements

<!-- Auto Generated Markdown for FIR-36922 - Owned by Ori Brostovski -->
### Improved expression comparison logic to better recognize identical expressions
The expression comparison logic was improved so more identical expressions in a query are recognized as identical. This update supports more queries and enhances plan quality.


## Bug Fixes

<!-- Auto Generated Markdown for FIR-36835 - Owned by Michael Freitag -->
### Resolved function recognition issues, optimized query performance, and updated documentation for clarity
We fixed an issue where the database did not recognize some PostgreSQL-compatible functions. These functions now work as expected, matching PostgreSQL behavior.

We improved the performance of query execution. Queries now run faster and more efficiently.

We updated the documentation to make it clearer and easier to understand.
