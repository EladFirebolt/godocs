# Firebolt Release Notes - Version 4.9

## Behavior Changes

## New Features

<!-- Auto Generated Markdown for FIR-37875 - Owned by Benjamin Wagner -->
### Added the setting `enable_result_cache` to prevent serving cached query results during benchmarking
Added the setting `enable_result_cache`. This setting ensures that when benchmarking Firebolt, query results are not served from the cache.


<!-- Auto Generated Markdown for FIR-36620 - Owned by Pascal Schulze -->
### Introduced support for the bit functions `BIT_SHIFT_RIGHT` and `BIT_SHIFT_LEFT`
Added support for the bit functions `BIT_SHIFT_RIGHT` and `BIT_SHIFT_LEFT`.


<!-- Auto Generated Markdown for FIR-37680 - Owned by Max Reinsel -->
### Added new `async_token` column to `information_schema.engine_running_queries` for tracking asynchronous query status
The `information_schema.engine_running_queries` now has a new column: `async_token`. If the query is asynchronous, this column contains the token. You can use this token to check the query's status with `call fb_GetAsyncStatus(<token>)`.


<!-- Auto Generated Markdown for FIR-35668 - Owned by Kfir Yehuda -->
### Added support for the aggregate function `PERCENTILE_CONT`
Added support for the aggregate function `PERCENTILE_CONT`.


## Performance Improvements

<!-- Auto Generated Markdown for FIR-36835 - Owned by Michael Freitag -->
### Improved system stability and performance with faster query processing and corrected `to_date` function handling of invalid date formats
We made general improvements to the system's stability. The SQL engine now processes queries faster, enhancing overall performance. We've also fixed an issue where large datasets caused slow page loads in the UI. Furthermore, the `to_date` function now handles invalid date formats correctly, which reduces errors during data processing. Removed deprecated storage features to streamline operations.


<!-- Auto Generated Markdown for FIR-36922 - Owned by Ori Brostovski -->
### Improved expression comparison logic for better identification of identical expressions within queries
Enhanced the expression comparison logic to better identify identical expressions within a query. This improvement supports more queries and enhances the quality of query execution plans.


## Bug Fixes

<!-- Auto Generated Markdown for FIR-37576 - Owned by Anton Perkov -->
### You didn't provide a release note text to summarize. If you could supply the text, I'd be happy to help create a concise title for it!
There is no content provided in your release note to rewrite. Please supply the specific release note text that you would like me to edit.
