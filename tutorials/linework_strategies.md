## Common problems  

A quick review of common cart problems and how to fix them.      

Please download [this toy problem](https://drive.google.com/file/d/1FcHYi7dzo0c71S89Cful04MsOE7iwNWB/view?usp=sharing) and open it with Illustrator.

### Problems with simply fixes  

1. Visual association of geometry and label    
2. Line art versus polygon data  
    - overlapping lines  
    - label placement  
3. Inner glow and different feature sizes
4. Spell checker   

### Problems with complicating fixes (clipping masks)  

_Clipping masks make it frustrating, difficult, or impossible to edit and work with your layers, so these two workflows should be the last things that you do in Illustrator._  

### Get organized  

1. Put labels into one folder.  
    - Can be all labels or just label groups with line conflicts.  
2. Put linework into a separate folder.  
3. Put base layer fills into a separate folder.  
4. Always save your work before applying clipping masks.  
    - In fact, you should consider making a copy of the ai file before applying clipping masks. They can be pretty cruel and destructive if you mess up.  

### Clip base layer fills by map extent.  

1. Make a copy of map extent.  
2. Place copy in folder with base layers.
3. Make sure map extent object is the top-most layer.
4. Select all objects in layer group.
5. Make/Release clipping mask (bottom of panel, middle button).   

### Knock out lines behind labels

1. Make a copy of any labels that you don’t want to see lines running through and put them in a single layer.
2. Select> Object> Expand> Object and fill  
3. Ungroup   
4. Object> Path> Offset path  
    - adjust so there are no spaces in between characters)  
    - use Round join  
5. Select all, Pathfinder> Unite  
6. Select all, Ungroup    
7. Select all, Object>Compound Path>Make    
8. Grab your map extent (or interior of map frame, if applicable)
9. Put rectangle under compound path of labels  
10. Path finder > Minus front  
11. Delete islands if necessary  
    - You should have one object as a result of the pathfinder operation.  
    - If you have more than one, see if the little ones are 'islands', or little paths created in small negative spaces.  
    - If so, delete the little paths.
12. Ungroup (if necessary)  
13. Make a copy of mask  
14. Use it as a clipping mask  
    - As described above, put the in the folder with the linework you want to knock out.  
    - Make sure mask is at the top of the layer stack.
    - Make/release clipping mask button at bottom center of layer panel.  

_Please note: if you change the position of a label after you have made and applied the mask, you will need to repeat workflow with new mask_.  

### Remaining problem  

- What conflict remains between labels and base lines?  
- What causes the conflict?  
- How can we fix it?  

### Advanced parallel line styling  

Many maps make use of parallel lines to represent events on a path.  

<center>

![metro maps](https://kickmap.com/images/mta_kick_vign_maps.jpg)

_NCY subway, Kick map, Vignelli subway map_  

![Brooklyn marathon](https://bklyner.com/content/images/bklyner/wp-content/uploads/2019/10/NYCRUNS_Brooklyn2019_Map_v12_FULL_05.10.19-1-1035x800.png)  

[_Brooklyn marathon course map_](https://nycruns.com/wp-content/uploads/2022/04/NYCRUNS_2022_Brooklyn_Course_Marathon_v4_04.17.22.pdf)  

</center>  

More than ten years ago, Chester Harvey '10 made a couple of short tutorials on strategies for making parallel lines with Illustrator. You may find them helpful if you are working with parallel lines in your second project.  

- [Part 1](https://youtu.be/gWlmeIT0hWI)  

- [Part 2](https://youtu.be/J9V9tQUBRE4)  
