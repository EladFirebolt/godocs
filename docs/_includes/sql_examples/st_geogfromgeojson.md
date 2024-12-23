The following code example constructs a Point from a GeoJSON string describing a Point at specified longitude and latitude coordinates and converts it to WKT format:

``` sql
SELECT ST_ASTEXT(ST_GEOGFROMGEOJSON('{"type":"Point","coordinates":[-73.98551041593687,40.75793403395676]}')) AS result
```

**Returns**

| result (TEXT) |
| :--- |
| 'POINT(-73.98551041593687 40.75793403395676)' |