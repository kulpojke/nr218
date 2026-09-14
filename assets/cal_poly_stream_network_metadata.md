# Cal Poly Stream Network

Generated: 2026-09-14

Files:

- `cal_poly_stream_network.gpkg`
- `cal_poly_stream_network.geojson`

GeoPackage layers:

- `campus_boundary`: Cal Poly San Luis Obispo campus boundary from OpenStreetMap via Nominatim, OSM way `290467779`.
- `stream_network`: clipped USGS NHD Flowline Large Scale features where `ftype = 460` (`Stream/River`). This layer contains one intentional undershoot and one intentional overshoot for a topology editing exercise.

Coordinate systems:

- GeoPackage layers are in `EPSG:26910` (NAD83 / UTM zone 10N).
- GeoJSON export is in `EPSG:4326`.

Sources:

- Campus boundary: OpenStreetMap via Nominatim, https://nominatim.openstreetmap.org/
- Hydrography: USGS The National Map NHD MapServer, Flowline - Large Scale layer, https://hydro.nationalmap.gov/arcgis/rest/services/nhd/MapServer/6

QA summary:

- `stream_network`: 65 features, 0 invalid geometries, 18,169.7 m total clipped length after intentional topology edits.
- `stream_network` categories: 54 ephemeral segments and 11 intermittent segments.
