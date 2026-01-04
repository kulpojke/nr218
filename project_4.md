---
title: ""
format:
  html:
    theme: cyborg
---

__Changes:__

+ __2025-11-11 - Band information in section 3 of part 1 was incorrect.__
   + The table has been changed and now reflects the proper band values (band 58 is red, band 90 is NIR)
   + also, band 90 was missing coordinate data, you may have notices it
   would not work with the vrt building step.  This is because band 90 was plotting
   into a 1m $\times$ 1m square on the prime meridian and equator.  As a result, the
   build vrt function was trying to buils a vrt with 1m resolution than included
   the actual site, and [Null Island](https://en.wikipedia.org/wiki/Null_Island).
   + A fixeD version of band 90 can be downloaded [herE](https://cpslo-my.sharepoint.com/:i:/g/personal/mthuggin_calpoly_edu/EZHfrzYO7KZMniR4iCj4nYABFfDmEmYGbNlHaKVGeIkLBw?e=W4m1ug)

# Project 4

There are two parts; a tutorial, and a challenging task for you to figure out.

# Part 1: QGIS Raster Workflow with NEON Data

This project is adabted from the [NEON "Raster Data in R"](https://www.neonscience.org/resources/learning-hub/tutorials/raster-data-r) tutorial, but every task is completed in QGIS instead of R. Follow the workflow below, document your process with screenshots, and answer the reflection prompts at the end.

If you are not familiar with National Ecological Observatory Network (NEON), it is the U.S National Science Foundation's continental-scale observation facility. It is designed to collect long-term ecological data. Click [here](https://www.neonscience.org/) for more information about NEON.

## Learning Goals

- Practice downloading and organizing remote sensing raster products
- Inspect spatial metadata, bit depth, and NoData handling inside QGIS
- Build multi-band raster composites and derive tree canopy/surface metrics with Raster Calculator
- Clip and summarize rasters with study-area polygons using built-in QGIS geoprocessing tools
- Export publication-ready rasters and QA plots that match the NEON tutorial outputs

## Downloading Data and Preparation

1. **Download the NEON SJER raster sample bundle** used in the NEON tutorial [here](https://ndownloader.figshare.com/files/7907590). This data comes from the [San Joaquin Experimental Range](https://www.neonscience.org/field-sites/field-sites-map/SJER) field site (SJER). It includes a digital surface model (DSM), digital terrain model (DTM), RGB imagery, canopy height model (CHM), and a shapefile of the SJER plot boundary.   

2. Extract the archive to a directory called `project_4/` (Wherever you are storing your files for nr218, NOT IN DOWNLOADS!). Keep the folder names (e.g. `NEON-DS-Field-Site-Spatial-Data/SJER/`) intact so that layer names match the instructions.   
<u>__Take a screenshot of your file explorer, showing the `project 4` directory and include it in your submission.__</u> 

3. Launch QGIS and create a project file `project_4_sjer.qgz` in the same directory. Set the default CRS to `EPSG:32611` (UTM Zone 11N) to match the NEON raster products.

> **Tip:** You can add the folders inside `data/project_4` to the QGIS Browser Favorites so you can drag files in quickly.

## Guided QGIS Workflow 

### 1. Inspect Raster Metadata
- Open `project_4/NEON-DS-Field-Site-Spatial-Data/SJER/DigitalSurfaceModel/SJER2013_DSM.tif` and `project_4/NEON-DS-Field-Site-Spatial-Data/SJER/DigitalTerrainModel/SJER2013_DTM.tif`.
- Open **Layer Properties ▸ Information** and record:  
   - CRS
   - resolution
   - pixel count
   - NoData value
   - and min/max elevation. 

<u>__Screenshot the Information panel and include it in your submission.__</u>

### 2. Visualize Single-Band Elevation Rasters
- With `SJER2013_DSM.tif` selected, open **Symbology** and switch to **Singleband pseudocolor**.
- Choose the `Spectral` color ramp, set the min/max to the reported DSM range, under "Min / Max Value Settings" enable "Cumulative count cut".
- Duplicate the layer styling for the DTM (right-click ▸ Styles ▸ Copy/Paste).
- Export both styled rasters as PNGs (**Project ▸ Import/Export ▸ Export map to image**) named `dsm_render.png` and `dtm_render.png`.

### 3. Build a Multi-Band RGB Composite
- Add the three files corresponding to red, green, and blue bands from `project_4/NEON-DS-Field-Site-Spatial-Data/SJER/RGB`

| Band | Approx. wavelength (nm) | Spectral region |
|------|-------------------------|-----------------|
| 19   | ~450                    | Blue            |
| 34   | ~520                    | Green           |
| 58   | ~610                    | Red             |
| 90   | ~660                    | NIR             |

- Use **Raster ▸ Miscellaneous ▸ Build Virtual Raster (VRT)** to stack them into `SJER_RGB.vrt`. arange the bands from top to bottom as Red, Green, Blue, and check "Place each file in seperate band"
- Load the VRT, change **Render type** to `Multiband color`, assign bands accordingly, and apply a slight saturation boost via **Layer Rendering ▸ Contrast**.
- Save the styled RGB map as `sjer_rgb_map.png`.

### 4. Derive a Canopy Height Model (DSM − DTM)
- Open **Raster ▸ Raster Calculator** and compute `"SJER2013_DSM.tif" - "SJER2013_DTM.tif"`.
- Save the output as `SJER_chm_qgis.tif` inside `data/project_4/outputs`. In the export/ save file dialogue, set the NoData equal to `-9999` (scroll to the bottom of the dialogue to do the NoData).
- Bring the CHM into the map, apply a graduated style with 2 m class breaks (0–2, 2–5, 5–10, 10–20, >20 m) by using singleband pseudocolor as the render type, and discrete interpolation.  Label the legend classes clearly.

### 5. Summarize Elevation and Canopy Stats
- Create a plot boundary vector file by extracting the extent of the DSM, use a scratch layer.
- Run **Raster ▸ Zonal statistics** twice: once for DSM, once for CHM. Calculate mean, min, max, standard deviation, and count; write results into fields prefixed `DSM_` and `CHM_`. Save the resulting vector as `project_4/NEON-DS-Field-Site-Spatial-Data/SJER/plot.geogjson'.

<u>__Capture a screenshot of the attribute table showing the computed stats.__</u>



## Reflection & Deliverables
 
- Table displaying zonal stats results
- `dsm_render.png`, `dtm_render.png`, `sjer_rgb_map.png`
- Screenshots of metadata panels, zonal statistics table (include timestamps).


# Part 2

__Download data__ for [Cachuma Reservoir](https://cpslo-my.sharepoint.com/:f:/g/personal/mthuggin_calpoly_edu/IgAhORxF2PtRRrtnycd25E56AXpYGpyTdPoqMhJC_xQJsL4?e=e3RMlj)

It includes:  

   + a DEM from summer of 2018 (as tiles)
   + Sentinel-2 image from July, 2018
   + Sentinel-2 image from February, 2014

## Task
Estimate the change in the volume of water that was in the reservoir between summer, 2018 and February, 2024. This can be done using tools that we have already used in this class.

## Deliverables
A short document with:

+ Methods: Write a clear explanation of what you did, and why.  Document the steps you took, using figures where needed.  
+ Solution:  Tell me your estimate for the volume of water, how confident you are in your answer, and what the major sources of error are.


>Hints:  
> You will need to mosaic the raster tiles.  You used build vrt in the section above to stack bands. Now use it to mosaic tiles. Think about the differences between mosaicing and stacking.  
> For a sanity check on your solution, the total volume of the reservoir is currently estimated as 232,000,000 $m^{3}$