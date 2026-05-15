---
title: ""
format:
  html:
    theme: cyborg
    css: terminal_theme.css
    include-after-body: terminal_theme_include.html
resources:
  - terminal_theme.js
---

# Gran Chaco Land-Use Change Detection

## Goal

Detect land-use change and deforestation in the Gran Chaco using dry-season satellite image composites.

## Study Area

- Use the [Gran Chaco AOI GeoJSON](assets/gran_chaco_aoi.geojson) as the area of interest.
- The AOI covers dry forest and agricultural clearing near the Cerro Chovoreca frontier in northern Alto Paraguay.
- Dry-season imagery composites are used to avoid cloud cover and reduce seasonal differences.

## Data 

You are being provided with data for an area in Paraguay's [Gran Chaco region](https://en.wikipedia.org/wiki/Gran_Chaco). The AOI includes dry forest and more recent agricultural clearing near the Cerro Chovoreca frontier. The dataset includes annual dry-season median composites made from June-August imagery.

Using Google Earth Engine, Sentinel-2 and Landsat 5, 7, 8 and/or 9 images were searched from June through August for the years 2000-2025. Imaged were filtered to exclude those with too many clouds or shadows, and in order to maintain fairly similar sun angle. If you would like to see how this was done see [this notebook](assets/sentinel_gran_chaco.html).

The bands of the exported imagery are given in @tbl-exported-bands.

| Exported TIF band | Common name | Sentinel-2 band | Landsat 5/7 band | Landsat 8/9 band |
| --- | --- | --- | --- | --- |
| 1 | Blue | B2 | SR_B1 | SR_B2 |
| 2 | Green | B3 | SR_B2 | SR_B3 |
| 3 | Red | B4 | SR_B3 | SR_B4 |
| 4 | Near infrared | B8 | SR_B4 | SR_B5 |
| 5 | Shortwave infrared 1 | B11 | SR_B5 | SR_B6 |
| 6 | Shortwave infrared 2 | B12 | SR_B7 | SR_B7 |

: Exported image band order and source sensor bands. {#tbl-exported-bands}


## Change Detection Workflow

1. Choose comparison years.
   - Select one older image and one newer image.
   - Good starting pairs:
     - 2018 vs 2025 for Sentinel-2
     - 2000 vs 2025 for Landsat-based long-term change

2. Inspect false-color composites.
   - Use NIR, red, green to highlight vegetation.
   - Use SWIR1, NIR, red to highlight bare soil, clearing, and dry vegetation.

3. Calculate vegetation or disturbance indices.
   - NDVI:
     - `(NIR - Red) / (NIR + Red)`
   - NBR:
     - `(NIR - SWIR2) / (NIR + SWIR2)`
   - NDMI:
     - `(NIR - SWIR1) / (NIR + SWIR1)`

4. Subtract index rasters.
   - Calculate:
     - `newer_index - older_index`
   - Large negative values may indicate vegetation loss or clearing.
   - Large positive values may indicate vegetation recovery or crop growth.

5. Classify change.
   - Pick a threshold for likely clearing.
   - Example:
     - strong vegetation loss
     - little or no change
     - vegetation gain
   - Adjust thresholds after visually checking known cleared areas.

6. Clean the change map.
   - Remove small isolated patches.
   - Optional: polygonize the change raster.
   - Optional: calculate area of changed land.

7. Validate visually.
   - Compare the change map against the original before/after imagery.
   - Check several cleared fields and intact forest patches.
   - Note confusion between cropland cycles, bare soil, burned areas, and true forest clearing.

## Outputs

- Before and after dry-season composites.
- False-color maps showing land-cover patterns.
- Index difference raster.
- Classified change raster or vector layer.
- Summary table of changed area.
- Short interpretation of where and how land use changed.

## Notes

- Use the same months for each year to reduce seasonal bias.
- Median composites help, but they do not remove all phenology or crop-cycle differences.
- Sentinel-2 gives better spatial detail from 2018 onward.
- Landsat gives a longer historical record at coarser resolution.
