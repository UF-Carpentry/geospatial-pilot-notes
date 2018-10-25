Welcome to The Carpentries Etherpad!

This pad is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

Use of this service is restricted to members of the Software Carpentry and Data Carpentry community; this is not for general purpose use (for that, try etherpad.wikimedia.org).

Users are expected to follow our code of conduct: [https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html](https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html)

All content is publicly available under the Creative Commons Attribution License: [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

Link to workshop page: [https://uf-carpentry.github.io/2018-10-23-ufii-geospatial/](https://uf-carpentry.github.io/2018-10-23-ufii-geospatial/) 

Hello everyone! Justin starts the workshop at 9:02 AM

Our first break will take place after Lesson 4, around 10:30 AM
Break got out at 10:45 and got back at 10:55 AM

**<u>Day 1</u>**
_Introduction to R for Geospatial Data_

The National Ecological Observatory Network (NEON) [https://www.neonscience.org/](https://www.neonscience.org/)
UF's connection to NEON [http://ordway-swisher.ufl.edu/NEON.aspx](http://ordway-swisher.ufl.edu/NEON.aspx)

We will be working with R through the R Studio GUI

**Basic layout of R Studio is as follows:**
When you first open RStudio, you will be greeted by <u>three</u> panels:

1.  1.  The interactive R console (entire left)
    2.  Environment/History (tabbed in upper right)
    3.  Files/Plots/Packages/Help/Viewer (tabbed in lower right)

If you get a plus sign (+) in the console than R is waiting for you to "finish your sentence"
Ctrl Enter on Windows or Command Return on Mac

Remember PEMDAS?
When using R as a calculator, the order of operations is the same as you would have learned back in school.
From highest to lowest precedence:

*   Parentheses: (, )
*   Exponents: ^ or **
*   Divide: /
*   Multiply: *
*   Add: +
*   Subtract: -

Code reproducability is key, write it for other people in mind. Your colleagues, other scientitsts will need to be able to understand what each line of code does
We can comment our code by using # before your comment

There's a lot out there about R
Don’t worry about trying to remember every function in R. 
You can look them up on Google, or if you can remember the start of the function’s name, use the tab completion in RStudio.
This is one advantage that RStudio has over R on its own, it has auto-completion abilities that allow you to more easily look up functions, their arguments, and the values that they take
I love using the autocomplete because it limits any typing mistakes I may make  

The exciting part of R starts now! Let's assign a valuable to a variable as follows:
x <-1/40
We are assigning the value 1/40 using the assignment operator (<-) to x

Your first Challenge Question of the workshop!
Challenge 1
What will be the value of each variable after each statement in the following program?
mass <- 47.5
age <- 122
mass <- mass * 2.3
age <- age - 20

Please do not use the = sign for variable assignment. Use <-
Variables cannot start with a number, space, or special character
Consistency is key, Geraldine and I like to use underscores. 
There are functions that have periods in the name which may complicate things. 
Do not name a variable a TRUE or FALSE

<u>Project Management with RStudio</u>
Another beneift of using RStudio is be able to use Projects to keep all things well-organized and reproducible 
Save your raw data in a seperate folder and never alter it
You can have a document folder, a cleaned data folder, output, scripts folders, etc. 
Keep related data together
Since this is a geospatial workshop, a special NOTE:
Some GIS file formats are really 3-6 files that need to be kept together and have the same name, e.g. shapefiles. 
It may be tempting to store those components separately (like saving them by extension), but your spatial data will be unusable if you do that.

We can make folders in R using "New Folder" in the bottom right pane 

[http://datacarpentry.org/r-intro-geospatial/02-project-intro/index.html](http://datacarpentry.org/r-intro-geospatial/02-project-intro/index.html)

This is how your working directory should look once you have downloaded today's data called nordic-data.csv, nordic-data-2.csv, and gapminder_data.csv
 data/
    gapminder_data.csv
    NEON-DS-Airborne-Remote-Sensing/
    NEON-DS-Landsat-NDVI/
    NEON-DS-Met-Time-Series/
    NEON-DS-Site-Layout-Files/
    NEON-DS-Airborne-Remote-Sensing.zip
    NEON-DS-Landsat-NDVI.zip
    NEON-DS-Met-Time-Series.zip
    NEON-DS-Site-Layout-Files.zip
    nordic-data.csv
    nordic-data-2.csv

Some key points to review for this lesson:

1.  1.  Use RStudio to create and manage projects with consistent layout.
    2.  Treat raw data as read-only.
    3.  Treat generated output as disposable.
    4.  Geraldine recommends keeping your scripts seperate (one for data download, one for calculations, one for analysis) (Geraldine has seen my scripts, RIP)

#

<u>Data Structures in R</u>
### Remember to comment on your scripts
Let us read in the nordic data using the function read.csv()
What is $ used for in R? $ is a special operator where you are pulling out a specific column in a data frame. Then you can do vector operation on this  

We are using read.csv in this workshop. There is something called read_csv found in the reader package. 
read.csv is found in the base package of R
all data in R is interpreted a specific data class
R cannot mix up data types in the same column, R will make a choice for you to turn the whole column a certain data class 
Data frames are the first data structures. This combination of data classes is a dataframe. Data frames have a lot of vectors 

Vectors only have one data type.
We will create an empty vector and fill it with data
my_vector <- vector(length = 3)
This reads: make me a vector called "my vector" of length 3. 

The coercion hierarchy is as follows
logical -> integer -> numeric -> complex -> character, where -> can be read as _are transformed into_. 
You can try to force coercion against this flow using the as. functions

Challenge 2
Start by making a vector with the numbers 1 through 26\. Multiply the vector by 2.
The : operator creates a sequence of numbers from the left element to the right.

Lunch is scheduled for 12:30 to 1:30

In five minutes, do Challenge Question 3
Is there a factor in our nordic data frame? what is its name? Try using ?read.csv to figure out how to keep text columns as character vectors instead of factors; then write a command or two to show that the factor in nordic is actually a character vector when loaded in this way.

Lesson 4 started at 11:35 AM

We can add  a  new column via:
cbind(gapminder, below_average)
Where we created a vector called below_average as follows:
    below_average <- gapminder$lifeExp < 70.5

Use rbind to append to a dataframe 

Skipping Lesson 5\. If you are interested in manipulating data frames in R without using dplyr, you can follow the lesson here [https://datacarpentry.org/r-intro-geospatial/05-data-subsetting/index.html](https://datacarpentry.org/r-intro-geospatial/05-data-subsetting/index.html)
Joe starts Lesson 6 at 12:00 PM

Lesson 6: [https://datacarpentry.org/r-intro-geospatial/06-dplyr/index.html](https://datacarpentry.org/r-intro-geospatial/06-dplyr/index.html) 

library(dplyr)
library(ggplot2)

You may need to install the packages:
    install.packages(c("dpylr","ggplot2")) 

Read in the data:
    gapminder <- read.csv("data/gapminder_data.csv)

Calculate the average GDP by continent  (the base R way):
    mean(gapminder[gapminder$continent == "Africa", "gdpPercap"])
    mean(gapminder[gapminder$continent == "Americas", "gdpPercap"])
    mean(gapminder[gapminder$continent == "Asia", "gdpPercap"])

The problem with this approach is that it's not very efficent, prone to typos, and hard to read unless you really understand R

The select() verb

In dplyr, the selec() function is used for selecting specific columns in your dataframe

year_country_gdp <- select(gapminder, year, country, gdpPercap)

## Piping 

We can create a "pipe" using %>%

*   For shortcut use CTRL+SHIFT+M in Windows or CMD+SHIFT+M in Mac
*   The pipe takes whatever is on the left-sde of the pipe and puts into the first argument on the next function
*   This is very useful for stringing together functions

# The filter() function

The filter() functions works similarly to select(), but it operates on rows rather an columns, and we can use some logical conditions to subset the rows
year_country_gdp_euro <- gapminder %>%
  filter(continent == "Europe") %>%
  select(year, country, gdpPercap)

  Joe skipped arrange() dplyr verb

Welcome back!

group_by()
group data frame by column before performing an action

gapminder %>% group_by(continent) %>% str()

summarize()
combined with group_by(), returns calculation (e.g., mean) based on each group

gdp_bycontinents <- gapminder %>% group_by(continent) %>% summarize(mean_gdpPercap=mean(gdpPercap))

tibbles are just like data frames, but are specific to the tidyerse packages (dplyr, tidyr, ggplot, etc...) 
they are optimized to work well with the functions in these packages.
they look a little different but they work essentially the same way as data frames, and you can convert back and forth between the two formats
as.data.frame(tibble) converts a tibble into a data frame

Find average life expectancy per country:
lifexp_percountry <- gapminder %>% group_by(country) %>% summarize(mean_lifeExp=mean(lifeExp))
Which are the min and max?
lifexp_percountry %>% filter(mean_lifeExp==min(mean_lifeExp) | mean_lifeExp==max(mean_lifeExp))

gdp_bycontinents_byyear <- gapminder %>% group_by(continent, year) %>% summarize(mean_gdpPercap=mean(gdpPercap))

do more than one summary statistics
gdp_bycontinents_byyear <- gapminder %>% group_by(continent, year) %>% summarize(mean_gdpPercap=mean(gdpPercap), sd_gdpPercap=sd(gdpPercap), mean_pop=mean(pop), sd_pop=sd(pop))

How many observations in each grouop?

count()

gapminder %>% filter(year=2002) %>% count(continent, sort=TRUE)

n()

gapminder %>% group_by(continent) %>% summarize(se_le=sd(lifeExp)/sqrt(n())

Create new columns in the tibble/data frame

mutate()

gdp_pop_bycontinents_byyear <- gapminder %>% mutate(gdp_billion=gdpPercap*pop/10^9) %>% group_by(continent, year) %>% summarize(mean_gdpPercap=mean(gdpPercap), sd_gdpPercap=sd(gdpPercap), mean_pop=mean(pop), sd_pop=sd(pop), mean_gdp_billion=mean(gdp_billion), sd_gdp_billion=sd(gdp_billion))

### Intro to visualization ###
2:05 pm

load package ggplot2
library(ggplot2)

ggplot2 works by layering. first, you define what data you're using and the aesthetics, where you specify what you want to plot on each axis.
Then, you can add things to the plot by adding layers with plus signs. 

Plot histogram of life expectancy

ggplot(data=gapminder, aes(x=lifeExp)) + geom_histogram()

Plot histogram of gdp per capita

ggplot(data=gapminder, aes(x=gdpPercap)) + geom_histogram()

Plot barplot of gdp per capita by country

gapminder_small <- filter(gapminder, year==2007, continent=="Americas")

ggplot(data=gapminder_small, aes(x=country, y=gdpPercap)) +
geom_col()

Can't read the x axis! We can fix this.

ggplot(data=gapminder_small, aes(x=country, y=gdpPercap)) +
geom_col() +
coord_flip()

gapminder_small_2 <- gapminder %>% filter(continent=="Americas", year %in% c(1952, 2007))

ggplot(gapminder_small_2, aes(x=country, y=gdpPercap, fill=as.factor(year))) +
geom_col(position="dodge") +
coord_flip()

### Exporting
Started at 2:25

Save as pdf
pdf("Distribution-of-GDP.pdf", width=12, height=4) # specify file name, type, and size
# code for the plot goes in the middle
ggplot(data=gapminder, aes(x=gdpPercap)) + 
geom_histogram()
# at the end, close the pdf exporting device
dev.off()

Also check out the ggsave() function!

# # # # # # # # #  Intro to geospatial concepts  # # # # # # # # # #
Started at 2:55

# Raster data

Advantages / disadvantages of raster data. Brainstorming! 

+ Lots of information at high resolution
+ You can do calculations
+ ...

- Huge files
- Sometimes difficult to embed metadata
- ...

-- Spatial extent is the overall geographic coverage of the spatial object of interest. You can think of it as the rectangle that delimits the area of interest
-- Resolution is the grain, the level of detail at which our data are available. Cell size defines the resolution
-- CRS = coordinate reference system
-- NoDataValue = how the absence of data is represented

All these information should be contained in the metadata of a raster file

Multi-band raster data can be either rasters for the same area on different spectrum bands, or for the same area at different times

Joe finished at 3:02
Kristina started at 3:17 geospatial concepts second lesson (vector)

3 kinds of vector data types
point data >> each element is a point (luke the location of the center of a tree), with coordinates 
lines >> are lines connecting points (minum of 2 points)
polygons >> at least 3 points, and have an extra feature: the area (an example of a polygon is a basin, a lake, a pond)

vector data are more efficient than raster; not as spacially extensive
raster  have information for each single pixel, vector information per object
each shapefile contain just one type of vector data

Started CRS at 3:28 PM
each spatial data has coordinates and a coordinate reference system associated to them

CRS information has three components:

*   **Datum:** A model of the shape of the earth. It has angular units (i.e. degrees) and defines the starting point (i.e. where is (0,0)?) so the angles reference a meaningful spot on the earth. Common global datums are WGS84 and NAD83\. Datums can also be local - fit to a particular area of the globe, but ill-fitting outside the area of intended use. In this workshop, we will use the <u>WGS84 datum</u>.

A common analogy employed to teach projections is the orange peel analogy. If you imagine that the earth is an orange, how you peel it and then flatten the peel is similar to how projections get made.
A datum is the choice of fruit to use. Is the earth an orange, a lemon, a lime, a grapefruit?

*   **Projection:** A mathematical transformation of the angular measurements on a round earth to a flat surface (i.e. paper or a computer screen). The units associated with a given projection are usually linear (feet, meters, etc.). In this workshop, we will see data in two different projections.
*   **Additional Parameters:** Additional parameters are often necessary to create the full coordinate reference system. One common additional parameter is a definition of the center of the map. The number of required additional parameters depends on what is needed by each specific projection.

A PROJ4 string includes the following information:

*   **proj=:** the projection of the data
*   **zone=:** the zone of the data (this is specific to the UTM projection)
*   **datum=:** the datum used
*   **units=:** the units for the coordinates of the data
*   **ellps=:** the ellipsoid (how the earth’s roundness is calculated) for the data
*   towgs84=: Datum transformation to WGS84\. Datum shifts can be approximated by 3 parameter spatial translations (in geocentric space), or 7 parameter shifts (translation + rotation + scaling). The parameters to describe this can be described using the **towgs84** parameter.

Kristina started [https://datacarpentry.org/organization-geospatial/04-geo-landscape/index.html](https://datacarpentry.org/organization-geospatial/04-geo-landscape/index.html) at 3:45 and ended at 3:50 (nice!!)
ArcGIS, Google Earth, QGIS used my most of the people at today's workshop 

GIS programming moving more towards CLI (command line interface) and away from GUI. 

Benefits of using a GUI include:

*   Tools are all laid out in front of you
*   Complex commands are easy to build
*   Don’t need to learn a coding language
*   Cartography and visualisation is more intuitive and flexible

Downsides of using a GUI include:

*   Low reproducibility - you can’t record your actions and replay
*   Most are not designed for batch-processing files
*   Limited ability to customise functions or write your own
*   Intimidating interface for new users - so many buttons!

*   sf for working with vector data
*   raster for working with raster data
*   rgdal for an R-friendly GDAL interface

Introduction to Geospatial Raster and Vector Data with R
[https://datacarpentry.org/r-raster-vector-geospatial/](https://datacarpentry.org/r-raster-vector-geospatial/)

Start at 3:50

If you need to install the libraries, run: 
    install.packages(c("dplyr", "ggplot2", "raster", "rgdal", "rasterVis", "sf"))

Data Tip - Object names
To improve code readability, file and object names should be used that make it clear what is in the file. The data for this episode were collected from Harvard Forest so we’ll use a naming convention of datatype_HARV

After running summary() you get this warning message for large datasets 
Warning in .local(object, ...): summary is an estimate based on a sample of 1e+05 cells (4.31% of all cells)

but note the warning - unless you force R to calculate these statistics using every cell in the raster, it will take a random sample of 10,000 cells and calculate from that instead. 
To force calculation on more, or even all values, you can use the parameter maxsamp:

summary(DSM_HARV, maxsamp = ncell(DSM_HARV))

You may not see major differences in summary stats as maxsamp increases, except with very large rasters.

ggplot only works on dataframes, so we need to coerce our raster layer into a dataframe. We learned about dataframes in an earlier lesson. The raster package has an built-in function for conversion to a plotable dataframe.

Dealing wwith missing data
Using GDALinfo()  we saw the NoDataValue was -9999
Bad data is different than missing data 
Bad data values are values that fall outside of the applicable range of a dataset.
Examples of Bad Data Values:

*   The normalized difference vegetation index (NDVI), which is a measure of greenness, has a valid range of -1 to 1\. Any value outside of that range would be considered a “bad” or miscalculated value.
*   Reflectance data in an image will often range from 0-1 or 0-10,000 depending upon how the data are scaled. Thus a value greater than 1 or greater than 10,000 is likely caused by an error in either data collection or processing

Kristina finished Intro to Raster Data in R at 4:32
Justin collecting minute cards and reminded people to fill out pre-survey 

### Second Day ###
3 no-shows today and 3 late from class before
Intro and Recap for the day ended at 9:23
Kristina begins Lesson 2 "Plot Raster Data in R" at 9:25

ggplot is a flexible plotting package (even placing one raster on top of another!)
DSM digital surface model from NEON Harvard Field Site

Difference between DSM, DTM, and CHM 
[https://www.earthdatascience.org/images/courses/earth-analytics/lidar-raster-data-r/lidarTree-height.png](https://www.earthdatascience.org/images/courses/earth-analytics/lidar-raster-data-r/lidarTree-height.png)

We might prefer to customize the cutoff values for the DSM plot. We round the cutoff values so that we have groups for the ranges of 300-349m, 350 - 399m, and 400-450m. 
To implement this we need to give mutate() a numeric vector of break points instead of the number of breaks we want, which is why we needed cut() to break it for us

Some good discussion on why we are grouping into three groups. Using ggplot() below
ggplot() +
    geom_bar(data = DSM_HARV_df, aes(fct_elevation))
We saw the distribution of the data. The majority of the data lies in the middle, or medium, bin of the bar plot
Curious about the cutoffs, we used unique()
unique(DSM_HARV_df$fct_elevation)
Where fct_elevation was the new variable we created using mutate() above

After exploring the data, we realize we could use more reasonable cutoffs
custom_bins <- c(300, 350, 400, 450)
Since we have just classifed our bins we can now cut() using this data object as the break argument 
Note that when we assign break values a set of 4 values will result in 3 bins of data.That's why custom bins had 4 elements (300, 350, 400, and 450)
The bin intervals are shown using ( to mean inclusive, and ] to mean exclusive. For example: (305, 342] means “from 305 through 341”.

For those joining us we are working from [https://datacarpentry.org/r-raster-vector-geospatial/02-raster-plot/index.html](https://datacarpentry.org/r-raster-vector-geospatial/02-raster-plot/index.html)

What is coord_quickmap(), it is a quick and approximate Mercator projection for our plots
 terrain.colors() returns a number of hex values for possible colors you can choose from. Putting terrain.colors() into ggplot's scale_fill_manual () function, it will set the colors to those you've specified 

theme() is a useful ggplot function. Tons of arguments that can be used to customize your plot like you want them to look

First Challenge Question of the day (10:00 AM): Plot Using Custom Breaks
Create a plot of the Harvard Forest Digital Surface Model (DSM) that has:

1.  1.  Six classified ranges of values (break points) that are evenly divided among the range of pixel values.
    2.  Axis labels.
    3.  A plot title.

### Layering Rasters (10:15 AM)
Remember that in order to plot a raster in ggplot is that you actually need to convert it into a dataframe
Using the same naming convention as before, we add _df to the end to remind ourselves (and our collaborators!) that this is a dataframe 
We are interested in geospatial data, so mak sure to set xy=TRUE

DSM_hill_HARV_df <- as.data.frame(DSM_hill_HARV, xy = **TRUE**) 
str(DSM_hill_HARV_df)

###  Lesson 3 at 10:55
We are using projectRaster() from the raster package because the two layers ae a differenct CRS
Check resolutions using res()
And extent with extent()
We saw that resolutions were still slightly different. So by adding in the res function we can fix this (now both will have a resolution of 1 X 1 )
DTM_hill_UTMZ18N_HARV <- projectRaster(DTM_hill_HARV,
                                  crs = crs(DTM_HARV),
                                  res = 1)

Skipping 
Challenge: Explore CHM Raster Values
### Moved on to Raster Calculations in R at 11:20
DSM - DTM = CHM
Since they're set to the same extent and resolution we can do raster math. Remember to think of these datasets like grids with numbers inside each grid cell. If everything aligns, we can subtract,add,etc.
The other way we can make a CHM is by using the overlay() function. Overlay is a good choice when 

1.  The rasters we are using are larger in size.
2.  The rasters are stored as individual files.
3.  The computations performed are complex.

The syntax is
outputRaster <- overlay(raster1, raster2, fun=functionName), where fun is the function we want to use 
A note on overlay, if you're working witrh RasterStacks or RasterBricks then overlay() is not for you. Try calc() instead

CHM<- overlay (raster1, raster2, fun=  functionName)
We've been using pre-made functions over the last two days. Let's make our own function!
function(variable1, variable2){WhatYouWantDone, WhatToReturn}
function(r1, r2){return(r1-r2)}, where the r's are our raster datasets 

writeRaster() Options
The function arguments that we used above include:

*   **format:** specify that the format will be GTiff or GeoTIFF.
*   **overwrite:** If TRUE, R will overwrite any existing file with the same name in the specified directory. USE THIS SETTING WITH CAUTION!
*   **NAflag:** set the GeoTIFF tag for NoDataValue to -9999, the National Ecological Observatory Network’s (NEON) standard NoDataValue.

San Joaquin Challenge at bottom of Lesson 4 begins at 11:45 AM

Simona starts at 12:00 PM
We are skipping Multi-band rasters but you can complete the lesson on your own time here [https://datacarpentry.org/r-raster-vector-geospatial/05-raster-multi-band-in-r/index.html](https://datacarpentry.org/r-raster-vector-geospatial/05-raster-multi-band-in-r/index.html)
Lunch at 45 minutes and not an hour 

Import your Area of Interest (AOI)
aoi_boundary_HARV <- st_read(
  "data/NEON-DS-Site-Layout-Files/HARV/HarClip_UTMZ18.shp")
Think of the bbox like the extent of the polygon area of interest 

ggplot and sf are optimized to work well together. We will be using ggplot to plot our vector data

### color is for the outline, fill is the inside color of the polygon
### The equivalent for coord_quickmap is coord_sf which defines the coordinate system of the plot 
ggplot() + 
  geom_sf(data = aoi_boundary_HARV, size = 3, color = "black", fill = "cyan1") + 
  ggtitle("AOI Boundary Plot") + 
  coord_sf()

Challenge: Import Line and Point Shapefiles assigned at 12:10 PM

What does no_defs mean? From a StackExchange answer:
[https://lists.osgeo.org/pipermail/mapserver-users/2003-November/046863.html](https://lists.osgeo.org/pipermail/mapserver-users/2003-November/046863.html)

Simona starts Vector Lesson 7
We used nrow(), head(), names(), and ncol() to interrograte this data too
Assigns Challenge Question at 12:22 PM

Challenge: Attributes for Different Spatial Classes
Explore the attributes associated with the point_HARV and aoi_boundary_HARV spatial objects.

1.  How many attributes does each have?
    1.  Use ncol()
2.  Who owns the site in the point_HARV data object?
    1.  Use the $ operator, 
    2.  point_HARV$Ownership
3.  Which of the following is NOT an attribute of the point_HARV data object?
    1.  A) Latitude B) County C) Country

*   Use names() to find out 

We can apply dplyr to this data!
footpath_HARV <- lines_HARV %>% 
  filter(TYPE == "footpath")nrow(footpath_HARV)

Last Challenge before lunch 
Subset out all boardwalk from the lines layer and plot it.

Lunch starts at 12:40 
Lunch ends 1:25

Simona uses levels() to find the types of roads
She builds a vector of road colors 
Then for the scale_color_manual function she specifies values= road_colors, road_colors being the vector she created

ggplot() +
  geom_sf(data = lines_HARV, aes(color = TYPE)) + 
  scale_color_manual(values = road_colors) +
  labs(color = 'Road Type') +
  ggtitle("NEON Harvard Forest Field Site", subtitle = "Roads & Trails") + 
  coord_sf()

Using theme(), Simona wants to specify two details of how the plot will look like. Specifically, 

*   legend.text: change the font size
*   legend.box.background: add an outline box

New vector of colors:
     new_colors <- c("springgreen", "blue", "magenta", "orange")

CHALLENGE:
    Create a plot that emphasizes only roads where bicycles and horses are allowed. To emphasize this, make the lines where bicycles are not allowed THINNER than the roads where bicycles are allowed. NOTE: this attribute information is located in the lines_HARV$BicyclesHo attribute.
Be sure to add a title and legend to your map. You might consider a color palette that has all bike/horse-friendly roads displayed in a bright color. All other lines can be black.

Simona creates a new object lines_removeNA that removes missing values. She does thus by using the function na.omit, and some of the operators we learned yesterday [] and $
lines_removeNA <- lines_HARV[na.omit(lines_HARV$BicyclesHo),]

##### Plot Multiple Shapefiles in R at 1:45 PM
[https://datacarpentry.org/r-raster-vector-geospatial/08-vector-plot-shapefiles-custom-legend/index.html](https://datacarpentry.org/r-raster-vector-geospatial/08-vector-plot-shapefiles-custom-legend/index.html)

Challenge Question Assigned at 2:02 PM
Plot Polygon by Attribute

1.  Using the NEON-DS-Site-Layout-Files/HARV/PlotLocations_HARV.shp shapefile, create a map of study plot locations, with each point colored by the soil type (soilTypeOr). How many different soil types are there at this particular field site? Overlay this layer on top of the lines_HARV layer (the roads). Create a custom legend that applies line symbols to lines and point symbols to the points.
2.  Modify the plot above. Tell R to plot each point, using a different symbol of shape value.

We've overlayed shapefile on top of each other
And we did the same for raster data when Kristina was teaching
Simona will teach us how to overlay shapefiles on top of raster data as we work through this challenge activity together (2:20 PM)

Challenge: Plot Raster & Vector Data Together--> Order matters here, the raster goes first since you want it in the background. 
You can plot vector data layered on top of raster data using the + to add a layer in ggplot. 
Create a plot that uses the NEON AOI Canopy Height Model NEON_RemoteSensing/HARV/CHM/HARV_chmCrop.tif as a base layer. 
On top of the CHM, please add:

*   The study site AOI.
*   Roads.
*   The tower location.

Solution:
ggplot() +
  geom_raster(data = CHM_HARV_df, aes(x = x, y = y, fill = HARV_chmCrop)) +
  geom_sf(data = lines_HARV, color = "black") +
  geom_sf(data = aoi_boundary_HARV, color = "grey20", size = 1) +
  geom_sf(data = point_HARV, pch = 8) +
  ggtitle("NEON Harvard Forest Field Site w/ Canopy Height Model") + 
  coord_sf()

Handling Spatial Projection & CRS in R with Sergio
Start: 2:30
[https://datacarpentry.org/r-raster-vector-geospatial/09-vector-when-data-dont-line-up-crs/index.html](https://datacarpentry.org/r-raster-vector-geospatial/09-vector-when-data-dont-line-up-crs/index.html)

Sergio is using the st_read() function to import the /US-Boundary-Layers/US-State-Boundaries-Census-2014 layer into R. This layer contains the boundaries of all contiguous states in the U.S. 
DISCLAIMER: Please note that these data have been modified and reprojected from the original data downloaded from the Census website to support the learning goals of this episode.
"Never give up!"- Sergio 2:36 PM 10/24/2018

New ggplot layer (shapefile of country outline with bigger thickness) on top of a states layer below. Note the size argument in the country_boundary layer
ggplot() + 
  geom_sf(data = country_boundary_US, color = "gray18", size = 2) +
  geom_sf(data = state_boundary_US, color = "gray40") +
  ggtitle("Map of Contiguous US State Boundaries") + 
  coord_sf()

ggplot to the rescue! 
We saw in an earlier episode [https://datacarpentry.org/r-raster-vector-geospatial/03-raster-reproject-in-r/](https://datacarpentry.org/r-raster-vector-geospatial/03-raster-reproject-in-r/) that when working with raster data in different CRSs, 
we needed to convert all objects to the same CRS. 
We can do the same thing with our vector data - however, we don’t need to! 
When using the ggplot2 package, ggplot automatically converts all objects to the same CRS before plotting.
It’s still a good idea to be aware of your object CRSs and extents.

2:50 PM
Sergio reminds you to be consistent with your object-naming conventions. (don't mix underscores and periods in your object names)
Now for your turn, complete this challenge question 
Challenge - Plot Multiple Layers of Spatial Data
Create a map of the North Eastern United States as follows:

1.  Import and plot Boundary-US-State-NEast.shp. Adjust line width as necessary.
2.  Layer the Fisher Tower (in the NEON Harvard Forest site) point location point_HARV onto the plot.
3.  Add a title.
4.  Add a legend that shows both the state boundary (as a line) and the Tower location point.

Convert from .csv to a Shapefile in R
Start 2:55
[https://datacarpentry.org/r-raster-vector-geospatial/10-vector-csv-to-shapefile-in-r/index.html](https://datacarpentry.org/r-raster-vector-geospatial/10-vector-csv-to-shapefile-in-r/index.html)

Often times, we may want to use geopgrahic data that is store in a csv file 

plot_locations_HARV <-
  read.csv("data/NEON-DS-Site-Layout-Files/HARV/HARV_PlotLocations.csv")
str(plot_locations_HARV)

For this is work, we the dataframe must contain cooridinates, as well as a coordinate reference system (CRS)
There are several ways to figure out the CRS of spatial data in text format.
- We can check the file metadata in hopes that the CRS was recorded in the data.
- We can explore the file itself to see if CRS information is embedded in the file header or somewhere in the data columns.

Looking at the columns (using the names() function) we see that there is a column call 'utmZone'

*   head(plot_locations_HARV$utmZone)

This is our CRS: UTM 18N

It will be easier to set the reference system using the proj4 format:
    utm18nCRS <- st_crs(point_HARV)
    utm18nCRS

NOTE: Be careful when naming objects. It's a good idea to:
    - Always start with a cleared enviroment (no existing variable, use the little broom in the Environment tab)
    - Use the Tab autocomplete, especially for files and variables with long names
    - If possible, you should "source" your script, which will run all the code from beginning to end

plot_locations_sp_HARV <- st_as_sf(plot_locations_HARV, coords = c("easting", "northing"), crs = utm18nCRS)
st_crs(plot_locations_sp_HARV)

ggplot() + 
  geom_sf(data = plot_locations_sp_HARV) +
  ggtitle("Map of Plot Locations")

The extent defines the space around the spatial object, and what ggplot uses to determine the plot boundaries:
    extent(plot_locations_sp_HARV)

ggplot() + 
  geom_sf(data = aoi_boundary_HARV) + 
  geom_sf(data = plot_locations_sp_HARV) +
  ggtitle("AOI Boundary Plot")

Exporting shapefiles
We can write an R spatial object to a shapefile using the st_write function in sf. To do this we need the following arguments:

*   the name of the spatial object (plot_locations_sp_HARV)
*   the directory where we want to save our shapefile (to use current = getwd() or you can specify a different path)
*   the name of the new shapefile (PlotLocations_HARV)
*   the driver which specifies the file format (ESRI Shapefile)

We can now export the spatial object as a shapefile.
We've done the work to create a full geographic file, now let's save it as an actual shapefile:
    st_write(plot_locations_sp_HARV,
         "data/PlotLocations_HARV.shp", driver = "ESRI Shapefile")

Note that R doesn't like when you save over files that already exist, but you can use the argument delete_dsn = TRUE to override this behavior
End 3:15 10 minute break, starting up at 3:25 PM

Manipulate Raster Data in R
[https://datacarpentry.org/r-raster-vector-geospatial/11-vector-raster-integration/index.html](https://datacarpentry.org/r-raster-vector-geospatial/11-vector-raster-integration/index.html)

How can I crop raster objects to vector objects, and extract the summary of raster pixels?
The objectives for this lesson are to 

*   Crop a raster to the extent of a vector layer.
*   Extract values from a raster that correspond to a vector file overlay.

The reason why we need "Spatial" here
CHM_HARV_Cropped <- crop(x = CHM_HARV, y = as(aoi_boundary_HARV, "Spatial"))
Is because aoi_boundary is not a "Spatial" object, it's actually an sf object. We must coerce it into a "Spatial" object using as()

If you recall from Geospatial Concepts, we can think of extent as a bounding box encompassing the area between the N, S, E, and W corners of a feature. 
To get the boundary box from CHM, the st_bbox() will extract the 4 corners of the rectangle that encompass all the features contained in this object. 
The st_as_sfc() converts these 4 coordinates into a polygon that we can plot:

###We do not have a CHM_HARV_sp so please use CHM_HARV below 

That's why we have st_bbox() below:
CHM_HARV_Cropped_df <- as.data.frame(CHM_HARV_Cropped, xy = **TRUE**)
ggplot() +
  geom_sf(data = st_as_sfc(st_bbox(CHM_HARV)), fill = "green",
          color = "green", alpha = .2) +  
  geom_raster(data = CHM_HARV_Cropped_df,
              aes(x = x, y = y, fill = HARV_chmCrop)) + 
  scale_fill_gradientn(name = "Canopy Height", colors = terrain.colors(10)) + 
  coord_sf()

Challenge Question assigned 3:52
Challenge: Crop to Vector Points Extent

1.  Crop the Canopy Height Model to the extent of the study plot locations.
2.  Plot the vegetation plot location points on top of the Canopy Height Model.

ggplot() + 
  geom_sf(data = aoi_boundary_HARV, color = "blue", fill = **NA**) +
  geom_raster(data = CHM_HARV_manual_cropped_df,
              aes(x = x, y = y, fill = HARV_chmCrop)) + 
  scale_fill_gradientn(name = "Canopy Height", colors = terrain.colors(10)) + 
  coord_sf()

Extract Data using x,y Locations
You can use whatever summary statistic you're interested in by changing what you set fun= to
What is the average height of a tree within some area (bounding box)?
mean_tree_height_tower <- extract(x = CHM_HARV,
                                  y = as(point_HARV, "Spatial"),
                                  buffer = 20,
                                  fun = mean)  
The buffer concept relates to the fact that we want to extract from more than just the pixel before, we want to extract the pixel and those surrounding it in a 20m buffer
We didn't set df=TRUE because we are only interested in one value, the mean. 

For the last Challenge Activity, because we set df=TRUE we won't get only one number back
Challenge: Extract Raster Height Values For Plot Locations
1) Use the plot locations object (plot_locations_sp_HARV) to extract an average tree height for the area within 20m of each vegetation plot location in the study area. Because there are multiple plot locations, there will be multiple averages returned, so the df = TRUE argument should be used.
2) Create a plot showing the mean tree height of each area.
Skipping lessons 12, 13, and 14
Skipped last challenge, ended at 4:20

Justin starts outro at 4:22
Justin shows us some resources
The UF Carpentries Club [https://www.uf-carpentries.org/](https://www.uf-carpentries.org/)
The event page [https://uf-carpentry.github.io/2018-10-23-ufii-geospatial/](https://uf-carpentry.github.io/2018-10-23-ufii-geospatial/)
Post workshop survey [https://www.surveymonkey.com/r/dcpostworkshopassessment?workshop_id=2018-10-23-ufii-geospatial](https://www.surveymonkey.com/r/dcpostworkshopassessment?workshop_id=2018-10-23-ufii-geospatial)
The UF-specific survey [https://docs.google.com/forms/d/e/1FAIpQLScFy5oWZo7L32kwiXdImhXvq0Ab4xOnK3ZHEed-rbTYJg55Xg/viewform](https://docs.google.com/forms/d/e/1FAIpQLScFy5oWZo7L32kwiXdImhXvq0Ab4xOnK3ZHEed-rbTYJg55Xg/viewform)
