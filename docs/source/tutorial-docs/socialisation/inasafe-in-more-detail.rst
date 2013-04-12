InaSAFE in more detail
======================

Interrogating the output data
-----------------------------

You will now have 3 layer that have been generated through InaSAFE

* 2 - �Population which need evacuating� - Raster Data

* 1 - �Estimated building affected� - Vector Data

We are now going to use the basic QGIS tools to examine the datasets. 


About Estimate building affected
................................

#. Zoom into a section of buildings using the zoom in tool

Here we have zoomed into 2 rivers going through the middle of Jakarta.


Note: that the red buildings are situated in water greater than 1 meter and the green building are determined not affected as they are in waters less than 1 meter deep.
Click once on �Estimate buildings affected�  to make sure layer is highlighted in blue
Click on the information tool
Click on an affected building (red)
Here I clicked on the building circled in the above picture to result is below.  This buildings has a lot of information recorded about it.
Note: As mentioned before, this information was gathered by the Provincial disaster managers, through an OpenStreetMap  data collection program.  They collect important structures and essential information about the building, such as name, address, type and building structural information.  Also included was if the building had roof access.
Zoom back to full extent using the Zoom Full tool 
About Population which Needs evacuation
Uncheck the �Estimated buildings affected� and recheck one of  �Population which Need evacuation�
Again zoom into an area of your choice
Click once on �Population which Need evacuation� and use the selection tool to select a pixel (square)
Here I clicked on the light green area, to find that there is a value of 80.6411, which means there are approximately 80 people in one pixel (square). 
In this dataset a pixel is 100m by 100m
Click on other pixels to find out their value.
Click Close
Is each pixel really 100m by 100m, lets check. Use the measure line tool
Note: it maybe easier to measure one pixel by zooming in further.
The answer is yes, a pixel is 100 meter across, and if you measure from top to bottom it will also be 100 meter.
As you can see I got 102 meters but this is only because its very hard to click on one corner of the pixel and then the other, unless I zoom in real close!
Click Close
Zoom back to full extent using the Zoom Full tool
Uncheck all layers except
buildings
people 
Flood footprint in InaSAFE
Adding a vector layer
Click on the Add vector tool
Click on browse and navigate to InaSAFE projects/data/ and select flood_osm_bpbd18113_jakarta.shp - click Open, then click Open again.
This dataset is the subvillage boundaries for Jakarta, during the floods in January this year the Provincial disaster mangers collected information about the flooding, one of which was the location of the flooded area by sub-village boundary.
Lets examine this data by opening up its attribute table
In the layer list Right click on the flood_osm_BPBD18113_jakarta layers  and select �Open Attribute Table�
OBJECTID: 	Feature ID
KAB_NAME:  District
KEC_NAME:  Sub-district
KEL_NAME:  Village
RW: 		Sub-village
affected:    	1= affected,              	                            	     NULL = not affected
Close the Attribute table
Symbolising Vector
Now we are going to colour only the area that were affected
Double click on flood_osm_BPBD18113_jakarta layers - this will open up the properties table
Make sure you are on the style tab
Select Categorised
Select attribute from the Column
Click on Classify (circle 1)
Click on �0�  (circle 2)
Click Delete (circle 3)
Click on  �_� (circle 4)
Click Delete  (circle 3)
Confirm that you only have 1 left
Click OK (circle 6)
Below are the results
You have now symbolised your first layer!  You can see only the subvillage areas that were flooded on the 18th of January! Now, can we use this hazard layer in InaSAFE?
Adding Keywords
Read through the error message (that occurs when you highlight flood_osm_BPBD18113_jakarta layer).  InaSAFE has identified that the layer does not have a keyword file.  As explained on page 10.
Click on the keyword editor
Fill out the title as �Jakarta flooding on the 18th January 2013�
For the Category check Hazard
For Subcategory select flood[wet/dry]
Click OK
Lets run InaSAFE again with this new flood hazard footprint
Buildings within affected subvillages
Check that InaSAFE has the following in the drop-down boxes
Jakarta flooding on the 18th January 2013
buildings
Be Flooded
Click Run
Note: This may take about a minute to run
How many estimated buildings were flooded?
AnsweR  __________________________
Take some time to examine the results, read through the InaSAFE window
Click InaSAFE Print, save accordingly
Now that you have run InaSAFE to find out �how many buildings might be affected�, lets find out how many people.
Evacuation as a percentage
Note: We were able to determine how many people needed to be evacuate in the last scenario by specifying how deep the water had to be for the location to be determined unsafe.  However when you don�t know how deep the water is and you only know the flooded area, it is hard to determine how many people will need evacuating. InaSAFE therefore needs your help!
Instead of determining how many people will be evacuated by  a spatial area, this scenario used the affected population. InaSAFE asks the user to input a percentage of the affected population that could be evacuated.
Un-check buildings in the layer panel and recheck people
Check that InaSAFE has the following in the drop-down boxes
Jakarta flooding on the 18th January 2013
people
Need Evacuation
Click on the impact function editor (pencil)
As you can see the default is 1, Click OK
Run InaSAFE
Note: This may take about a minute to run
How many people were evacuated?
AnsweR  __________________________
How many people were affected?
AnsweR  __________________________
Take some time to examine the results, read through the InaSAFE window
Click InaSAFE Print, save accordingly
Comparing Results - Optional
You have now completed the following runs
Hazard	Threshold	Data Type	Exposure	Data Type	Impact function	Data Type
flood model	1.0m	Raster	People	Raster	Need Evacuation	
flood model	0.8m	Raster	People	Raster	Need Evacuation	
flood model	1.0m	Raster	Buildings	Vector	Be flooded	
flood 180113		Vector	Buildings	Vector	Be flooded	
flood 180113	1%	Vector	People	Raster	Need Evacuation	
Please complete the Data Type for each impact layer you have created through InaSAFE
Compare between results, 1. How different are the results, 2 Why are they different?
1. AnsweR  _____________________________________________________________
2. AnsweR  _____________________________________________________________
