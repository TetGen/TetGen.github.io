# .off - Geomview's polyhedral file format

<a
href="http://www.geomview.org/docs/html/geomview_41.html#SEC44">.off</a>
is the one of the popular file formats of <a
href="http://www.geomview.org">Geomview</a> - an interactive 3D
viewing program for Unix/Linux.  It represents collections of planar
polygons with possibly shared vertices, a convenient way to describe
polyhedra. The polygons may be concave but there's no provision for
polygons containing holes.  

The description of .off file format can be easily found elsewhere in
the internet.  Below is a simple discription of this file format. 

<code>
OFF
numVertices numFaces numEdges<br>
x y z<br>
x y z<br>
... numVertices like above<br>
NVertices v1 v2 v3 ... vN<br>
MVertices v1 v2 v3 ... vM<br>
... numFaces like above<br>

</code>


Note that vertices are numbered starting at 0 (not starting at 1), and
that numEdges will always be zero.


A simple example for a cube:


<code>
OFF<br>
8 6 0<br>
-0.500000 -0.500000  0.500000<br>
0.500000 -0.500000  0.500000<br>
-0.500000  0.500000  0.500000<br>
0.500000  0.500000  0.500000<br>
-0.500000  0.500000 -0.500000<br>
0.500000  0.500000 -0.500000<br>
-0.500000 -0.500000 -0.500000<br>
0.500000 -0.500000 -0.500000<br>
4 0 1 3 2<br>
4 2 3 5 4<br>
4 4 5 7 6<br>
4 6 7 1 0<br>
4 1 7 5 3<br>
4 6 0 2 4<br>
</code>



Here is an example of using TetGen to read (-p) a polyhedron described
in .off file format (<a href="https://codeberg.org/TetGen/TetGenTests/src/branch/main/tetgen/socket.off">socket.off</a>),
compute its constrained Delaunay tetrahedralization and output (-O)
the CDT in .off file format (socket.1.off).

<pre>
tetgen -pO socket.off
</pre>

The picture of the socket.<br>
<img src="../figs/fffigs/socket-plc.gif"><br>
Source file: <a href="https://codeberg.org/TetGen/TetGenTests/src/branch/main/tetgen/socket.off">socket.off</a>

<!---
A big repository of free 3D models in OFF file format are available at
<a href="http://shape.cs.princeton.edu/benchmark">The Princeton Shape
Benchmark</a>.  Please note, these models may not be <a
href="definitions.html#PLC">piecewise linear complexes</a>. You can
check them with the '-d' switch of
TetGen.
--->

