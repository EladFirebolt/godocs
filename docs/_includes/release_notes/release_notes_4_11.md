# Firebolt Release Notes - Version 4.11

## New Features

<!-- Auto Generated Markdown for FIR-36897 - Owned by Demian Hespe -->
### Introduced the `GEOGRAPHY` data type and functions for geospatial data handling (beta)
Added a new data type `GEOGRAPHY` and related functions for working with geospatial data.
Learn more about geospatial support in Firebolt in the [GEOGRAPHY data type documentation]({% link sql_reference/geography-data-type.md %}) and [geospatial functions documentation]({% link sql_reference/functions-reference/geospatial/index.md %}).
This is a beta release.

<!-- Auto Generated Markdown for FIR-36663 - Owned by Kfir Yehuda -->
### Added the window function `FIRST_VALUE`
Added a new window function [FIRST_VALUE]({% link sql_reference/functions-reference/window/first-value.md %}).


## Bug Fixes


<!-- Auto Generated Markdown for FIR-38446 - Owned by Vitaliy Liudvichenko -->
### Adjusted the behavior of the `GRANT` and `REVOKE` commands for situations where an object owner could not grant or revoke an ANY-privilege on that object
Corrected the behavior of the `GRANT` and `REVOKE` commands when an object owner could not grant or revoke an ANY-privilege on that object.
