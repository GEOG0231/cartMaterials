## Shaded relief tasks    


| TASK | KEY TERMS | WORKFLOW |
| :--- | :--- | :--- |
| Bring DEM into Photoshop | [Data types][dataTypes] | [1. Scale image values for Uint16][scaleUint16]<br>[2. Convert image data type to Uint16][convertUint16] |  
| Bring Slope layer from QGIS into Photoshop | [Data types][dataTypes] |  [1. Make slope from DEM[makeSlope] 1. Scale image values for Byte][scaleByte]<br>[2. Convert image data type to Byte][convertByte] |      


### Data types  

| Type | Min | Max | QGIS output<br>good for PS  | Scale and convert for PS |
| :--- | :---: | :---: | :--- | :--- |
| Byte | 0 | 255 | Hillshade | Slope (degrees) |
| Uint16 | 0 | 65535 | | DEM |  

### Convert image data type to Byte  

_This step usually follows [scale image for byte][3]._  

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Translate (convert format)**: GDAL> Raster conversion> Translate (convert format)  
3. Input layer: image_scaled.tif  
4. Output data type: Byte  
5. Converted: Ellipses> Save file> _image_scaled_converted_byte.tif_   

### Convert image data type to Uint16

_This step usually follows [scale image for uint16][1]._  

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Translate (convert format)**: GDAL> Raster conversion> Translate (convert format)  
3. Input layer: _image_scaled.tif_  
4. Output data type: Uint16  
5. Converted: Ellipses> Save file> _image_scaled_converted_uint16.tif_   


### Scale image for byte  

Here is the general equation to scale the pixel values of an image so that they are in the range of an 8 bit integer (byte) data type.   

**(Image - min value) / (max value - min value) * 255**  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Raster calculator**: Raster analysis> Raster calculator  
3. Expression: (_image_name_ - _min_value_) / (_max_value_ - _min_value_) * 255  
4. Reference layer(s): _image_name_  
5. Output: Ellipses> Save file> image_scaled.tif  
6. Run  

### Scale image for Uint16  

Here is the general equation to scale the pixel values of an image so that they are in the range of an unsigned 16 bit integer (Uint16) data type.   

**(Image - min value) / (max value - min value) * 65535**  

In QGIS:  

1. Open Processing Toolbox: Processing>Toolbox  
2. Search for **Raster calculator**: Raster analysis> Raster calculator  
3. Expression: (_image_name_ - _min_value_) / (_max_value_ - _min_value_) * 65535  
4. Reference layer(s): _image_name_  
5. Output: Ellipses> Save file> image_scaled.tif  
6. Run  

[convertByte]: #convert-image-data-type-to-byte  
[convertUint16]: #convert-image-data-type-to-uint16  
[dataTypes]: #data-types  
[scaleByte]: #scale-image-for-byte  
[scaleUint16]: #scale-image-for-uint16  
