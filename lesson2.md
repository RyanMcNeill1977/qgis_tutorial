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

Hit OK. Voila. 

![Here's what you want.](/lesson2_10.jpg)

Let's go ahead and save our Oklahoma shape just in case we need it later. Right click on the state layer and select save as. 

Name your file something you can remember. I like to keep the original name, then just add a suffix describing what it is. 

![Here's what you want.](/lesson2_11.jpg)

Hit OK. 

Your new shapefile will show up in the layers panel. Awesome. 

Now let's whittle down our dots. 

We're going to use a little different method this time. Instead of selecting the features we want based on their attributes, this time we're going to select the features we want based on their spatial location. 

To do that, go to Vector->Research Tools->Select by location.

![Here's what you want.](/lesson2_12.jpg)

What we want to do is tell QGIS to select all the dots that intersect the the Oklahoma boundary. So set it up like so: 

![Here's what you want.](/lesson2_13.jpg)

Hit run. QGIS might chug a little bit. 

Finally, you'll have some results. It might be a little hard to see because the Oklahoma shape is in the way. Click on the next next to the Oklahoma layer or change the transparency. Whichever is easier for you.

See all those yellow dots? Those are the dots selected based on your select by location query.

![Here's what you want.](/lesson2_14.jpg)

Now we want to do one more thing: Save those selected dots as their own file. Right click on the dots layer and select SAVE AS. 

You've seen this screen before. But this time you want to do something a little different. We want to tell QGIS to only save the selected dots.

Name it what you want. The important thing to remember is to click the box telling QGIS to save only the selected features.

![Here's what you want.](/lesson2_15.jpg)

Hit OK.

Voila! Now you have a file with just the Oklahoma dots. 

Now you should have four maps in your layer panel. The original state boundaries and the Oklahoma boundaries, as well as the original dots layer and the Oklahoma layer. 

I like to keep my map area clean. Less chance for confusion. Let's clear off our workspace by hitting the blank white piece of paper. Then let's reload just the Oklahoma dots and the Oklahoma boundary.

![Here's what you want.](/lesson2_16.jpg)

OK. Our original question was which communities have the most earthquake epicenters. 

Let's go back to the Census Bureau's TIGER page and download the shapefile for places in Oklahoma. Add it to your map. 

Now let's count the number of dots in each place. To do this, go to Vector->Analysis Tools->Count points in polygon. 

![Here's what you want.](/lesson2_17.jpg)

This works as you'd expect. See the count field name? QGIS is going to add a new field to your polygon layer with a count of the dots. Name it what you want, but I just leave it as numpoints. 

![Here's what you want.](/lesson2_18.jpg)
