# Exercise-1: Working with Geometric Objects

This week we will practice how to create geometric objects using Shapely module and how to find out different useful attributes from those geometries.
We will also take advantage of what we have learned earlier, specifically functions, that you should use for making different GIS operations easier to use 
in the future. We will also use numpy to read data from a file.
   
## Sections

 - Problem 1: Creating basic geometries
 - Problem 2: Attributes of geometries 
 - Problem 3: Reading coordinates from a file and creating a geometries out of them

## Problem 1: Creating basic geometries

Write your codes into a single `create_geometries.py` -file and upload the script to your personal GitHub Exercise-1 repository.

1. Create a function called `createPointGeom()` that has two parameters (x_coord, y_coord). Function should create a shapely Point geometry object and return that. 
Demonstrate the usage of the function by creating Point -objects with the function.

2. Create a function called `createLineGeom()` that takes a list of Shapely Point objects as parameter and returns a 
LineString object of those input points. Function should first check that the input list really contains Shapely Point(s). 
Demonstrate the usage of the function by creating LineString -objects with the function.

3. Create a function called `createPolyGeom()` that takes a list of coordinate tuples **OR** a list of Shapely Point objects and creates/returns 
a Polygon object of the input data. Both ways of passing the data to the function should be working. 
Demonstrate the usage of the function by passing data first with coordinate-tuples and then with Point -objects.

## Problem 2: Attributes of geometries

Write your codes into a single `read_attributes.py` -file and upload the script to your personal GitHub Exercise-1 repository.

1. Create a function called `getCentroid()` that takes any kind of Shapely's geometric -object as input and returns a centroid of that geometry. Demonstrate the usage of the function.

2. Create a function called `getArea()` that takes a Shapely's Polygon -object as input and returns the area of that geometry. Demonstrate the usage of the function.

3. Create a function called `getLength()` takes either a Shapely's LineString or Polygon -object as input. Function should check the type of the input and returns the length of 
the line if input is LineString and length of the exterior ring if input is Polygon. If something else is passed to the function, 
it should tell the user --> `"Error: LineString or Polygon geometries required!"`.  Demonstrate the usage of the function.

## Problem 3: 

One of the "classical" problems in GIS is the situation where you have a set of coordinates in a file and you need to get them into a map (or into a GIS-software). Python is a really handy
tool to solve this problem as with Python it is basically possible to read data from any kind of input datafile (such as csv-, txt-, excel-, or gpx-files (gps data) or from different databases). 
So far, I haven't faced any kind of data or file that would be impossible to read with Python. 

Thus, let's see how we can read data from a file and create Point -objects from them that can be saved e.g. as a new Shapefile (we will learn this next week). 
Our dataset **[travelTimes_2015_Helsinki.txt](data/travelTimes_2015_Helsinki.txt)** consist of 
travel times between specific locations in Helsinki Region. Our data looks like this:

```
   from_id;to_id;fromid_toid;route_number;at;from_x;from_y;to_x;to_y;total_route_time;route_time;route_distance;route_total_lines
   5861326;5785640;5861326_5785640;1;08:10;24.9704379;60.3119173;24.8560344;60.399940599999994;125.0;99.0;22917.6;2.0
   5861326;5785641;5861326_5785641;1;08:10;24.9704379;60.3119173;24.8605682;60.4000135;123.0;102.0;23123.5;2.0
   5861326;5785642;5861326_5785642;1;08:10;24.9704379;60.3119173;24.865102;60.4000863;125.0;103.0;23241.3;2.0
```

Thus we have many columns of data, but the few important ones are:


| Column | Description |
|--------|-------------|
| from_x | x-coordinate of the **origin** location (longitude) |
| from_y | y-coordinate of the **origin** location (latitude) |
| to_x   | x-coordinate of the **destination** location (longitude)|
| to_y   | y-coordinate of the **destination** location (latitude) |
| total_route_time | Travel time with public transportation at the route |

1. 