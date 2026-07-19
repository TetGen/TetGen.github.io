# .stl - Stereolithography file format

The .stl or stereolithography format is an ASCII or binary file used
in manufacturing. It is a list of the triangular surfaces that describe
a computer generated solid model. This is the standard input for most rapid
prototyping machines. 

<!---
The description of .stl file format can be easily found elsewhere in
the internet.  An elaborated description can be found at <a
href="http://www.sdsc.edu/tmf/Stl-specs/stl.html">here</a>. Below is
an example of this file format. 
--->

<pre><tt> solid
 ...</tt></pre>

<pre><tt> facet normal 0.00 0.00 1.00
    outer loop
      vertex  2.00  2.00  0.00
      vertex -1.00  1.00  0.00
      vertex  0.00 -1.00  0.00
    endloop
  endfacet
 ...
 endsolid</tt>
</pre>


Here is an example of using TetGen to read (-p) a polyhedron described
in .stl file format (<a href="https://codeberg.org/TetGen/TetGenTests/src/branch/main/tetgen/sphere.stl">sphere.stl</a>),
compute its constrained Delaunay tetrahedralization.

<pre>
tetgen -p sphere.stl
</pre>

The picture of the sphere.<br>
<img src="../figs/fffigs/sphere-plc.gif"><br>
Source file: <a href="https://codeberg.org/TetGen/TetGenTests/src/branch/main/tetgen/sphere.stl">sphere.stl</a>

