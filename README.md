# VL.PolyTools
Tools for working with Polygons and Polypaths in vvvv gamma. 

Polygon = shape made only of lines, Polypath = shape made of lines and curves

See the helppatches for a more detailed overview

# To Install
Grey menu (top left)>Manage Nugets>Command Line 

Type
```nuget install VL.PolyTools```

# What kind of things does it do? 

![image](https://github.com/TobyKLight/VL.PolyTools/assets/4467208/8f598eec-f057-40ab-8c57-2e13ff3787f6)
Interactive Helppatches

![PolyTubeStars](https://github.com/TobyKLight/VL.PolyTools/assets/4467208/5986ffa5-9d8d-4c73-aea9-80f3213ac98a)

Polygon Tube


![NormalMappedTube](https://github.com/TobyKLight/VL.PolyTools/assets/4467208/19301827-0490-49e9-a320-359cd1e0e48a)

Polygon Tube with normal mapping

![LerpDemo](https://github.com/TobyKLight/VL.PolyTools/assets/4467208/e7a47c1c-5f02-45af-bd93-1374cdacf694)

Lerp between 2D Polygons in 2D and 3D

![VL PolyTools FOV Calc](https://user-images.githubusercontent.com/4467208/193471193-00f37121-4291-4f5e-96b8-f6f1b4862b12.gif)

Visibility from a point inside a polygon 
(Using Expanding Triangles method by Francisc Bungiu, Michael Hemmer, John Hershberger, Kan Huang and Alexander Kröller)


![VL PolyTools 3D Extrude](https://user-images.githubusercontent.com/4467208/193471211-3fbd4d82-f38c-4a37-9a2d-0c6f1e720fc5.gif)

3D extrusion of Polygons in stride


![VL PolyTools Polypath Union](https://user-images.githubusercontent.com/4467208/193471293-660766b1-8c12-4399-a1cc-a2049c15494b.JPG)

Union of PolyPaths including internal compartment lines. 


![VL PolyTools Cutting A Poly into Compartments](https://user-images.githubusercontent.com/4467208/193478760-e1ad7721-a4ae-4d34-a3ba-d15dc5c67208.gif)

Cutting a PolyPath into compartments

![VL.PolyTools extruded polygon with normal mapping](https://github.com/TobyKLight/VL.PolyTools/assets/4467208/c90eb722-16ab-4c8d-8ff8-117dd71a29ac)

An extruded Polygon with Normal mapping

Bonus see included 'SKPathUtils.vl' if you are looking for low level ways to extend SKPaths

# Dependencies
Made with vvvv Gamma 5.3-0088

com.angusj.Clipper -Version 6.4.2

https://sourceforge.net/projects/polyclipping/

https://www.nuget.org/packages/com.angusj.Clipper

credit Angus Johnson, gylee
 

LibTessDotNet
https://github.com/speps/LibTessDotNet

https://www.nuget.org/packages/LibTessDotNet

credit https://github.com/speps/LibTessDotNet/graphs/contributors

Geometry3Sharp
https://github.com/gradientspace/geometry3Sharp

# Special Thanks
@Untone for help unlocking the SKPath verbs for use in vvvv gamma

# Version History
V1.4.2a2 
* Fixed red nodes in helppatch 'Example SVG Path Extract', thanks @antokhio 


V1.4.1 
* Fixed a Polygon2DPlus helpatch 
* Added new function RadialSort as a way to generate a polygon from unordered points, in simple cases. 

V1.4.0
* !Breaking Change! Fixed error in the Polygon2DPlus Join method that takes 3D polygon points and a normal 
* !Breaking Change! Renamed 'LineSegmentIntersectsBox' to just 'LineIntersectsBox' to make consistent with similar functions  
* Added new function LineIntersectsRectangle and helppatch. 
* Fixed bug TransformsOnLine where it didn't normalise internal direction vector 
* Fixed Bug PolyTubeMesh where it would reverse the direction of 2D data but not 3D data.  
* Improved debug out data on PolyTubeMesh 
* Added new function and helppatch 'find if points are on a line' 
* Added new function and helppatch 'Interpolate points in a triangle'
* Added new function and helppatch 'Calculate normal of a line segment 2d'  

V1.3.0 
* !Breaking Changes! Re-categorisation of some nodes into new Line category. Some line related functions may have red nodes. Double click on them, clear their existing associations in the bottom right and search again for the name and you should find the same nodes.  
* !Breaking Change! All polytubes need their input 'Polygon2DPlus' types to have heightmode=1 (Y=height). This is now consistent, was 0 on some old helppatches. 
* Added 3D Triangle Intersection, see helppatch. 
* Exposed RayIntersectsTriangle from Stride.Core.Mathematics 
* Added a helppatch for Solving a Triangle in 3D and a node for finding the third point of a triangle if you know some constraints about the first two points. 
* Added function for finding a 3D Line segment intersects a box with helppatch 
* Added new dependency Geometry3Sharp https://github.com/gradientspace/geometry3Sharp. Currently only using this for a few intersections but has potential to do a lot more in this package. It's Boost 1.0 licence (like clipper). 
* Added LinePoints utility drawing function for stride 
* Added Plane (Plane) utility drawing function for stride, this takes a Plane mathematical struct as input, however note this has some limitations as the struct is infinite and we are drawing a finite plane. Basically just make it really big. 
* Exposed Normal input on LibTessDotNet Triangulation nodes. Triangulation nodes are 2D but it can be necessary to set the face direction in 3D use. See the CalcTubeEndCaps process inside PolyTubes for an example usecase. 
* Improved TransformsOnSpline and TransformOnLine nodeset where you specify either ForwardVectors or a single ForwardVector. See the "Tube On Path" helppatch for an explanation. This is less confusing for their usecases where the UpVector of the Spline/Line is the Y axis, and results in less weird singularity twists in tubes. The previous nodes are still included in obsolete category.  


V1.2.2 
* Bugfixes with dependencies 

V1.2.0
* !Breaking Change! Refactored categories for some of the Polygon3D nodes to make it clearer The actual nodes are still the same, you may have to double click red nodes in your apps and retype the names to recreate them.
* !Breaking change! Bugfix on winding direction node. With the calculation method I was using winding direction is potentially flipped in some spaces where Y is inverted. Between Stride and Skia we have a mix of spaces where this might be true. There is now a 'YIncreasesDownward' pin on the WindingDirection and ForceClockwise/CounterClockwise nodes. Check the helppatch 'HowTo Calculate Winding Direction Of A Polygon' 
* New Polygon2DPlus datatype, for a 2D polygon that is effectively annotated with a third dimension. The underlying 2D polygon can still be accessed and manipulated. 
* Rearranged helppatches to make general geometric functions clearer
* Added sample a point on a line 
* New 3D functions for dynamic geometry to make 'polygon tubes', where each element of the tube can have a different polygon face. See the new helppatches in 3D category.
* LERP (morph) between two polygons, see HowTo LERP between Polygons helppatch
* Added sample a point on a polygon perimeter (previously only for PolyPath) 
* Added DrawPolygonRadialLines to draw radial lines between origin and points 
* Added DrawPolygonPointLabels to draw text labels at each point on a polygon  
* Improved the TriangleContainsPoint helppatch  
* Aspect changed on PolygonVisibility nodes to advanced. 
* Added PointCount operation to Polygon datatype 

V1.1.3 
* Removed stride physics Raycast function now there is a native one shipped with vvvv 5.3 

V1.1.2 
* PolygonExtrude now has an additional 2D UV scaling option for the sides of the extrude. (Was U only in last release) 

V1.1.1 
* Rearranged and expanded the helppatches for PolygonPlane and PolygonExtrusions 
* Added option to generate tangents, needed for normal (bump) mapping 
* Added many options for texture mapping the 3D polygon objects 
* For those planning to make their own dynamic meshes or models in stride the PolygonPlane and PolygonExtrusion patches are reasonably well documented examples, including with UV coordinates, tangents and bounding boxes. 
* Added some tools for debugging stride entities as wireframe, vertices, tangents etc

V1.1.0
* Tested in vvvv gamma 5.0-stable 
* Added UV map to the ExtrudedPolygon. This is not intended for every usecase but should be a good starting point. 
* Fixed another bug with bounding boxes of PolygonPlane and ExtrudedPolygons that caused incorrect culling. 
* Minor breaking change due to new signature of PolygonPlane and ExtrudedPolygon nodes (so they go red). Just double click on them and recreate them and you should be good to go. 

V1.0.10
* Minor improvement to 3D polygon plane and extrusion nodes and helppatch 
* Can set custom bounding box depth for the 3D polygon plane 

V1.0.9 
* Stride dependencies moved to separate document VL.PolyTools.Stride 

V1.0.8 
* Ensured compatibility with vvvv 2021.4.11-1313 (RC4) 
* Fxed some helppatch windows potentially not opening 

V1.0.7 

* Made the bugfix from V1.0.6 optional as 'Allow Perfect Diagonals' on  'HowTo Find Grid Cells Along A Line'

V1.0.6 

* Fixed bug in line intersects grid calculation 

V1.0.5 

* Added second 'Does Line Intersect Grid cells' operation including all cells. See helpatch 'HowTo Find Grid Cells Along A Line'


V1.0.4

* Added function for finding grid cells along a line based on Bresenhams Line Algorithm. See Helppatch 'HowTo Find Grid Cells Along A Line'
* Added function for generating square-ish layout grids using a single count input. I say square-ish because it handles cases where the input count does not have a whole square root and a partial row/column might be needed.  See HelpPatch 'HowTo Generate a nearly Square GridSpread'


V1.0.3

* Helppatch improvements
* Consistent GetBounds method for Polygon and PolyPath
* Added Splitting Circles Example patch kindly contributed by ██ ██
* Added option to Compartments to avoid including outer stroke

 

# License

Boost 1.0
