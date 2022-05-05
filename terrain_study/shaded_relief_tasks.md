## Shaded relief workflow    


| TASK | KEY TERMS | WORKFLOW |
| :--- | :--- | :--- |
| Prepare DEM for Photoshop | [Data types][dataTypes] | [Scale image for Uint16][scaleUint16]<br><br>[Convert image to Uint16][convertUint16] |  
| Prepare Slope image for Photoshop * | [Data types][dataTypes] | [Make slope from DEM][makeSlope]<br><br> [Scale image for Byte][scaleByte]<br><br>[Convert image to Byte][convertByte] |
| Create a grayscale stack file | |[Load files into stack][loadStack]<br><br>[Organize layers][organizeLayers] |
| Remove detail from hillshades | | [Apply median filter][medianFilter] |  
| Illuminate from multiple angles | | [Blend hillshades][blendHillshades] |  
| Make shaded base layer | | [Apply level adjustment layer][adjustLevels]<br><br>[Make composite layer][makeComposite] |   
| Apply aerial perspective | | [Simple aerial perspective](makeAP) |  
| Save graystack | | |
| Make color stack | |    
| Make hypsometric tints | | Apply color gradient map<br><br>Customize color gradient |  
| Apply shading to hypsometric tint | | Add composite layer from gray stack to color stack<br><br>Change blending mode. |  
| Tint shadows | | Create shadow mask.<br><br>Add Hue/Saturation adjustment layer.<br><br>Apply shadow mask to adjustment layer. |  


### Key terms

#### Data types  

Data types constrain the range of values that can be stored by an image. In general, you need to have images in either Byte or Uint16 formats in order to work with them in Photoshop.  

The table below lists the data type and the minimum and maximum integers that can be stored by the data type. The fourth column (QGIS output good for PS) identifies layers created in QGIS that can be used directly in Photoshop. The fifth column (scale and convert for PS) identifies layers created in QGIS that should be converted into the row data type in order to be used in Photoshop.   

| Type | Min | Max | QGIS output<br>good for PS  | Scale and convert for PS |
| :--- | :---: | :---: | :--- | :--- |
| Byte | 0 | 255 | Hillshade | Slope (degrees) |
| Uint16 | 0 | 65535 | | DEM |  

### Tasks  

#### Apply level adjustment layer  

_To adjust the contrast of a layer._  

1. Click on the layer or folder that you want to change.  
2. Click on the adjustment button (half-moon circle, bottom center of layers panel)> Levels.
3. Adjust the numbers directly below the histogram to change the data range (the min and max data value to distinguish with the grayscale ramp).
4. Adjust the output levels to change the colors used to display the min and max data values. Increasing the minimum output will reduce the strength of black, while decreasing the maximum output will reduce the strength of white.  
5. For the base shade layer, the minimum display value should be a more mid-gray and the maximum display value should not be pure white.  

_Please note: if you only want to apply the adjustment to the layer directly underneath the adjustment layer, then hold option key (mac) or alt key (pc) and hover the cursor in between the adjustment layer and the layer you want to effect and click once. If you are successful here, a little arrow show appear on the adjustment level pointing down._  

#### Apply median filter  

_To remove excessive detail in a hillshade layer._  

1. Open a hillshade layer in Photoshop  
2. Convert to smart object:  
    1. Click on layer in layers panel  
    2. Layer> Smart Objects> Convert to smart object  
3. Filter> Noise> Median  
    1. Make sure 'Preview' is checked.
    2. Adjust Radius (larger radius = more generalized)  
4. Repeat for other hillshades in your stack.    

#### Blend hillshades  

_To combine two or more hillshades together to illuminate terrain from more than one direction._  

1. Create a new group layer and name it 'hillshade blend' or something equivalent.  
2. Put the two or more group layers with hillshades into this new blend folder.  
3. Click on the top-most sub-group layer and change the blend operation.  
    - 'Darken' is a good blend to start with.  

#### Convert image data type to Byte  

_This step usually follows [scale image for byte][scaleByte]._  

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Translate (convert format)**: GDAL> Raster conversion> Translate (convert format)  
3. Input layer: image_scaled.tif  
4. Output data type: Byte  
5. Converted: Ellipses> Save file> _image_scaled_converted_byte.tif_   

#### Convert image data type to Uint16

_This step usually follows [scale image for uint16][scaleUint16]._    

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Translate (convert format)**: GDAL> Raster conversion> Translate (convert format)  
3. Input layer: _image_scaled.tif_  
4. Output data type: Uint16  
5. Converted: Ellipses> Save file> _image_scaled_converted_uint16.tif_   

#### Load files into stack  

_To quickly create a set of layers in a single file from a set of files._  

With Photoshop open:  

1. File> Scripts> Load files into stack  
2. Load layers window: Browse> select files  
    1. Scaled and converted DEM  
    2. Two or more hillshades  
    3. Scaled and converted slope  

#### Make composite layer  

_To take a snapshot of a stack of layers. This is similar to the idea of 'flattening' a stack, but this method is non-destructive (you do not lose the stack)._

1. In layers panel, click on the top layer of a stack.
2. Make the composite layer.  
    - Mac: Shift-Command-Option-E  
    - PC: Shift-Ctrl-Alt-E  

#### Make slope layer from DEM  

1. Open Processing Toolbox: Processing>Toolbox  
2. GDAL> Raster analysis> Slope  
3. Input layer: _original DEM_    
4. Slope: ellipses> Save to file> slope_degrees.tif   

#### Organize layers  

_To keep your file organized._

1. Open Layers panel.
2. Click folder icon.
3. Name folder after layer.
4. Place layer in folder.
5. Repeat for all layers.    

#### Scale image for byte  

Here is the general equation to scale the pixel values of an image so that they are in the range of an 8 bit integer (byte) data type.   

**(Image - min value) / (max value - min value) * 255**  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Raster calculator**: Raster analysis> Raster calculator  
3. Expression: (_image_name_ - _min_value_) / (_max_value_ - _min_value_) * 255  
4. Reference layer(s): _image_name_  
5. Output: Ellipses> Save file> image_scaled.tif  
6. Run  

#### Simple aerial perspective  

_To give strongest contrast to highest elevations and progressively reduce contrast with decreasing elevation._  

1. Get organized: Create a group layer, name it 'aerial perspective' or something equivalent. (See [organize layers][organizeLayers]).
2. Move shaded base layer into folder (you will need to move both the shade layer and the levels adjustment layer).  
3. Make a copy of the layer and the adjustment layer: click, option-drag (mac) or alt-drag (pc).  
4. Rename layer 'aerial perspective' or something equivalent.
5. Change the levels adjustment on the aerial perspective layer so that the output value min is a bit darker and the output value max is white (255).  
6. Apply a mask to the aerial perspective image: click the black circle on white icon at bottom of layers panel.
7. Copy the DEM:
    1. Click on the DEM.
    2. Select all: command-D (mac) or ctrl-D (pc)  
    3. Activate the mask panel: option-click (mac) or alt-click (pc) mask panel on aerial perspective layer.  
    4. Paste the copied image: command-v (mac) or ctrl-v (pc).
    5. Click on another layer to deactivate mask panel.  

_To fine tune, you can use levels to stretch enhance the DEM (to increase mask on lower elevations). You can also experiment with different blending modes between aerial perspective layer and base shade layer.     

#### Scale image for Uint16  

Here is the general equation to scale the pixel values of an image so that they are in the range of an unsigned 16 bit integer (Uint16) data type.   

**(Image - min value) / (max value - min value) * 65535**  

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Raster calculator**: Raster analysis> Raster calculator  
3. Expression: (_image_name_ - _min_value_) / (_max_value_ - _min_value_) * 65535  
4. Reference layer(s): _image_name_  
5. Output: Ellipses> Save file> image_scaled.tif  
6. Run  

[adjustLevels]: #apply-level-adjustment-layer    
[blendHillshades]: #blend-hillshades  
[convertByte]: #convert-image-data-type-to-byte  
[convertUint16]: #convert-image-data-type-to-uint16  
[dataTypes]: #data-types  
[loadStack]: #load-files-into-stack  
[makeAP]: #simple-aerial-perspective  
[makeSlope]: #make-slope-layer-from-DEM  
[makeComposite]: #make-composite-layer  
[medianFilter]: #apply-median-filter    
[organizeLayers]: #organize-layers  
[scaleByte]: #scale-image-for-byte  
[scaleUint16]: #scale-image-for-uint16  
