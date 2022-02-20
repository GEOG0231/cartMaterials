## QGIS to Adobe workflow  

This is the second part of a tutorial that walks you through using Adobe and QGIS to make map layouts. It is based on workflows used by professional cart shops, including the National Park Service and National Geographic.  

The basic idea is that we will use different software platforms for different parts of the mapmaking workflow:  

- For **map layout**, we use Adobe InDesign.    
- For **map compilation**, we use QGIS.  
- For **map styling**, we use Adobe Illustrator for vector data and labels. (When we get to raster geographic data, we will use Adobe Photoshop).   

_Please note: this workflow is admittedly a little arduous, especially when you first start trying to work through it. The main advantage is that the Adobe tools will allow you to customize the style of mapped geography and marginalia in ways that are not possible in QGIS alone._  

## Playlist   

Please work through this playlist after you have [made a grid with InDesign](layout.md) to guide your layout.

[Playlist (13 videos)](https://youtube.com/playlist?list=PLdXGsLVpvp2rYyf4o4IE3WbZJOOJMoI8_)   

### Goal

Quick overview of end products from this tutorial.  

### Quick intro to QGIS  

- Start QGIS  
- View> Panels> Browser Panel  
- View> Panels> Layout Panel
- View> Toolbars> Project Toolbar    
- View> Toolbars> Map Navigation Toolbar  

### Add data, pan, and zoom    

- Browser> XYZ Tiles> OpenStreetMap  
- To navigate:   
    - Pan: space bar  
    - Zoom in: command/ctrl +  
    - Zoom out: command/ctrl -   
- Project>Save  

### Create new layout  

- Project> Layout manager  
- New from Layout> Empty layout> Create  
- Enter a title  
- Right-click on page> page properties  
- Item properties> Size> Custom  
- Item properties> Width: 1224 pts (from InDesign layout)  
- Item properties> Height: 1048.5 pts (from InDesign layout)  
- Guides> Horizontal Guides> Add> 692 pt, 350 pt (thirds)  
- Guides> Vertical Guides> Add> 612 pt (center)
- Save layout   

### Add project map to layout  

#### In Layout View  

- Add Item>Add Map  
- Select/Move Item  
- Move item content  
- Item Properties> Scale  
- Item Properties> Map rotation  
- CRS: Use Project CRS  
- Zoom to 100%  
- Zoom to Full (Fit Layout)

### Design mapped geography  

#### In Layout View  

##### Think about:

- your map's purpose, audience, and media  
- map center and vertical thirds  
- geographic wholes and map edge

##### Primary tools:  

- Scale: 80000 (try keep rounded to 1000)  
- Map rotation: -105  
- Move item content  
- When done, Item> Map 1> Lock  

### Add North Arrow  

#### In Layout View  

- Add Item>North Arrow>  
- Item Properties> Picture> SVG image> SVG groups>   

### Add scale bar  

#### In Layout View  

- Add Item>Scale bar  
- Item Properties> Map: Map 1  
- Item Properties> Style: Line Ticks Middle  
- Item Properties> Scalebar units: Miles  
- Item Properties> Segments: left 0, right 1
- Item Properties> Fixed width: 1

### Make layer of map extent  

#### In Project View  

- Processing> Toolbox  
- Cartography> Print layout map extent to layer  
- Print layout> _select your map layout_  
- Map item> Map 1  
- Extent> ... > Save to File >  
- Layer Properties> Symbology> Simple Fill> Stoke style: No Pen  
- Make OSM not visible  (uncheck)
- Save  

### Export layout  

#### In Layout View  

- Refresh  
- Layout> Export as .pdf  
- New Folder> 'exports'  
- '_01_extent_scale_arrow.pdf'  
- Uncheck 'Export RDF metadata'  
- Uncheck 'Save geo-reference information'  
- Uncheck 'Simplify geometries to reduce output file size'   

### Open pdf with AI  

- Organize layers  
    - Remove clipping masks  
    - Ungroup  
    - Create new layers  
- Save as .ai   
- Create new 'marginalia' .ai file  
- Cut and paste north arrow and scale bar  
- Save files  

### Place .ai file into InDesign  

- File> Place>  
- Select .ai file  
- Reflect on the layout. If you want to change the size of the mapped geography, you will want to do so at this stage (before we start adding a lot of layers to the map).     
