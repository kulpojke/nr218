---
title: ""
format: 
  html:
    theme: cyborg
---

# Lab 2: Mapping

## Learning Goals

- Understand geographic concepts
- Start working with geographic data 
- Make your first map!
- Start working with map attributes and styling
- Practice organizing files

## Introduction

This assignment consists of three parts. Written responses, tutorials, and a short project in which you will make a map.

Make a Folder called `NR218` in your home folder. Make a subdirectory, `lab_2` inside of `NR218`

```
agustov
└──nr218 
   └── lab_2
```

__All of your work for this lab will go into the `lab_2` directory. You will zip it and submit the zipped file on Canvas__

# Written Responses (3 pts)

__Provide written responses to the following Questions in a pdf__. Name the document `answers.pdf` save it in your`NR218/lab_2` folder.

1. **Map Scale Analysis**: Determine and discuss the most appropriate (approximate) representative fractions for the following verbal map scale descriptions: (a) individual person, (b) neighborhood, (c) urban, (d) regional, (e) national, and (f) global.

2. **Map Projections Research**: Go to the National Atlas website and read about map projections ([archived link](http://web.archive.org/web/20110717124751/http://www.nationalatlas.gov/articles/mapping/a_projections.html)). Define the following terms:
   a. datum
   b. developable surface
   c. secant
   d. azimuth
   e. rhumb line
   f. zenithal

4. **Projection Properties**: Describe the general properties of the following projections: 
   a. Universal Transverse Mercator (UTM)
   b. State plane system
   c. Robinson projection

5. **USGS Topographic Maps**: 
   - Download a map for your place of residence from: [https://ngmdb.usgs.gov/topoview/](https://ngmdb.usgs.gov/topoview/)
   - What are the scale, projection, and contour interval of the USGS topographic map that you downloaded for your place of residence?

6. **Coordinate Systems**: Find the latitude and longitude of your hometown. Explain how you can convert the coordinates from DD to DMS or vice versa.


# Tutorial Assignments (3 pts)
Make a subdirectory called `tutorials` within your `NR218/lab_2` directory.

```
agustov
└──nr218
   └── lab_2
       └── answers.pdf
       └── tutorials
```

Complete the following tutorials.   Put screenshots of the final product for each tutorial within `NR218/lab_2/tutorials`.  Give the screenshots reasonable names (e.g. `attributes_tutorial.png`)


- [Working With Attributes](https://www.qgistutorials.com/en/docs/3/working_with_attributes.html)
- [Basic Vector Styling](https://www.qgistutorials.com/en/docs/3/basic_vector_styling.htm)
- [Calculating Line Lengths and Statistics](https://www.qgistutorials.com/en/docs/3/calculating_line_lengths.html ) (in the first step of this, it tells you to use a file that is still inside of the zip file.  Do not do that. Extract the file first!)


# Making a Map (3 pts)

**Make your first (production quality) map!** 
- Make a subdirectory called `map` within your `NR218/lab_2` directory in which to store files for this part.
- Complete the [Making a Map tutorial](https://www.qgistutorials.com/en/docs/3/making_a_map.html)
- __Submit a PDF image of the final map you created at the end of the tutorial__

# Show your directory structure (1 pt)

In the terminal navigate to your `NR218/lab_2` folder.  Use `tree` (or in PowerShell `tree /F` to show the directory structure).  __Paste the tree output into a text file called `tree.txt` (or .rtf) and save to you `lab_2` folder__.

# How to submit

Make a zip of your `lab_2` folder.  Submit it on Canvas.

[How to zip stuff on OSX](https://support.apple.com/guide/mac-help/zip-and-unzip-files-and-folders-on-mac-mchlp2528/mac)

[How to zip stuff on Windows](https://support.microsoft.com/en-us/windows/zip-and-unzip-files-8d28fa72-f2f9-712f-67df-f80cf89fd4e5)

On Linux, in terminal 
```bash
zip -r lab_2.zip lab_2
```
