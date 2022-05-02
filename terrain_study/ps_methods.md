## Raster overlay methods for shaded relief  

### Review  

- Why/when should you change azimuth?  
- Why/when should you change the altitude?  
- Why/when should you change the z-factor?  

### Principles of hand-drawn shaded relief.   

[Relief shading design principles](http://www.reliefshading.com/design/)  

#### Key principles  

1. Remove excessive terrain detail (noise) and accentuate major landforms (visual hierarchy).    
2. Illuminate terrain from more than one direction.  
3. Make valley bottoms neutral gray, illuminated slopes lighter gray, shaded slopes darker gray.
4. Increase contrast (use darker tones for shadows) as you increase elevation and reserve darker tones for highest elevations (aerial perpective).   

### Design context  

- These principles are for shaded relief as a _base layer_.  
- This assumes that the terrain layer should be able to work with labels, lines, and symbol layers that would lie on top of this base layer.    

For example, compare:  

- [Eduard Imhof 'Karte der Gegend um den Walensee' (1938)](http://www.reliefshading.com/examples/walensee/)  
- [Tom Patterson 'Adirondack Park Wall Map' (2019)](http://shadedrelief.com/adk/Resources/f.jpg?36)  

### Materials  

At a minimum, you should work with the following layers:  

- DEM  
- at least two hillshades with different parameters    
- slope layer  

_QGIS demo_  

### Methods  

#### Median filter (remove detail)  

1. Open a hillshade layer in Photoshop.
2. Create a copy of the layer.   
2. Convert layer to a Smart Object.  
3. Filter> Noise> Median  
    - Adjust radius   
4. Create a composite layer.  
    - Mac: Shift-Command-Option-E  
    - PC: Shift-Ctrl-Alt-E  

_Quick check: Why are smart objects helpful?_  

#### Adjustment layer - levels    

1. Still with a hillshade layer in Photoshop.  
2. Add Adjustment Layer (bottom of layer panel, half-moon circle icon).   
3. Apply stretch enhancement (set min and/or max display values).  
4. Change min and/or max color values.   

#### Blending modes   

To become acquainted with blending modes in Photoshop, please open [this demo file](https://drive.google.com/file/d/1MM13YVUt4TDU7e6F3n2EYVNPLd6S76DR/view?usp=sharing) and compare to [this page](https://helpx.adobe.com/photoshop/using/blending-modes.html) from the Adobe manual.  

Now try blending two terrain layers together (two different illumination angles, or )

#### Masks

To become acquainted with masks in Photoshop, please open [this demo file](https://drive.google.com/file/d/1Ctd0VsMk6DbnVG5_2PA3jY-cHojPAIuw/view?usp=sharing).  

#### Homework problems    

- How could you adjust the tones of only valley bottoms separately from the tones of slopes?  

- How could you make the amount of black used in shadows to increase with higher elevations?  
