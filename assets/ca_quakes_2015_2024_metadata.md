# California Earthquakes 2015–2024

Generated: 2026-11-12

Files:

- `ca_quakes_2015_2024.zip`, containing a folder `ca_quakes/` with one CSV per year: `ca_quakes_2015.csv` … `ca_quakes_2024.csv`.

Contents:

- All events of magnitude 2.5 or greater, 1 January to 31 December of each year (UTC).
- Search box: latitude 32.5 to 42, longitude −124.5 to −114. The box is a rectangle, so it also includes parts of Nevada, Oregon, Mexico and the Pacific offshore.
- Useful columns: `time`, `latitude`, `longitude`, `depth` (km), `mag`, `magType`, `place`, `type`.
- Coordinates are WGS 84 (`EPSG:4326`). Use `longitude` as X and `latitude` as Y.

Source:

- USGS ANSS Comprehensive Catalog (ComCat), FDSN event web service, https://earthquake.usgs.gov/fdsnws/event/1/
- Example query (2019): https://earthquake.usgs.gov/fdsnws/event/1/query?format=csv&starttime=2019-01-01&endtime=2020-01-01&minmagnitude=2.5&minlatitude=32.5&maxlatitude=42&minlongitude=-124.5&maxlongitude=-114&orderby=time-asc

QA summary (events per file, M2.5+):

| Year | Events | M3+ | M3+ inside `cal_counties.geojson` |
|---|---|---|---|
| 2015 | 1087 | 318 | 130 |
| 2016 | 975 | 282 | 194 |
| 2017 | 854 | 224 | 167 |
| 2018 | 715 | 176 | 149 |
| 2019 | 3641 | 1385 | 1309 |
| 2020 | 2627 | 898 | 380 |
| 2021 | 1533 | 438 | 339 |
| 2022 | 958 | 270 | 199 |
| 2023 | 901 | 278 | 219 |
| 2024 | 1049 | 339 | 236 |

Notes:

- The catalog is revised over time, so a fresh download may differ slightly.
- When QGIS opens these CSVs from a file path (e.g. in a batch or model), every column is read as text. Comparisons such as `"mag" >= 3` still work; convert with `to_real("mag")` for math or graduated symbology.
