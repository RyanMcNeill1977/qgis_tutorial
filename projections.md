### All the Earth's Projections

One last thing I want to point out is the EPSG at the bottom right of your screen. 

![Here's what you want.](/qgis28.jpg)

This refers to the projection of the map. 

Below are a few bullet points from [this really useful United States Geological Survey website](https://egsc.usgs.gov/isb//pubs/MapProjections/projections.html) on map projections. 

Long story short, we could spend a massive amount of time --- far more time than we have in this class --- to discuss map projections. There are whole textbooks on the topic. 

As the USGS says above, there's no "right" map projection that always works. It depends on what you're doing. 

![Here's what you want.](/qgis29.jpg)
![Here's what you want.](/qgis30.jpg)

See the difference?

The first map is in EPSG 4269, [also known as NAD83](http://spatialreference.org/ref/epsg/4269/). This is the most common format used by federal agencies. That is the format of our map. 

The second is EPSG 102008, which is Albers Equal Area Conic. [Read a little bit about that projection](http://desktop.arcgis.com/en/arcmap/latest/map/projections/albers-equal-area-conic.htm) on the ESRI site. 

The first map is unprojected. 

The second map is projected. What does that mean? [Check this document out](https://www.nceas.ucsb.edu/~frazier/RSpatialGuides/OverviewCoordinateReferenceSystems.pdf).

From the document:

"The elliptical Earth can be projected onto a flat surface (i.e., a paper map). Map coordinates of a point are computed from its
ellipsoidal latitude and longitude by a standard formula known as a map projection. It is impossible to flatten a round object
without distortion, and this results in trade-offs between area, direction, shape, and distance. For example, there is a trade-off
between distance and direction because both features can not be simultaneously preserved. There is no 'best' projection, but
some projections are better suited to different applications."
