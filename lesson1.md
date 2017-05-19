# Getting started with QGIS

### Download the data from Census Bureau 

One of the most important sites for GIS work is the [Census Bureau's TIGER program](https://www.census.gov/geo/maps-data/data/tiger.html).

It is a tremendous resource of boundary maps of all kinds: states, legislative districts, congressional districts, counties, cities and so on. 

Let's go to the [download page](https://www.census.gov/geo/maps-data/data/tiger-line.html) and click on the link for the web interface. 

![Here's what you want.](../screenshots/tiger1.jpg)

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

### Let's get ready to cook

We're going to make a simple map that shows a color for each state, based on the population. This is [called a chloropleth](https://en.wikipedia.org/wiki/Choropleth_map). 

Before we do that, I want you to take a look at the attributes of the state map you've already loaded. You want to look in the layers panel, which shows you each thing ("thing" is not official terminology), or layer, that you've added so far. Right click on our state's layer and click **open attribute table**. 

![Here's what you want.](/qgis4.jpg)

Voila. A table. There's a record for every state in our map. 

![Here's what you want.](/qgis5.jpg)

Pay special attention to the STATEFP column. That's important. That is the FIPS code for each state. Just like a SQL database, we're going to join data based on a field. In our case, that field is STATEFP. 

Now let's go to the Census Bureau and [download the 2016 population estimates.](https://www.census.gov/data/datasets/2016/demo/popest/nation-total.html) 

![Here's what you want.](/qgis6.jpg)

Open up the data you just downloaded and take a look. Now is a good time to remind you about those pesky numeric columns in Excel. If you click directly on a CSV to open it in Excel, there's a good chance it will guess wrong on columns with numbers that should be text. 

![Here's what you want.](/qgis8.jpg)

So remember to take care and pay attention to those pesky numbers-that-should-be-text columns (zip codes are a prime culprit). A way around this is to use Excel's import from text. Then you can explicitly tell Excel the proper data type for each column.

![Here's what you want.](/qgis9.jpg)

Look at the column called STATE. Those are the FIPS code in this dataset. So we want to join this data to our map. If you think about SQL, it's the equal of doing something like this: 

```SQL
select a.*
from state_boundary_map a
left join population_data b 
  on a.STATEFP = b.STATE
```

When I attended map camp at NICAR, Jennifer LaFleur told us to think of it like pouring ingredients into a bowl. The population data we just downloaded are the ingredients, the state boundaries are the bowl. 

### But we need to do some pre-processing

But here's the problem: When we go to import this file into QGIS, it's going to take a guess at these fields and you're probably not going to like the results. So [there's a way](https://anitagraser.com/2011/03/07/how-to-specify-data-types-of-csv-columns-for-use-in-qgis/) to force QGIS to recognize the data types for each column. 

First, let's shorten up the spreadsheet. Delete all the columns except for the first five columns (SUMLEV, REGION, DIVISION AND STATE), as well as **ESTIMATESBASE2010** AND **POPESTIMATE2016** fields. Save your current spreadsheet as a .csv file. 

![Here's what you want.](/qgis18.jpg)

Now let's add a blank line at the top. Above each column header, enter whether it's "Integer, Real, String, Date (YYYY-MM-DD), Time (HH:MM:SS+nn) and DateTime (YYYY-MM-DD HH:MM:SS+nn)." Let's keep it simple and just use Integer and String (text). 

![Here's what you want.](/qgis19.jpg)

Don't save it. Instead, copy and paste that first row into a new spreadsheet. 

![Here's what you want.](/qgis20.jpg)

Then save it as its own csv. In this case, it needs to have the exact same name as the main spreadsheet, only with a .csvt extension.


![Here's what you want.](/qgis21.jpg)

That file acts as a "guide" for QGIS to know what data type each field in the main CSV should be. 

One last thing. Open the the .CSVT file you just saved and make sure it has quotes around each field. If not, add them.

![Here's what you want.](/qgis22.jpg)


### Get the bowl ready

So let's add the ingredients to the bowl. 

Start by looking at the left rail where we added the shapefile data. Let's use a different button. 

![Here's what you want.](/qgis10.jpg)

And your screen should look like this. In this case, we aren't loading geographic data, so make sure you click the No Geometry radio button.

![Here's what you want.](/qgis7.jpg)

Notice QGIS added our data to the list of layers. Now we need to join it to the states shapefile. 

Double click on the states shapefile. You'll get the below screen. Click on joins. 

![Here's what you want.](/qgis12.jpg)

At the bottom of the screen is a little plus sign. Let's use that. 

![Here's what you want.](/qgis13.jpg)

So what we're going to do is tell QGIS what table we want to join, the fields on which to join (remember our SQL example above?) and which fields we want to join up. In this case, for 


![Here's what you want.](/qgis14.jpg)

Hit OK. 

So we've added the ingredients (population data) and poured it into the bowl (the state boundary shapefile). To prove it, right click on the state shapefile and open the attribute table. Scroll all the way to the right. You should see your new fields. 

![Here's what you want.](/qgis15.jpg)

Now let's make this map useful. 

Left click on the state layer and open the properties screen. Click on style. 

There's a lot of stuff going on here.

First, we want to select graduated. Remember when we discussed continuous variables? Graduated allows you to color the states based on a continuous variable. 

Then there's the color ramp. This is just the range of colors you see. You can change it, if you want, but I'm going to leave it alone. 

Next is the number of classes. We've selected five. That means we'll have five categories. 

See the mode? That just gives us options of how to automatically set the ranges for each of the classes. 

Hit the classify button.

![Here's what you want.](/qgis17.jpg)

In the picture below, you'll see it has equally divided each of the classifications into roughly 785,000 people. This probably isn't the best way to do this, but for now let's leave it alone. 

![Here's what you want.](/qgis23.jpg)

Hit OK.

We have a map. 

![Here's what you want.](/qgis24.jpg)

But this doesn't tell us very much, does it? 

Let's make some changes. Open the properties table again for the states layer. We could use one of the other preset modes, which might be useful, or we could make our own custom categories. 

The most populous state, California, has about 39 million people. Let's see what happens if we break these into categories of 5 million. 

In the values area, double click on a value. 

![Here's what you want.](/qgis25.jpg)

You should be able to create categories like so:

![Here's what you want.](/qgis26.jpg)

And now we have a new map. What do you think?

![Here's what you want.](/qgis27.jpg)

You could tinker with the map all day. Try different modes. Try your own manual ranges. 

When I make a map, it is usually for reporting purposes. I'm trying to understand the spatial distribution of some sort of data. But sometimes what I might need to better understand the data might be different than how we should display it graphically for the public. I try to work closely with our graphical journalists on that front. 










