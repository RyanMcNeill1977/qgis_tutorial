# Getting started with QGIS

One of the most important sites for GIS work is the [Census Bureau's TIGER program](https://www.census.gov/geo/maps-data/data/tiger.html).

It is a tremendous resource of boundary maps of all kinds: states, legislative districts, congressional districts, counties, cities and so on. 

Let's go to the [download page](https://www.census.gov/geo/maps-data/data/tiger-line.html) and click on the link for the web interface. 

![Here's what you want.](/tiger1.jpg)

Download the U.S. states for 2016. Unzip it. 

Now back to QGIS. 

On the left side of the screen, you see a number of icons, each for a different kind of data you can add. We're using a shapefile, an extremely common way of storing GIS data. 

A shapefile is actually multiple files. Wikipedia has a [good breakdown of a shapefile](https://en.wikipedia.org/wiki/Shapefile). I've copied and pasted a few main ingredients. 

Mandatory files: 

|Extension|What is it?                                                                                |
|---------|-------------------------------------------------------------------------------------------|
| .shp    |the feature geometry itself                                                                |
| .shx    |a positional index of the feature geometry to allow seeking forwards and backwards quickly |
| .dbf    |columnar attributes for each shape, in dBase IV format                                     |

Other files 

|Extension  |What is it?                                                                                                               |
|-----------|------------------------------------------------------------------------------------------------------------------------- |
| .prj      |the coordinate system and projection information, a plain text file describing the projection using well-known text format|
| .sbn/.sbx |a spatial index of the features




