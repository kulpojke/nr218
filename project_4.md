---
title: ""
format:
  html:
    theme: quartz
---

# Project 


__Download data__ for [Cachuma Reservoir](https://cpslo-my.sharepoint.com/:f:/g/personal/mthuggin_calpoly_edu/IgAhORxF2PtRRrtnycd25E56AXpYGpyTdPoqMhJC_xQJsL4?e=DbWm9j)

It includes:  

   + a DEM from summer of 2018 (as tiles)
   + Sentinel-2 image from July, 2018
   + Sentinel-2 image from February, 2014

## Task

Find the following:

+ The approximate surface area of the lake in summer, 2018
+ The approximate elevation of the lake surface in summer, 2018
+ The approximate surface area of the lake in February, 2024
+ The approximate elevation of the lake surface in February, 2024
+ The approximate change in volume of water stored in the reservoir between 2018 and 2024. (See this [painfully slow video](https://youtu.be/ZUR1qk5Vhlg?si=99NvkaGSXbNA-N2_) or [this webpage](https://esurveying.net/earthwork-quantity/volume-calculation-contour-method) for tips.) 
+ The change in NDVI between 2018 and 2024 in the four plots (`vectors/plots.geojson`)


## Deliverables
__1) Description of methods__  
Write a short document describing the methods you used to solve the problem. Here is an example [faux-document](project_outline_example.html)  It should contain:

+ Methods: Write a clear explanation of what you did, and why.  Document the steps you took, use figures where needed.  
+ A table of important layers created in your workflow. (These layers should be cross referenced in your methods.)
+ Solution:  Tell me your estimate for the volume of water, how confident you are in your answer, and what the major sources of error are.

__2) GIS Poject Files__  
A zip file of your project directory.

__3) A pdf map of the project area__  
Should include scale, legend, and North arrow.

## How the Project will be graded

Recall from the syllabus that the Project is worth 20% of the grade.  The final exam, which is about the project, is worth another 20%. 

The __project grade__ will be based on:

+ Explanation of the methods, methods are applicable to the problem (25%)
+ Reasonable estimates of the values (25%)
+ The project opens and contains all of the layers you describe in you methods (25%)
+ Your map has all of the required elements, and looks ok (25%)

The __final exam grade__ will be based on:

+ You can explain your methods, and answer questions about them.

## Hints
+ You will need to mosaic the raster tiles or build a vrt
+ For a sanity check on your volume estimation, the total capacity of the reservoir is currently estimated as 232,000,000 $m^{3}$
