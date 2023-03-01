# MGHD-OH-GIS-Workshop

In this hands on workshop, you will explore the concepts of Geographic Information Systems and use the free and open source QGIS software to create different vector elements as well as use public health data to create a compelling choropleth maps. 


# Pre-requisites

1. A laptop
2. Internet
3. [QGIS Software]()
4. Vibes 😎

# Activity 1: Adding point vector layer

## Case Scenario

It is Ebola season in Uganda and the DRC. The Rwandan Biomedial Center is exploring 

    a) Create a folder in your desktop – QGIS course
    b) Creating a new layer
        1. layer → create layer → new shapefile layer
        2. layer information
            1. file name: houses (make sure it’s in the QGIS course layer)
            2. geometry type: point
            3. Additional dimensions: Project CRS
            4. new field
                1. name: room_number
                2. type: integer (because rooms are full numbers)
                3. length: 2 (most likely won’t go beyond double digit rooms at most)
                4. click: add to fields layer
        3. Now you try adding two new fields
            1. reg_date: date
            2. latrine: text
    c) Now we have our layer, let’s add some points
        1. Let’s move to an area with some houses: 3354736,-219125
            1. Go to the ‘coordinate box at the bottom of your screen and put in this number
        2. Click on the house layer, in the layer view
        3. Toggle the editing icon       → add point feature1       → you get a target 
        4. click on a house;
            1. pop up – fill in the information → click save
            2. how can we check the information we put in?
                1. Click on the ‘Attribute table’ and view the information you entered
            3. Now, let’s say you want to add a new field, household_head, how can you do that?
                1. While in the attribute table view, toggle the edit mode (ctrl+e)
                2. find and click on ‘New field’ (ctrl+w) then input the information
                    1. name: house_head; type: text → click save
                    2. In the edit mode, we can add information to the previous point we had entered 
                        1. Double click on the ‘Null’ box → type female
                    3. Add two more points – male and female headed
                    4. to save changes: click on edit mode icon
        5. Save your file
