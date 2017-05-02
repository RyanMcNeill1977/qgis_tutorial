# Getting started with QGIS

One of the most important sites for GIS work is the [Census Bureau's TIGER program](https://www.census.gov/geo/maps-data/data/tiger.html).

It is a tremendous resource of boundary maps of all kinds: states, legislative districts, congressional districts, counties, cities and so on. 

Let's go to the [download page](https://www.census.gov/geo/maps-data/data/tiger-line.html) and click on the link for the web interface. 

![Here's what you want.](/tiger1.jpg)

Download the U.S. states for 2016. Unzip it. 

Now back to QGIS. 

On the left side of the screen, you see a number of icons, each for a different kind of data you can add. We're using a shapefile, an extremely common way of storing GIS data. 

A shapefile is actually multiple files. Wikipedia has a [good breakdown of a shapefile](https://en.wikipedia.org/wiki/Shapefile). I've copied and pasted the main ingredients. 

.shp — shape format; the feature geometry itself
.shx — shape index format; a positional index of the feature geometry to allow seeking forwards and backwards quickly
.dbf — attribute format; columnar attributes for each shape, in dBase IV format

Other files 
.prj — projection format; the coordinate system and projection information, a plain text file describing the projection using well-known text format
.sbn and .sbx — a spatial index of the features
.fbn and .fbx — a spatial index of the features that are read-only
.ain and .aih — an attribute index of the active fields in a table
.ixs — a geocoding index for read-write datasets
.mxs — a geocoding index for read-write datasets (ODB format)
.atx — an attribute index for the .dbf file in the form of shapefile.columnname.atx (ArcGIS 8 and later)
.shp.xml — geospatial metadata in XML format, such as ISO 19115 or other XML schema
.cpg — used to specify the code page (only for .dbf) for identifying the character encoding to be used
.qix — an alternative quadtree spatial index used by MapServer and GDAL/OGR software

