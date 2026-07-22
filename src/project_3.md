---
title: ""
format: 
  html:
    theme: cyborg
---

# Lab 12: More Vector and Raster Stuff


## Provide written responses to the following Questions

1. What are the differences between vector and raster data? 
2. Give 3 examples (and explain your reasoning) of real-world data that are best described by:
    a. Vector datasets, and 
    b. Raster datasets. 
3. What are the trade offs of high spatial resolution in raster data? 
4. In a raster with resolution given in degrees, the ground distance represented by each cell varies from row to row.  Why?
5. Why can area and distance calculations unreliable if the layer is in the wrong projection?
6. In theory, a raster could be represented as a polygon layer in which each pixel is stored as a square polygon with attributes for its value(s). Why is this impractical compared with using a raster format?

## Project Work 

For the next questions, you will need to download the SPR [Elevation Data](https://cpslo-my.sharepoint.com/:i:/g/personal/mthuggin_calpoly_edu/IQB7BHJ9vN2fTpTTyvOoVDECAR1lB4HA5PFi8ECh-1ympRo?e=kj6ASv) use it with existing [SPR Vector Data](https://github.com/kulpojke/nr218/raw/refs/heads/main/assets/SPR_data.zip) in order to answer the following questions: 

> NOTE: pixel values, i.e. elevation, in the SPR DEM are given in feet.

7. Report the minimum, maximum, mean, and median elevation within the boundary of Swanton Ranch, as defined in sprBoundary.geojson? 

8. What are the exact elevations of the highest and lowest flumes (sprFlumes.geojson) in Swanton Ranch? 

9. Report the mean slope (in degrees) for parcels (sprParcels.geojson) with the following APN #s: `057-131-60`, `057-141-01`, and `057-121-14`.


## Submit on Canvas:
1. Answers to Written Questions 1-9 above, in a pdf.

