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

Pay attention to the hand icon. That lets you pan around the map. Then there's the magnifying glass icons. The main ones you'll use contain the plus and minus signs. They let you zoom in and out on the map. 

Take a minute to use them to navigate around your map. 

Now let's add some data.

### Adding data to your map 

We're going to make a simple map that shows a color for each state, based on the population. This is [called a chloropleth](https://en.wikipedia.org/wiki/Choropleth_map). 

Before we do that, I want you to take a look at the attributes of the state map you've already loaded. You want to look in the layers panel, which shows you each thing ("thing" is not official terminology), or layer, that you've added so far. Right click on our state's layer and click **open attribute table**. 

![Here's what you want.](/qgis4.jpg)

Voila. A table. There's a record for every state in our map. 

![Here's what you want.](/qgis5.jpg)

Pay special attention to the STATEFP column. That's important. That is the FIPS code for each state. We're going to use that to join up the data we download. 









