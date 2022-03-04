## 05B Map lettering (2): Q to AI workflow  

This tutorial walks through a workflow to compile labels with QGIS and export them into Illustrator for styling.  

After working through this tutorial, please try to apply the methods demonstrated here to your own map project.  

In lecture on Monday, we will begin to examine strategies and methods for using a style sheet to  develop and impose a type hierarchy.    

### Playlist  

[QGIS to Adobe Illustrator: Lettering (5 videos)](https://www.youtube.com/playlist?list=PLdXGsLVpvp2rJpWtSxuJpgg2jisZ5-12C)  

### Video notes  

#### 0511 Point labels: preparation    

**1. Create a spatial index for a point layer.**  

  - Vector general> Create spatial index  

    - Input layer: your point layer  

**2. Select the points that are in your map extent.**      

  - Vector> Research Tools> Select by location

    - Select features from: point layer  

    - Where the features (geometric predicate): intersect  

    - By comparing to the features from: Layout extent  

    - Modify current selection by: creating new selection  

**3. Save selected points as a layer.**  

  - Right-click layer name  

     -  Export> Save selected features as  

       -  Format: GeoPackage  
       -  File name: _osm_natural_points_in_extent  

**4. Select only the points with placenames.**  

  - Select layer and look at attribute table.  

  - Select by expression>  "name" is not  NULL  

**5. Save selected points as layer.**

  - _Repeat steps described in step 3 above, but change the name as appropriate._      

**6. Symbolize points by class.**  

  - Select the layer.    

  - Layer properties> Symbology> Categorized  

    - Value: natural (or equivalent)  

    - Symbol> Simple marker> Stroke style: No Pen  

    - Color ramp: Random colors  

    - Classify  

#### 0512 Display point labels in QGIS  

**1. Open labeling properties for a layer.**    

  - Select the layer.  

  - Layer properties> Labels> Single labels  

    - Value: name (or appropriate column with your placenames)  

**2. Define text rules.**  

  - Font: Avenir (or your choice)  

**3. Define placement rules.**  

  - Mode: Offset from Point  

  - Quadrant: center position  

  - Offset X,Y: 0, 0  

  - Priority: High  

  - Obstacles: **uncheck** Features act as obstacles  

**4. Define rendering rules.**  

  - **Uncheck** Scale dependent visibility.   

  - **Check** show all labels for this layer (including colliding labels).  

  - Feature options> **Check** Label every part of multi-part features.  

**5. Apply all label rules for layer.**  

  - Apply  
  - OK  

#### 0513 Move labels from QGIS to AI  

**1. Prep the Project view.**  

  - Only display the layer that has the labels that you want to bring into AI.  

**2. Open the Layout view.**

  - Project> Layouts> select your layout.  

  - Refresh  

**3. Export the layer as svg.**  

  - Layout> export as SVG.  

  - Ignore the warning.  

  - Name the file.  

  - SVG Export Options>

    - **Uncheck** all options.  

    - Text export: Always expert as Text Objects.

#### 0514 Manage the labels in AI  

**1. Open file in Adobe Illustrator.**  

**2. Create a new layer for labels.**  

**3. Select and move labels.**  

  - Ungroup  

  - Select one label (anyone will do)  

  - Select> Same> Fill and stroke  

  - Cut selected paths  

  - Select labels layer> paste in place  

  - Ungroup  

**4. Add to map compilation file in AI.**  

  - Copy labels.  

  - Open map compilation file.  

  - Add a new layer for labels.  

  - Paste in place.    


#### 0515 Display area labels in QGIS  

**1. Open labeling properties for a polygon layer.**  

  - Select the layer  

    - _Remember to select a polygon layer that you have clipped to your map extent, so that you only bring in layers within your extent._      

  - Layer properties> Labels> Single labels  

    - Value: name (or appropriate column with your placenames)    

**2. Define text rules.**  

  - Font: Baskerville (or your choice, but something different)  

**3. Define placement rules.**  

  - Mode: Offset from Centroid    

  - **Uncheck** Allow placing labels outside of polygons  

  - Centroid: visible polygon  

  - **Check** Force polygon inside of polygon  

  - Quadrant: center position  

  - Offset X,Y: 0, 0  

  - Priority: High  

  - Obstacles: **uncheck** Features act as obstacles  

**4. Define rendering rules.**  

  - **Uncheck** Scale dependent visibility.   

  - **Check** show all labels for this layer (including colliding labels).  

  - Feature options> **Check** Label every part of multi-part features.  

**5. Apply all label rules for layer.**  

  - Apply  
  - OK    
