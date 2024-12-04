# Firebolt Release Notes - Version 4.11

## New Features

<!-- Auto Generated Markdown for FIR-36897 - Owned by Demian Hespe -->
### Introduced the `GEOGRAPHY` data type and functions for geospatial data handling
Added a new data type `GEOGRAPHY` and related functions for working with geospatial data.


<!-- Auto Generated Markdown for FIR-36663 - Owned by Kfir Yehuda -->
### Added the window function `FIRST_VALUE`
Added the window function `FIRST_VALUE`.


## Bug Fixes

<!-- Auto Generated Markdown for FIR-37817 - Owned by Demian Hespe -->
### Resolved a discrepancy in execution time reporting to include all query execution steps for the UI and JSON responses
Fixed an issue where the execution time reported in the UI and JSON responses did not include all steps of query execution.


<!-- Auto Generated Markdown for FIR-38446 - Owned by Vitaliy Liudvichenko -->
### Adjusted the behavior of the `GRANT` and `REVOKE` commands for situations where an object owner could not grant or revoke an ANY-privilege on that object
Corrected the behavior of the `GRANT` and `REVOKE` commands when an object owner could not grant or revoke an ANY-privilege on that object.
