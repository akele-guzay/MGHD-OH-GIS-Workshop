# MGHD-OH-GIS-Workshop

![banner image](https://github.com/akele-guzay/MGHD-OH-GIS-Workshop/blob/main/pictures/banner.png)

In this hands on workshop, you will explore the concepts of Geographic Information Systems and use the free and open source QGIS software to create different vector elements as well as use public health data to create a compelling choropleth maps. 


# Pre-requisites

1. A laptop π»
2. Internet π©π½βπ»
3. [QGIS Software](https://www.qgis.org/en/site/forusers/download.html)
4. Mad Vibes π
---

## Case Scenario: Ebola Season π±ππ½ββοΈβοΈ

It is Ebola season in Uganda and the DRC. The Rwandan Biomedial Center (RBC) is exploring potential areas of disase introductio into Rwanda. They are looking at major boarder crossings between Rwanda and the two countries, as well as the major international airport in Kigali as potential sites for disease introduction. They have contacted you to map out some important structures within the airport to plan for case screening. They would like to see:

1. Two hand washing stations π§΄
2. Two paths for individuals to disembark a flight and walk along πΈ
3. Two buildings where travelers can be screened π’

---

### Activity 1: Creating the hand washing stations π§΄

``` markdown
*Initial steps* πͺ

- Launch QGIS
- Go into the Projects setting
  - General
    - Project file: GIS_Workshop
    - Prject home
    - Project title
    - Units for distance measurement: meters
  - CRS: `EPSG:3857`
- Add a basemap
  - `A basemap is a layer that provides geographical context to the map and other dataset
  layers above it.`
- Find the Kigali airport
```

``` markdown
    a) Create a folder in your desktop β QGIS course
    b) Creating a new layer
        1. layer β create layer β new shapefile layer
        2. layer information
            1. file name: hand_washing (make sure itβs in the QGIS course layer)
            2. geometry type: point
            3. Additional dimensions: Project CRS
            4. new field
                1. name: tap#
                2. type: integer (because rooms are full numbers)
                3. length: 2 (most likely wonβt go beyond single digit)
                4. click: add to fields layer
        3. Now you try adding two new fields
            1. soap?: text
            2. bld_date: date
    c) Now we have our layer, letβs add some hand washing points
        1. Click on the hand wash layer, in the layer view
        3. Toggle the editing icon β add point feature β you get a target 
        4. click on a spot outside some buildings
            1. pop up β fill in the information β click save
            2. how can we check the information we put in?
                1. Click on the βAttribute tableβ and view the information you entered
            3. Now, letβs say you want to add a new field,running_water, how can you do that?
                1. While in the attribute table view, toggle the edit mode (ctrl+e)
                2. find and click on βNew fieldβ (ctrl+w) then input the information
                    1. name: running_water; type: text β click save
                    2. In the edit mode, we can add information to the previous point we had entered 
                        1. Double click on the βNullβ box β type yes
                    3. Add two more points
                    4. to save changes: click on edit mode icon
        5. Save your file
        
```
        
### Activity 2: Paths for disembarking πΈ

``` markdown
    d) Creating a new layer
        1. layer β create layer β new shapefile layer
        2. layer information
            1. file name: paths
            2. geometry type: line string
            3. new field
                1. name: path_name
                2. type: string
                3. length: 10
                4. click: add to fields layer
    e) Now we have our layer, letβs add a short path
        1. Click on the road layer, in the layer view
        2. Toggle the editing icon β add line feature β you get a target 
        3. click on a path and add the feature; 
            1. When youβre done `Right Click` to remove the target
            2. then input the right information and click save
            3. exit editing mode and save changes to layer
        4. Click on the attribute table so we can see what we entered
        5. Letβs say you want to calculate the length of our paths β 2 ways to do this
            1. toggle the editing icon on attribute table view
               2. click `Open field calculator` (ctrl+i)
                  1. fill in the following info:
                    1. Output field name: length
                    2. output field type: decimal number (real)
                    3. Expression box: $length
                    4. press βOKβ
            2. Easy way for quick measurements
                1. click the βmeasure lineβ on top
                2. click along the line β write click when youβre done
                   a. Question: Whatβs the length of the runway?
                4. click on the βpan mapβ hand icon
```

#### Stylizing our wash points and paths π

``` markdown
    f) Letβs say we want to change the color of our wash points based on number of taps and the shape of the icons
        1. right click on the hand washing layer β properties β symbologies β categorized (this is for discreet values)β change value to `tap#` β click classify at the bottom β apply
        2. click Labels β single label β `tap#`
        3. Question: change the marker and color of the road and label it with βroad lengthβ   
```

### Activity 3: Selecting buildings for screening π’

``` markdown
    g) Reproduce the processes from before
    h) Fields
        1. bldg_name: string
        2. bldg_type: string
        3. door#: integer (32bit)
        4. window#: integer (32bit)
    i) trace the airport buildings with paths β right click when youβre done
    k) toggle editing button β save
```

### Knowledge bomb π£

``` markdown
**What we've been doing so far is called 'Digitizing'**
```

#### Changing basemaps via QuickMapServices πΊ

``` markdown
1οΈβ£ Plugins menu > Manage and Install Pluginsβ¦ 
    β’ Scroll down, or search all plugins for `quickmap` (you donβt need to type the whole name) 
    β’ Select the QuickMapServices plugin 
    β’ Click the `Install plugin` button (it installs in seconds) 
    β’ Click `Close` 
2οΈβ£ When you first install QuickMapServices, you'll want to get the full set of basemap definitions.
    β’ Web menu > QuickMapServices > Settings 
    β’ `More services` tab > `Get contributed pack`
3οΈβ£ To add the Google Satelite basemap, which combines aerial photos with place name labels:
    β’ Web menu > QuickMapServices > Google > Google Satellite
```

#### Tiny exercise ππ½ββοΈ

``` markdown
- Calculate the areas of the buildings in exchange for chocolate! π«π
```
---
## Case scenario 2: Air Pollution π€

The RBC is happy with your work so far and they would like to use your services to assess an alarming cluster of asthma cases in one of the districts. They have a suspicion that the cause of the asthma cases is the polution from heavy trucks using the main road that passes through the comminity. They have sent you a shape file containing the a number of households along a section of the road. They would like for you to identify and isolate the houses within 50 meters of the main road. 

#### Initial steps πͺ

- Open a new project
- Add a basemap
  - `Google Satelite` through the QuickMapServices plugin
- [Download the files](https://ughe-my.sharepoint.com/:u:/g/personal/gagazi_ughe_org/EaFUJmtuXhVDpQBSpUo3YUgB7BOkC3nI89VZeB3yWpCCig?e=DqTWjC)
- Unzip the folder
- Add the `.shp` file entitled `selection_houses`
- Zoom to the area of interest
  - `Zoom to layers option`

### Activity 4: Air polution & asthma π«

``` markdown
        1. Letβs add a layer containing a road going through the community
        2. Let's select some houses randomly
            a) Open attribute table for selection_houses
            b) Click Select features by area β select an area of houses
        3. Let's select houses within 50 meters of the main road (EPSG:3857)
            1. Method 1: by creating a 50 m buffer around our road
                a) Select selection_road layer β Vector β geoprocessing tools βbuffer
                        1. input layer: selection_road
                        2. distance: 50 m (0.0005 for those whose unit is decimal points)
                        3. Run
                        4. readjust layers β check if the distance really is 50m
                        5. Now weβre ready to select the houses within the buffer zone
                            1. Click on βSelect by locationβ or Vector β research tools β Select by location
                                1. select feature from: selection_roads
                                2. where the features: intersect
                                3. by comparing: buffered
                                4. Run
                                5. Show them how to invert selection and deselect
        3. How do we create a new layer from the selections?
            a) With the houses selected β right click on layer  β export β save selected feature as
```
---
## Case scenario 3: Rwand Mass Drug Administration Campaign π·πΌπͺ±π₯

Youβre contacted by the Rwandan Biomedical Center (RBC) Neglected Tropical Diseases (NTD) Program to assist with some GIS work. The program conducts yearly mass drug administration (MDA) campaigns where they distribute anti soil transmitted helmenthiasis (STH) medicine (albendazole) to pre-school-aged children (Pre-SAC). Once a year, parents bring their children to the closest health center to receive the drugs. The campaigns are preceded by mass mobilization campaigns used to communicate information about the MDA. 

After each MDA, the program reviews itβs coverage rate by comparing the number of children actually treated vs the projected Pre-SAC count before the launch of the campaign. The unit wants your assistance in visualizing their coverage rate for 2021 at the district level. Furthermore, they would like to compare the coverage rate in relation to the availability and distribution of health centers in the districts. 

They have provided the following two documents

- STH MDA Coverage data
- Distribution of health centers in Rwanda
---
### Activity 5: Rwand Mass Drug Administration Campaign π
   
1. Conceptualize the assignment
	- What is the required output? 
	- What things do you need to make this map?
2. Open QGIS & create a new project
   - Select the appropriate folder
   - Make sure the project CRS is EPSG:3857
3. Add a base-map
   - `Web`-->`QuickMapServices`-->`CartoDB`-->`Positron (retina)`
4. Find and add Rwandaβs shapefile
	- Download the shapefile [here](https://diva-gis.org/gdata)
	- Add it to QGIS
	- Explore its contents through the attributes table function
5. Download the document containing the information for MDA coverage at district level ππ½ [here](https://ughe-my.sharepoint.com/:x:/g/personal/gagazi_ughe_org/Ef1ylSR4fFFAuDKbOqOE9XgB0hYi3qSCW43eOWiGW-j3Gg?e=U99pYr)
   - Explore the csv file. What do you see? What is useful for you inorder to make the map?
   - Edit the file to meet your needs
6. Import the csv file into QGIS
   - Click on `Layer` --> `Add layer` --> `Add Delimited Text Layer`
   - `File Name`: locate the downloaded csv file
   - `Layer Name`: STH MDA Coverage
   - `File format`: csv
   - `Geometry Definition`: no geometry
   - Clic `Add`
   - What do you see on the layer list?
     - Open the new layer with the `Open attribute table`
7. Join the data to Rwanda's shapefile
   - Open the layer properties for Rwanda's shape file
   - Click `Joins`
   - Click the add symbol
   - `Join layer`: STH MDA layer
   - `Join field`: District
   - `Target field`: NAME_2
   - Check `Dynamic form` and `Editable layers`
   - Click `OK`
   - Click `Apply` then `Ok`
   - Explore the attribute table for Rwanda shape file. What do you see? π
8. Change the symbology the map using the MDA coverage information
9. Download the document containing information about the distribution of health centers in Rwanda ππ½ [here](https://ughe-my.sharepoint.com/:x:/g/personal/gagazi_ughe_org/ERIlsTsZN-ROtPEaZ8WoWk4BuW1uXXPo_1_SlRewmcnHBA?e=H7T30n)
10. Add the csv file containing the distribution of health centers in Rwanda into QGIS
   - `Geometry Definition`: point coordinates
     - `X field`: long
     - `Y field`: lat
     - `Geometry CRS`: Default CRS `EPSG:4326 -WGS 84`
11. Stylize the new health centers layer
12. Steps for creating a map for sharing
   - What do you think should be included in a map?
     - Cartographic guideline ππ½ [here](https://ughe-my.sharepoint.com/:b:/g/personal/gagazi_ughe_org/EXR9D-rLV9pBtSX8_ZOz_X8BJ8_LlbiBkK85ha9HDe7kvA?e=ld1uMU)
   - Take a look at the sample map shared by the RBC team ππ½ [here](https://ughe-my.sharepoint.com/:b:/g/personal/gagazi_ughe_org/EYc_kHHUpdNApvytsVzlZzAB_7N_3usBzyunKc68mw1u8g?e=KHBZQX)
13. Creating the map
   - Click on `Project` --> `New print layer`
   - Enter the title: `STH MDA`
   - Click `Ok`
14. Conduct the following activites
   - [ ] Create guidelines
     - Click on `Guides`
       - `Horizotal Guides`: 10mm, 200mm
       - `Vertical Guides`: 10mm, 200mm, 205mm, 285mm
   - [ ] Add map
     - Check `Lock layers` and `Lock styles for layers` when you are done editing
     - [ ] Add map inset
   - [ ] Add title
   - [ ] Add north
   - [ ] Add scale
   - [ ] Add citation and other information
15. Export the map
	- [ ] Pdf 
	- [ ] png 

---

## References π₯Έπ

- [QGIS Documentation](https://docs.qgis.org/3.22/en/docs/index.html) π
- [QGIS Tutorials](https://www.qgistutorials.com/en/index.html) πΌ
- [How to make a map](https://www.qgistutorials.com/en/docs/3/making_a_map.html) πΊ
- [QGIS Map Showcase](https://www.flickr.com/groups/qgis/pool)
