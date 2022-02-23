## Data wrangling: Open Street Map    

This tutorial shows you how to extract data from Open Street Map (OSM), clean and prepare data layers with QGIS, export data layers into Adobe Illustrator, and organize layers by feature and sub-type.   

We will focus on gathering data from OSM for roads and land/water boundaries. These lines often serve as reference features on maps (elements that help people understand location and think spatially). In forthcoming tutorials, we will look at methods for working with political boundaries and point data.    

### Playlist  

[Data wrangling with OSM (13 videos)](https://youtube.com/playlist?list=PLdXGsLVpvp2raFwvdkdHjD9sJR6RDu8BU)

### Video notes  

#### Add Google tile service to QGIS    

- In QGIS: Browser> XYZ Tiles> right click> New Connection  
- Name: something descriptive  
- URL: paste appropriate url from [this table](https://docs.google.com/spreadsheets/d/1MztAeJly_-2Jcf_5B0nzju4ejUGkN7fm2x8aUPVH06Q/edit?usp=sharing)

#### Introduction to OSM   

- History of OSM  
- wiki   
- OSM features (highways, natural, waterways, boundaries)  

#### QuickOSM  

- Install plugin  
- Vector> QuickOSM or View> Toolbars> QuickOSM  

#### Extract and explore OSM roads  

- In QGIS  
- Create group, rename
- Explore data  
- View> Toolbars> Attributes Toolbar
- Activate layer> Identify features icon> click   
- Activate layer> Open Attribute icon> click

#### Select with symbology  

- Layer properties> Categorized  
- Value> highway
- Color ramp> Random colors   
- Classify   
- Uncheck from layer contents  

#### Dissolve  and explode (multipart to singlepart)  

- Inspect geometries  
- Processing> toolbox>Vector geometry> Dissolve  
- Input layer> highway (or whatever line work you want)  
- Dissolved field> highway (or whatever OSM attribute distinguishes attributes)
- Dissolved> osm_roads_dissolved, put in folder (qgis_data_layers)  
- Run  
- Compare to original  
- Redo Symbolize and select by attribute task    

#### Clip linework by map extent  

- Compare OSM features to map extent  
- (optional): Processing> Toolbox> Vector general> Create spatial index
- Processing> Toolbox> Vector overlay> Clip  
- Input layer: roads_dissolved (or equivalent)  
- Overlay layer: map extent layer  
- Clipped: osm_roads_dissolved_clipped (in qgis_data_layers folder)
- Compare to previous  
- Redo: Symbolize and select by attribute task   

#### Export linework to AI  

- Open Layer Manager  
- Uncheck marginalia  
- Refresh  
- Layout> Export pdf  
- Open AI  
- Open Map Layout file    
- Open export file  
- Find feature layer  
- Select layer> Copy
- Activate Map Layout file
- Create new folder  
- Activate folder> paste in place  

#### Organize features  

- In QGIS: Remind yourself how colors represent feature attributes  
- In AI: select one feature
- Select> Same> Fill and Stroke  
- Cut  
- Make new sub-folder (attribute class)> Paste in place
- Repeat for other line types  

#### Saving work with OSM imports  

- The original layers from QuickOSM are temporary (not saved on your hard drive)  
- Before you close your project, you need to export these original layers and save them on your hard drive if you want them available when you next open the project.  

#### Land/water linework  

- Extract 'natural' OSM features  
- Symbolize polygons by attribute  
- Note small island/big island problem> water-based solution  
- (optional): Processing> Toolbox> Vector general> Create spatial index  
- Do: Clip Linework by Map extent task    
- Do: Symbolize and select by attribute task  
- Right-click layer> Symbology> Simple fill> Stroke style> no pen
- Do: Export linework to AI  

#### Figure from ground task  

- View> Toolbars> Selection Toolbar  
- Select by expression>
    - Fields and Values: "natural"
    - =  
    - Show values> All unique > 'bay'
    - Final expression:  "natural" = 'bay'  OR "natural" = 'water'  
    - Select features  
- Right-click layer> Export> Save selected features as  
- Name 'osm_selected_water' and put in qgis_data_layers  
- Processing> Toolbox> Vector overlay> Difference  
- Input layer> map extent
- Overlay layer> selected water features  
- Difference: osm_difference_for_land  
- Do: Export linework to AI task  
