# Week 5 · Designing with Algorithms

We'll examine this week how contemporary designers are implementing iterative algorithmic processes to address complex design problems.

In particular, we'll look at the related [Delaunay Triangulation](https://en.wikipedia.org/wiki/Delaunay_triangulation) and [Voronoi Tesselation](https://en.wikipedia.org/wiki/Voronoi_diagram) — simple mathematical models for complex natural phenomena.

-----

### References for the Week

Some examples of pattern algorithm design work.

- [Voronoi at Thingiverse](https://www.thingiverse.com/search?q=voronoi)
- [Jerusalem Table](https://www.core77.com/projects/39363/Jerusalem-Tables)
- [Nervous System](https://n-e-r-v-o-u-s.com/projects/)
- [Marc Newson Voronoi Shelf](http://marc-newson.com/voronoi-shelf/)
- [Go Wheel Chair](http://layerdesign.com/projects/go/)
- [Bespoke 3D Orthopedics Brace](https://www.youtube.com/watch?v=OGRkNexY3N8)
- [Interactive Subdivision](https://www.khanacademy.org/partner-content/pixar/modeling-character/modeling-subdivision/p/interactive-subdivision-in-3d)
- [Unyq](http://unyq.com/en-us/us/)
- [Osteoid Ultrasonic Cast](https://competition.adesignaward.com/design.php?ID=34151)
- [Cortex Cast](http://www.evilldesign.com/cortex)
- [Thermal Comfort Casts](https://3dprint.com/192877/3d-printed-cast-thermal-comfort/)
- [XKELET Hand and Wrist Fracture Cast](https://www.xkelet.com/en/)
- [How to Hand Draw Delaunay and Voronoi](http://765.blogspot.com/2009/09/how-to-draw-voronoi-diagram.html)
- [Simple Interactive Voronoi Editor](http://www.sygreer.com/projects/voronoi/)
- [Interactive Javascript Translation](http://paperjs.org/examples/voronoi/)
- [World Capitals Voronoi](https://www.jasondavies.com/maps/voronoi/capitals/)
- [In D3 Data Viz Library](https://github.com/d3/d3-delaunay)
- [Anna Nowak on Application of Voronoi diagrams in contemporary architecture and town planning](https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-5259df1a-e1f7-442f-a68c-10c0c2b35c96/c/chmot62_06.pdf)
- [All the Maths](http://cgl.uni-jena.de/pub/Workshops/WebHome/cgl12new.pdf)
- [Easier to Understand All the Maths](https://meemoo.org/blog/2014-07-14-noflo-geometry)


-----


### Triangulation, Tesselation, Subdivision

#### Delaunay Triangulation

![del](https://i.pinimg.com/originals/76/c1/a2/76c1a2a0222ff50861797b6152db8aa2.jpg)

Developed in the 1930s by Russian geometer [Boris Delaunay](https://en.wikipedia.org/wiki/Boris_Delaunay), the [Delaunay triangulation](https://en.wikipedia.org/wiki/Delaunay_triangulation) is essential to nearly all computer graphics. Whenever you hear or talk about a 'mesh', that's likely based on a Delaunay Triangulation! Videogames, visual effects for cinema, medical scanning, arcGIS geographic data — everything! It is also in heavy use by structural engineers, and unintentionally undergirds nearly all of the truss geometries that define bridges, attics, and other triangular structures as well as communication network routing. More recently, as autonomous vehicles begin to explore unmapped areas where sensors may fail, Delaunay Triangulation logic is used to [allow intelligent agents to navigate dangerous boundaries](https://en.wikipedia.org/wiki/Constrained_Delaunay_triangulation). 

In 3D space, the triangulation creates a *network topography* of triangular cells, based on known points to support, which would use the minimal amount of connective material to maintain, in opposition to a *singular force vector*. Imagine the Delaunay set as the circus net for trapeze artists, which would stretch and deform as the gymnasts fall into it and bounce around in it. That same net would not work very well to catch someone launched into it from the side...

To produce a Delaunay Mesh...

- Sprinkle random points on a 2D plane
- Draw all possible circles defined by any of the 3 points
- If those circles contain *any* of the sprinkled points, that circle should be discarded
- If a circle passes the test, then draw the [circumscribed triangle](https://en.wikipedia.org/wiki/Circumscribed_circle) as an edge

![delaunay supports](delSample.jpg)

-----

#### Voronoi Tesselation

![voronoi](http://datagenetics.com/blog/may12017/anim2.gif)

![del vor](http://meemoo.org/images/delaunay_voronoi_dual.gif)

The geometric [*dual*](https://en.wikipedia.org/wiki/Dual_polyhedron) of the Delaunay Triangulation, [Voronoi Tesselation](https://en.wikipedia.org/wiki/Voronoi_diagram) invented by another amazing Russian mathematician — [Georgy Voronoi](https://en.wikipedia.org/wiki/Georgy_Voronoy) — similarly tiles a plane with shapes — though not not usually triangles. The unusual cells that come out of the Voronoi Tesselation model fairly accurately a multitude of natural formal phenomena as well as behaviors. Bone microstructure, sponge anatomy, soil clumping, termite and bee architecture, neuron network arrangement.... the list is almost endless. This is because the Voronoi Tesselation models an *efficient* set of cells. All of the space within a single Voronoi cell is *closer* to the centroid of a Delaunay triangle, and as a result, Voronoi logic approximates how any agent might make a decision about which of a set of possible choices should be chosen based purely on efficiently traversing or covering a plane or volume. It is increasingly being used by public policymakers to [place train stops, design road networks](http://datagenetics.com/blog/may12017/index.html), and [predict crime](https://www.tandfonline.com/doi/abs/10.1080/00330124.2017.1288578?scroll=top&needAccess=true&journalCode=rtpg20).

- Generate a Delaunay Triangulation
- Find the midpoint of each edge, and draw a line perpendicular to the edge
- Intersect all these lines, and clip adjacent lines with one another
- Draw the remnant, irregular polygons

![bone](https://afinemesh.files.wordpress.com/2014/04/printed-voronoi.jpg)

-----

### Grasshopper Algorithmic Forms


#### Delaunay Construction

From a field of random points, manually create a Delaunay triangulation from container circles.

[Download](delaunay-definition.gh)

![Grasshopper Definition](delaunay-grasshopper.png)

![Grasshopper Screenshot](delaunay-screenshot.png)

-----

#### Voronoi Construction

From a structured grid, create a set of discrete Voronoi bounds using only closest point logic.

[Download](voronoi-attractor-definition.gh)

![Grasshopper Definition](voronoi-attractor-grasshopper.png)

![Grasshopper Screenshot](voronoi-attractor-screenshot.png)

-----

#### Simple Voronoi Region Coloring with Delaunay Connectivity

View these algorithms at work, in combination, on random data....


[Download](simple-definition.gh)

![Grasshopper Definition](simple-grasshopper.png)

![Grasshopper Screenshot](simple-screenshot.png)

-----

#### Voronoi Food Regions in Chicago

Based on [these neighborhood bounds](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Neighborhoods/bbvz-uum9) and these [grocery store locations](https://data.cityofchicago.org/Community-Economic-Development/Grocery-Stores-2013/53t8-wyrc), let's use the Voronoi algorithm to try to predict which grocery store any given resident might visit.

Download the pre-processed [neighborhood boundaries](neighborhoodDiscontinuities.txt) and [grocery store](groceryStores.csv) coordinates.

[Download](grocery-definition.gh)

![Grasshopper Definition](grocery-grasshopper.png)

![Grasshopper Screenshot](grocery-screenshot.png)

-----

#### Geographic Data Sample

Sculpt real data into form in Grasshopper using this [dataset on the geographic position of capital cities](capitalCities.txt). This Grasshopper file produces a map and globe similar in intent to this [interactive page](https://www.jasondavies.com/maps/voronoi/capitals/) attempting to reveal the mismatch between geopolitical governing structures and geography. 

[Download](voronoi-geographic-definition.gh)

![Grasshopper Definition](voronoi-geographic-grasshopper.png)

![Grasshopper Screenshot](voronoi-geographic-screenshot.png)

-----

### Homework

To come!