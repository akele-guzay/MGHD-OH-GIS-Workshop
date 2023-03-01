# MGHD-OH-GIS-Workshop

In this hands on workshop, you will explore the concepts of Geographic Information Systems and use the free and open source QGIS software to create different vector elements as well as use public health data to create a compelling choropleth maps. 


# Pre-requisites

1. A laptop
2. Internet
3. [QGIS Software]()
4. Vibes 😎
---

## Case Scenario: Ebola Season 😱🏃🏽‍♀️✈️

It is Ebola season in Uganda and the DRC. The Rwandan Biomedial Center (RBC) is exploring potential areas of disase introductio into Rwanda. They are looking at major boarder crossings between Rwanda and the two countries, as well as the major international airport in Kigali as potential sites for disease introduction. They have contacted you to map out some important structures within the airport to plan for case screening. They would like to see:

1. Two hand washing stations 🧴
2. Two paths for individuals to disembark a flight and walk along 🚸
3. Two buildings where travelers can be screened 🏢

---

### Activity 1: Creating the hand washing stations 🧴

``` markdown
*Initial steps*

- Launch QGIS
- Go into the Projects setting
  - General
    - Project file: GIS_Workshop
    - Prject home
    - Project title
    - Units for distance measurement: meters
  - CRS: `EPSG:3857`
- Add a basemap
  - ```A basemap is a layer that provides geographical context to the map and other dataset layers above it.```
- Find the Kigali airport
```

``` markdown
    a) Create a folder in your desktop – QGIS course
    b) Creating a new layer
        1. layer → create layer → new shapefile layer
        2. layer information
            1. file name: hand_washing (make sure it’s in the QGIS course layer)
            2. geometry type: point
            3. Additional dimensions: Project CRS
            4. new field
                1. name: tap#
                2. type: integer (because rooms are full numbers)
                3. length: 2 (most likely won’t go beyond single digit)
                4. click: add to fields layer
        3. Now you try adding two new fields
            1. soap?: text
            2. bld_date: date
    c) Now we have our layer, let’s add some hand washing points
        1. Click on the hand wash layer, in the layer view
        3. Toggle the editing icon → add point feature → you get a target 
        4. click on a spot outside some buildings
            1. pop up – fill in the information → click save
            2. how can we check the information we put in?
                1. Click on the ‘Attribute table’ and view the information you entered
            3. Now, let’s say you want to add a new field,running_water, how can you do that?
                1. While in the attribute table view, toggle the edit mode (ctrl+e)
                2. find and click on ‘New field’ (ctrl+w) then input the information
                    1. name: running_water; type: text → click save
                    2. In the edit mode, we can add information to the previous point we had entered 
                        1. Double click on the ‘Null’ box → type yes
                    3. Add two more points
                    4. to save changes: click on edit mode icon
        5. Save your file
        
```
        
### Activity 2: Paths for disembarking 🚸

``` markdown
    d) Creating a new layer
        1. layer → create layer → new shapefile layer
        2. layer information
            1. file name: paths
            2. geometry type: line string
            3. new field
                1. name: path_name
                2. type: string
                3. length: 10
                4. click: add to fields layer
    e) Now we have our layer, let’s add a short path
        1. Click on the road layer, in the layer view
        2. Toggle the editing icon → add line feature → you get a target 
        3. click on a path and add the feature; 
            1. When you’re done `Right Click` to remove the target
            2. then input the right information and click save
            3. exit editing mode and save changes to layer
        4. Click on the attribute table so we can see what we entered
        5. Let’s say you want to calculate the length of our paths – 2 ways to do this
            1. toggle the editing icon on attribute table view
               2. click `Open field calculator` (ctrl+i)
                  1. fill in the following info:
                    1. Output field name: length
                    2. output field type: decimal number (real)
                    3. Expression box: $length
                    4. press ‘OK’
            2. Easy way for quick measurements
                1. click the ‘measure line’ on top
                2. click along the line → write click when you’re done
                   a. Question: What’s the length of the runway?
                4. click on the ‘pan map’ hand icon
```

#### Stylizing our wash points and paths 💄

``` markdown
    f) Let’s say we want to change the color of our wash points based on number of taps and the shape of the icons
        1. right click on the hand washing layer → properties → symbologies → categorized (this is for discreet values)→ change value to `tap#` → click classify at the bottom → apply
        2. click Labels → single label → `tap#`
        3. Question: change the marker and color of the road and label it with ‘road length’   
```

### Activity 3: Selecting buildings for screening 🏢

``` markdown
    g) Reproduce the processes from before
    h) Fields
        1. bldg_name: string
        2. bldg_type: string
        3. door#: integer (32bit)
        4. window#: integer (32bit)
    i) trace the airport buildings with paths – right click when you’re done
    k) toggle editing button → save
```

#### Changing basemaps via QuickMapServices 🗺

``` markdown
1️⃣ Plugins menu > Manage and Install Plugins… 
    • Scroll down, or search all plugins for `quickmap` (you don’t need to type the whole name) 
    • Select the QuickMapServices plugin 
    • Click the `Install plugin` button (it installs in seconds) 
    • Click `Close` 

2️⃣ When you first install QuickMapServices, you'll want to get the full set of basemap definitions.
    • Web menu > QuickMapServices > Settings 
    • `More services` tab > `Get contributed pack`

3️⃣ To add the Google Satelite basemap, which combines aerial photos with place name labels:
    • Web menu > QuickMapServices > Google > Google Satellite
```
