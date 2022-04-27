## Terrain study - part 1  


### Plan the study   

Please plan to make a layout that compares methods for layered compositions of terrain with multiple tiles.        

[Imhof examples](https://drive.google.com/file/d/1IDaugNyd9clOR7Gk6ptVxupoTwCYNGV_/view?usp=sharing)  

The layout should be designed for print and should fit on one or more 11" x 17" tabloid-size pages.  

This suggests a 5" x 5" tile for each multiple and use of a CMYK color model.  

### Create a DEM scale calculator  

#### Key terms  

- Raster data model    
- DEM  
- Resolution  
- Extent        
- Pixel density  

#### Task  

1. Open a new Google sheet  
2. Fill out a sheet as described in the table below.      

| A | B | C |
|:--: | :--: | :--: |  
| DEM resolution (m) | 15 |  
| Map pixel density (p/cm) | 120 | _Should be 40, 80, or 120_ |  
| **MAP SCALE** | __= B2 * 100 * B3__ |

### Choose a DEM  

Choose a DEM from the [Sample Elevation Models for Evaluating Terrain Representation](http://shadedrelief.com/SampleElevationModels/).  

Key decisions:  

- What resolution?  
- What map scale?    
- What region or landforms?  

To get acquainted with the data, we will start with Gore Range. Please download the folder and unzip it.     

#### Key terms

- LiDAR  
- SRTM  
- NED  

### Explore in QGIS  

1. Open QGIS.
2. Add 5m DEM.    
3. Display as hillshade.  
4. Discuss resampling artifacts.   
5. Change resampling to biliear (layer and QGIS preferences).  

### Create tile layout

1. In QGIS, Project> New Print Layout
2. Change paper size to 5" x 5".
3. Draw layer.
4. Use scale calculator to scale.  

### Basic hillshade concepts  

#### Key terms  

- Altitude  
- Azimuth  

#### Quick altitude study  

1. Create a group called 'altitudes'.    
2. Duplicate original layer, put in group, and change altitude to 0. Discuss.
3. Duplicate original layer, put in group, and change altitude to 90. Discuss.

#### Quick azimuth study  

1. Create a group called 'azimuths'.    
2. Duplicate original layer, put in group, and change azimuth to 135. Discuss.  
3. Duplicate original layer, put in group, and change azimuth to 270. Discuss.

### Scale and extent  

#### Key terms  

- resolution  
- extent  
- contrast  
- z-factor  

#### Quick resolution study

1. Create a group called 'Resolution study'.
2. Add the 1m, 15m, 30m, 90m, 250m, 500m tifs.
3. Display each as a hillshade.   
4. Discuss: how is contrast related to resolution and extent?  

#### Quick z-factor study?  

1. For the 500m layer, change z-factor to 4. Discuss.
2. For each layer, change the z-factor to improve contrast.  
3. Discuss relationship between resolution and z-factor.  

### Hand-drawn versus automated shaded relief  

1. Go to [Shaded Relief Archive](https://www.shadedreliefarchive.com/).  
2. In USA folder, download Harrison and Schutzler shaded relief maps.  
3. Open in QGIS.  
4. Compare hand-drawn to automated shaded relief maps.
5. Discuss.

### Google Terrain Map  

1. In QGIS, right-click XYZ Tiles> New Connection  
2. Name: Google Terrain  
3. URL: https://mt1.google.com/vt/lyrs=p&x={x}&y={y}&z={z}  
4. OK.
5. Add to map and place as bottom layer.  
6. Discuss.  

### Slope shading  

1. In QGIS, Processing toolbar> GDAL> Raster analysis> Slope.
2. Select DEM.
3. Accept defaults and Run.
4. Place above hillshade.
5. Layer properties > Symbology > Color gradient: White to black.
6. Layer properties > transparency > 50%.
7. Discuss.

### Homework  

By our next meeting, please:  

1. Choose a dataset.
2. Choose a resolution and map scale.  
3. Try to create two or more 'on-the-fly' hillshade layers that have strengths and weaknesses individually, but may have potential benefits if combined together.  
