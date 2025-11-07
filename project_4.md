---
title: ""
format:
  html:
    theme: cyborg
---

# NR 218 Project 4: QGIS Raster Workflow with NEON Data

This project mirrors the [NEON "Raster Data in R"](https://www.neonscience.org/resources/learning-hub/tutorials/raster-data-r) tutorial, but every task is completed in QGIS instead of R. Follow the workflow below, document your process with screenshots, and answer the reflection prompts at the end.

## Learning Goals

- Practice downloading and organizing NEON remote sensing raster products
- Inspect spatial metadata, bit depth, and NoData handling inside QGIS
- Build multi-band raster composites and derive canopy/surface metrics with Raster Calculator
- Clip and summarize rasters with study-area polygons using built-in QGIS geoprocessing tools
- Export publication-ready rasters and QA plots that match the NEON tutorial outputs

## Data + Prep Work

1. **Download the NEON SJER raster sample bundle** used in the NEON tutorial (DSM, DTM, RGB imagery, canopy height model, and a shapefile of the SJER plot boundary). You can grab the identical zip here: <https://www.neonscience.org/sites/default/files/NEON-DS-Imaging-SJER.zip>
2. Extract the archive to `data/project_4/` inside this repo. Keep the folder names (`NEON-DS-Airborne-RemoteSensing/SJER/`) intact so layer names match the instructions.
3. Launch QGIS ≥ 3.30 and create a project file `project_4_sjer.qgz` in the same directory. Set the default CRS to `EPSG:32611` (UTM Zone 11N) to match the NEON raster products.

> **Tip:** Add the folders inside `data/project_4` to the QGIS Browser Favorites so you can drag files in quickly.

## Guided QGIS Workflow (mirrors NEON steps)

### 1. Inspect Raster Metadata
- Drag `SJER_dsmCrop.tif` and `SJER_dtmCrop.tif` into the map.
- Open **Layer Properties ▸ Information** and record: CRS, resolution, pixel count, NoData value, and min/max elevation. Compare to what NEON reports in their R output tables.
- Screenshot the metadata panel and include it in your submission.

### 2. Visualize Single-Band Elevation Rasters
- With `SJER_dsmCrop.tif` selected, open **Symbology** and switch to **Singleband pseudocolor**.
- Choose the `Spectral` color ramp, set the min/max to the reported DSM range, and enable the **Histogram stretch** to mimic the R plots.
- Duplicate the layer styling for the DTM (right-click ▸ Styles ▸ Copy/Paste).
- Export both styled rasters as PNGs (**Project ▸ Import/Export ▸ Export map to image**) named `dsm_render.png` and `dtm_render.png`.

### 3. Build a Multi-Band RGB Composite
- Add the three files `SJER_ORT_1.tif`, `SJER_ORT_2.tif`, `SJER_ORT_3.tif` (red, green, blue bands).
- Use **Raster ▸ Miscellaneous ▸ Build Virtual Raster (VRT)** to stack them into `SJER_RGB.vrt`. Set **Source band** order to 1=Red, 2=Green, 3=Blue, and check **Separate**.
- Load the VRT, change **Render type** to `Multiband color`, assign bands accordingly, and apply a slight saturation boost via **Layer Rendering ▸ Contrast**.
- Save the styled RGB map as `sjer_rgb_map.png`.

### 4. Derive a Canopy Height Model (DSM − DTM)
- Open **Raster ▸ Raster Calculator** and compute `"SJER_dsmCrop@1" - "SJER_dtmCrop@1"`.
- Save the output as `SJER_chm_qgis.tif` inside `data/project_4/outputs`. Set the output data type to `Float32` and NoData = `-9999` to match NEON.
- Bring the CHM into the map, apply a graduated style with 2 m class breaks (0–2, 2–5, 5–10, 10–20, >20 m). Label the legend classes clearly.

### 5. Clip Rasters to the SJER Plot Boundary
- Add the boundary shapefile `SJER_plotBoundary.shp`.
- Use **Raster ▸ Extraction ▸ Clip Raster by Mask Layer** to clip DSM, DTM, RGB VRT, and CHM to the boundary. Name the outputs `*_plot.tif`.
- Confirm the clip preserved the CRS and NoData values; document by showing the **Metadata** tab for one clipped raster.

### 6. Summarize Elevation and Canopy Stats
- Convert the plot boundary polygon to a layer with an attribute field `Plot_ID = "SJER"` (attribute table ▸ toggle edit ▸ field calculator).
- Run **Raster ▸ Zonal statistics** twice: once for DSM, once for CHM. Calculate mean, min, max, standard deviation, and count; write results into fields prefixed `DSM_` and `CHM_`.
- Capture a screenshot of the attribute table showing the computed stats. Cross-check the values against the R tutorial results.

### 7. Profile and Histograms
- Use the **Raster layer histogram** (Layer Properties ▸ Histogram) for DSM and CHM to reproduce the NEON distribution plots. Export each histogram as an image and note the bin settings used.
- Optional: draw an elevation profile using the **Profile Tool** plugin to mimic the NEON line plots.

### 8. Document Outputs
Create a layout (`Project ▸ New Print Layout`) that contains:
- Map frame showing the clipped CHM with boundary overlay
- Insets for DSM and RGB renderings
- Table displaying zonal stats results
- Text blocks citing data source (NEON, 2018) and projection info
Export the layout as `project_4_layout.pdf`.

## Reflection & Deliverables

1. **Short Answer (submit in Canvas or append to this repo)**
   - How do the DSM and DTM ranges compare to the R-based summary values? Explain any differences.
   - Describe your workflow for handling NoData in QGIS. Where did you confirm the mask value?
   - What advantages did you notice when completing the raster math (CHM) in QGIS versus code?

2. **Files to Upload to Canvas**
   - `dsm_render.png`, `dtm_render.png`, `sjer_rgb_map.png`, `project_4_layout.pdf`
   - Screenshots of metadata panels, zonal statistics table, histograms, and any optional profile plots (include timestamps).
   - A short PDF or Markdown note answering the reflection prompts.

3. **Include in Repo Submission (if requested)**
   - `project_4.md` (this file) plus any QGIS project files or derived rasters under `data/project_4/outputs/`.

Stay organized, follow the NEON tutorial’s order, and call out any deviations you make while working in QGIS so the workflow can be replicated.
