#QGIS 1 
#Tips & troubleshooting when getting started with QGIS

## Christine Jeavans, BBC News Visual Journalism, 
@chrisjeavans

QGIS is a great piece of software which allows geographers and GIS experts to do detailed geospatial analysis of data. However for journalists, a few relatively straightforward functions allow you to explore your data and tell your story through the power of mapping. 

###Downloading and opening QGIS

Download QGIS here. It is free - which is amazing, given how much it can do. It also gives you the option to donate to the QGIS project.

There are lots versions as QGIS is frequently updated. Find previous versions here
There is a Mac version. You have to download some more files. Make sure you install them in the order given.

_**TIP** beware that QGIS projects are not always compatible with new / old releases. You can often open an old file in a new release but when you save it may stop it working in the previous release._ 

###Finding your way around

Your version may not look exactly like this but it should have the same functionality.
The toolbars and panels can all be dragged around.

Map nav tools include:
- Pinching fingers = use the mouse wheel to zoom in and out
- Hand = grab and pan
* Three arrows on magnifying glass = zoom to full extent of the map 
* Magnifying glass with forward or back arrow = return to previous zoom level - v useful for if you (ironically) get lost in the detail of a map

Tools to add layers include
* V+ with dots = add vector layer = usually a shape file 
* Comma+ = add text delimited layer = usually a CSV

###Shapefiles

A shapefile is actually a collection of files which all correspond to each other. You will often find them in a zipped folder.
The various files include
* .shp this is the shapefile itself and it is a drawing or geometry file. It can be made up of lines, points or polygons. A map showing all the states of the USA would be a polygon shapefile. The roads or the coastline would be a line shapefile. And one showing cities would be a point shapefile. Shapefiles are VECTOR files meaning they are drawn mathematically. You can scale a shapefile to any size or project it in any way and it will always stay crisp and true.  
* .dbf database file containing information such as name of a state, its area, a unique ID code. 
* .shx index file
* .prj - projection, how this part of the globe should appear on a flat surface

_TIP keep the various elements of the shapefile all together in one folder and make sure they all have the same file name apart from the extension. This is because QGIS will need to reference them during the process._ 

###Where to find shapefiles
A good place to start with shape files is Natural Earth http://www.naturalearthdata.com/  You can freely download lots of different files here. Be aware that the more detail you choose, the bigger the file size.

To add your shapefile in QGIS hit the **V+ button** = Add Vector Layer and browse your .shp file. 
OR use the Layer>Add Layer>Add Vector Layer
OR you can even drag and drop onto your work area - there are often several ways of doing things in QGIS
Your map should now draw

_TIP if you have a very detailed shape file and moving around is slow, toggle off the render button at the bottom right of the main map panel, perform your move, then toggle back on. It means QGIS is not trying to draw all the in between stages._

Use the symbol which looks like an **i with an arrow** from the main toolbar to identify features in your shape file = it tells you what info is attributed to the shape you have clicked - e.g. a state may have its name, a unique ID code, the population at the last census or how much is land and how much water. You can also see this information for the whole shape file by clicking on the attribute table button, next to the abacus. The attribute table = all the data in the .dbf database file. 

###Preparing your data for QGIS

QGIS recognises delimited text files, the most common of which is CSV (Comma Separated Values - the comma is the delimiter of your data values). 
In practical terms, this means that if you are working in Excel, you have to save your sheet as a CSV, you can’t import the whole .xls

Keep the formatting to a minimum in order to help QGIS recognise what type of data it is looking at. 

* First row = column headers. Keep them short and either one word or use underscore (no spaces). 
* Data in separate columns
* Do not mix text and numbers within a column
* Do not use symbols such as £ or %
* Watch out for trailing spaces
* If you have lat long they need to be in in two separate columns

###Adding data

Use the comma+ button or Layer> Add Layer> Add delimited text layer

When prompted to select Geometry definition:
If you have lat long in your data (and you want to use it) then select Point coordinates
Otherwise, choose no geometry

Lat Long TIP ********

THING THAT CAN GO WRONG TIP  - about lat long bunching up


###Joining data

In order to join data you need to have an ID which is shared by the shape file and by your data. 
Often these are codes for example in the US the code for Florida is 12 - ***********link to the list of codes**********
QGIS can use this to match the data to the shape. 

Highlight shape file layer and double click for Layer properties panel>Joins
Green + button at the bottom
Join layer = the data layer you want to join
Join field = the code column in that data e.g. FIPS
Target field = the corresponding code column in the shape file.  eg GEOID
Apply and OK 

_TIP it is *possible* to join on names but really not recommended. This is because QGIS needs the text to be EXACTLY the same; different punctuation and format will prevent the join being made.
EG in UK parliamentary constituencies, City of York is sometimes written as York, City of_

_TIP  QGIS will only show areas it has data for. if you have holes in your map check if boundaries have moved and if the area was given a new number in either the data or the shapefile._

TIP the 001  and how to get round it. 

###Styling data

Often you want to make a chloropleth (sometimes called a heat map although that’s really something different) 
Once you have joined your data, use the Style section of the Layer properties panel to colour up your map according to your data
Use graduated to show a colour scale 
Select the column from your data that you want to show. This HAS to be a number (whereas categorised can be text)

IF YOU CAN’T SEE YOUR COLUMN then QGIS may not have recognised that column of data as numbers (integer) 
How to find out if this has happened - open the Layer properties panel on your data layer
Look at the fields tab, it tells you how QGIS is seeing your data. 
Integer = number
Qstring = text
It gives a clue with the abc or 123

You need to look at your original data and see if it includes anything in the problematic columns that may confuse QGIS - eg a symbol, one cell has a letter O instead of a zero, even a 1,000 separator can cause problems
Then re-import 

If you still can’t fix it try this to force QGIS to see your string column as number.

Method A
Method B

Categorising data
Scaling data



Labels

To label your counties, either bring up the Layer properties menu again or use the abc button on a yellow background
￼


* Choose Show labels for this layer 
* Label with - and choose what you want to show eg: Name, Values   
* You can change the font, size, colour - again you can match this to house style 
* Buffer tab can be useful to make the text stand out from the background 

￼

If you have chosen names, you will see that they don't all show up on a wide view. There are ways to manually change the placing  - more details here http://docs.qgis.org/2.0/ca/docs/training_manual/vector_classification/label_tool.html




TIP my shape file is too detailed  - MAPSHAPER *****************

Further reading
GIS stack exchange
FT man’s videos

