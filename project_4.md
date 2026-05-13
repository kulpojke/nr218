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
+ The change in NDVI between 2018 and 2024 in the four plots (`vectors/plots.geojson`)
+ (5% BONUS) The approximate change in volume of water stored in the reservoir between 2018 and 2024. (See this [painfully slow video](https://youtu.be/ZUR1qk5Vhlg?si=99NvkaGSXbNA-N2_) for tips.) 


## Deliverables
### Description of methods
Write a short document describing the methods you used to solve the problem.  It should contain:

+ Methods: Write a clear explanation of what you did, and why.  Document the steps you took, use figures where needed.  
+ A table of important layers created in your workflow. (These layers should be cross referenced in your methods.)
+ Solution:  Tell me your estimate for the volume of water, how confident you are in your answer, and what the major sources of error are.

A zip file of your project directory.


## How the Project will be graded

Recall from the syllabus that the Project is worth 20% of the grade.  The final exam, which is about the project, is worth another 20%. 

The project itself will be graded 50% on your explanation of the methods you used, 25% on having reasonable estimates, and 25% on the project opening and containing all of the layers you describe in you methods.

>Hints:  
> You will need to mosaic the raster tiles.  You used build vrt in the section above to stack bands. Now use it to mosaic tiles. Think about the differences between mosaicing and stacking.  
> For a sanity check on your solution, the total volume of the reservoir is currently estimated as 232,000,000 $m^{3}$