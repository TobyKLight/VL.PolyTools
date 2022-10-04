# VL.PolyTools
Tools for working with Polygons and Polypaths in vvvv gamma. 

Polygon = shape made only of lines, Polypath = shape made of lines and curves

See the helppatches for a more detailed overview

# To Install
Grey menu (top left)>Manage Nugets>Command Line 

Type
```nuget install VL.PolyTools -Version 1.0.3```

# What kind of things does it do? 

![image](https://user-images.githubusercontent.com/4467208/193471641-538d34a3-54cb-481e-b99e-4a1eda421d92.png)

Interactive Helppatches


![VL PolyTools FOV Calc](https://user-images.githubusercontent.com/4467208/193471193-00f37121-4291-4f5e-96b8-f6f1b4862b12.gif)

Visibility from a point inside a polygon 
(Using Expanding Triangles method by Francisc Bungiu, Michael Hemmer, John Hershberger, Kan Huang and Alexander Kröller)


![VL PolyTools 3D Extrude](https://user-images.githubusercontent.com/4467208/193471211-3fbd4d82-f38c-4a37-9a2d-0c6f1e720fc5.gif)

3D extrusion of Polygons in stride


![VL PolyTools Polypath Union](https://user-images.githubusercontent.com/4467208/193471293-660766b1-8c12-4399-a1cc-a2049c15494b.JPG)

Union of PolyPaths including internal compartment lines. 


![VL PolyTools Cutting A Poly into Compartments](https://user-images.githubusercontent.com/4467208/193478760-e1ad7721-a4ae-4d34-a3ba-d15dc5c67208.gif)

Cutting a PolyPath into compartments

Bonus see included 'SKPathUtils.vl' if you are looking for low level ways to extend SKPaths


# Dependencies
Made with vvvv Gamma 2021.4.10

com.angusj.Clipper -Version 6.4.2

https://sourceforge.net/projects/polyclipping/

https://www.nuget.org/packages/com.angusj.Clipper

credit Angus Johnson, gylee
 

LibTessDotNet
https://github.com/speps/LibTessDotNet

https://www.nuget.org/packages/LibTessDotNet

credit https://github.com/speps/LibTessDotNet/graphs/contributors

# Special Thanks
@Untone for help unlocking the SKPath verbs for use in vvvv gamma

# Version History
V1.0.3

-Helppatch improvements

-Consistent GetBounds method for Polygon and PolyPath

-Added Splitting Circles Example patch kindly contributed by ██ ██

-Added option to Compartments to avoid including outer stroke

 

# License

Boost 1.0
