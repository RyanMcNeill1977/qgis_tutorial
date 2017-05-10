# QGIS Lesson 2

OK. So in the first lesson we learned to make a basic map. But that's not why we're here. Let's do something more interesting. 

### Earthquake! 

Believe it or not, Oklahoma is now one of the most seismically active areas in the country. Scientists link the massive increase
in seismicity to wastewater injection wells, which store waste from the fracking process used to pry loose natural gas from the ground. 

So lets figure out which communities have been the site of the most earthquake epicenters. 

To make things easy, I've downloaded the earthquake data for you. The source of the data is the [United States Geological Survey](https://earthquake.usgs.gov/earthquakes/search/).

I selected all quakes with a magnitude greater than 2.5 between 5/10/2013 and 5/10/2017. 

Obviously if you were working with this data for a real story, you'd want to read the documentation and discuss with USGS officials 
about any caveats that might exist with this data. But for our class, we'll skip that step. 

Let's fire up QGIS. Our data is a CSV so let's add a delimited file. But unlike the last lesson, we need to tell QGIS that this file contains geometry information. 

![Here's what you want.](/lesson2_1.jpg)

Hit OK. 

Now this brings up an important screen. Why? The dreaded projections. More on that later. 

For now, just use the filter to whittle down the selections to those with NAD83. Pick the NAD83 option that's a geographic coordinate system (as opposed to the projected coordinate systems). 

![Here's what you want.](/lesson2_2.jpg)

Hit OK. Boom we have dots. 

![Here's what you want.](/lesson2_3.jpg)

Now let's add some state boundaries on the map to help us get a grasp of what's where. 

Go to the Census Bureau's [TIGER program site](https://www.census.gov/geo/maps-data/data/tiger-line.html) and download the state boundaries file, just like we did in lesson one.

Now let's put it on the map. 

![Here's what you want.](/lesson2_4.jpg)

Well, crap. That's not much help. Let's fix this. 

Right click on the state layer and open the properties. Adjust the layer's transparency. 

![Here's what you want.](/lesson2_5.jpg)

Now click OK. You might need to tinker with it to get things where you want. 

We want to concentrate on Oklahoma and we've got all these other dots on the map. Let's fix that.

Go to Vector->Research Tools>-Select by location.

![Here's what you want.](/lesson2_6.jpg)

Right click on the state layer and select filter. 

![Here's what you want.](/lesson2_7.jpg)

So this screen allows you to write queries and limit what appears on the map based on the filters you select. Your SQL skills will come in handy. 

Highlight the NAME field, then hit all. What this does is give you all the values in the NAME field. 

![Here's what you want.](/lesson2_8.jpg)

This helps us write our query. 

Now double click on NAME. Then hit the equal button. Then select Oklahoma (you might have to hit ALL again to see the values). 

![Here's what you want.](/lesson2_9.jpg)




