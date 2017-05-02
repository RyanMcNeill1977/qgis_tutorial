# Getting started with QGIS

### Download the data from Census Bureau 

One of the most important sites for GIS work is the [Census Bureau's TIGER program](https://www.census.gov/geo/maps-data/data/tiger.html).

It is a tremendous resource of boundary maps of all kinds: states, legislative districts, congressional districts, counties, cities and so on. 

Let's go to the [download page](https://www.census.gov/geo/maps-data/data/tiger-line.html) and click on the link for the web interface. 

![Here's what you want.](/tiger1.jpg)

Download the U.S. states for 2016. Unzip it. 

### What's a shapefile?

We just downloaded a shapefile, controlled by ESRI (the maker of ArcGIS) and widely used to distribute GIS data. 

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


### Add the data to QGIS

Now back to QGIS. 

Click on the icon to load a shapefile vector layer. 

![Here's what you want.](/qgis2.jpg)

Chose file and click browse to navigate to your file. Remember how we said shapefiles are actually multiple files? Select the file called **tl_2016_us_state.shp**. Click open. Voila! You have a map. 

### Navigate around the map

Now's a good time to take a quick interlude and discuss how to navigate around your map. At the top of QGIS, you'll see a couple of rows of icon. Below is a picture of some key ones for getting around. 

![Here's what you want.](/qgis3.jpg)










