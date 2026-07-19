# .poly files

A .poly file represents a [piecewise linear complex](plc.md) (PLC) 
as well as some additional information.  It consists
of four parts, which are a list of points, a list of facets, a list of
(volume) hole points, and a list of region attributes,
respectively. The first three parts are mandatory, but the fourth part
is optional.

<h4><a name="part1">Part 1 - node list</a></h4>
<ul>
<li> First line:  &lt;# of points&gt; &lt;dimension (must be 3)&gt;
&lt;# of attributes&gt; &lt;# of boundary markers (0 or 1)&gt;
<li> Remaining lines list # of points:<br> 
     &lt;point #&gt; &lt;x&gt; &lt;y&gt; &lt;z&gt;[attributes] [boundary marker]<br>
     ...
</ul>

<h4><a name="part2">Part 2 - facet list</a></h4>
<ul>
<li> One line: &lt;# of facets&gt; &lt;boundary markers (0 or 1)&gt;
<li> Following lines list # of facets: <br>
     &lt;facet #&gt;<br>
     ...
</ul>

where each &lt;facet #&gt; has the following format:
<ul>
<li> One line: &lt;# of polygons&gt; [# of holes] [boundary marker]
<li> Following lines list # of polygons:<br>
     &lt;# of corners&gt; &lt;corner 1&gt; &lt;corner 2&gt; ... &lt;corner #&gt;<br>
     ...
<li>  Following lines list # of holes:<br>
       &lt;hole #&gt; &lt;x&gt; &lt;y&gt; &lt;z&gt;<br>
       ...
</ul>

<h4><a name="part3">Part 3 - hole list</h4>

<ul>
<li> One line: &lt;# of holes&gt;
<li> Following lines list # of holes:<br>
     &lt;hole #&gt; &lt;x&gt; &lt;y&gt; &lt;z&gt;<br>
     ...
</ul>

<h4><a name="part4">Part 4 - region attributes list</h4>

<ul>
<li> One line: &lt;# of region&gt;
<li> Following lines list # of region attributes:<br>
     &lt;region #&gt; &lt;x&gt; &lt;y&gt; &lt;z&gt;&lt;region number&gt;&lt;region attribute&gt;<br>
     ...
</ul>


<a href="#part1">Part 1</a> lists all the points, and is identical to
the format of <a href="fformats.node">.node</a> files. &lt;\# of
points&gt; may be set to zero to indicate that the points are listed
in a separate .node file.

<a href="#part2">Part 2</a> lists all the facets. To understand the
format of a facet is crucial. Each facet is a planar straight line
graph (PSLG), i.e., it is a polygonal region which may contain
segments, single points and holes in it.  A list of <em>polygons</em>
is used to represent a facet. Each polygon has <tt>n</tt> corners,
<tt>n >= 1</tt>. The polygon can be degenerate, i.e., <tt>n = 1</tt> or
<tt>n = 2</tt> represents a single point or a segment, respectively.

A hole in a facet (don't confuse with the volume hole below) is
sepcified by identifying a point inside the hole. However, this point
need not be exactly in the hole, as long as its orthogonal projection
onto this facet is in the hole. The list of hole points
(consecutively) follows the list of polygons.

If the boundary markers is '1', TetGen will produce an additional
boundary marker for each face in .face file (in the last column of
each record). You can prevent boundary markers from being written into
.face file by using the -B switch.

Boundary markers of facets are tags used mainly to identify which
faces of the tetrahedralization are associated with which PLC facet,
hence identify which faces occur on a boundary of the
tetrahedralization.  A common use is to determine where the boundary
conditions should be applied to a mesh.

<a href="#part3">Part 3</a> lists all holes in the volume. Each holeis
specified by identifying a point inside it. After the constrained
Delaunay tetrahedrization is formed, TetGen creates holes by removing
tetrahedra. Thus exactly is the reason why TetGen requires a closed
boundary of the PLCs. In case of non closed PLC facets the whole
tetrahedrization will be 'eaten' away. If two tetrahedra abutting a
subface are removed, the subface itself is also vanished. Hole points
have to be placed inside a region, else the rounding error determines
which side of the facet is being transformed into the hole.

<a href="#part4">Part 4</a> (optional) lists regional attributes (to
be assigned to all tetrahedra in a region) and regional constraints on
the maximum tetrahedron volume. TetGen will read this section only if
the <a href="switches.AA.html">-A</a> switch is used or the <a
href="switches.a.html">-a</a> switch without a number is invoked.
Regional attributes and volume constraints are propagated in the same
manner as holes. 

If two values are written on a line after the x, y and z coordinate,
the former is assumed to be a regional attribute (but will only be
applied if the <a href="switches.AA.html">-A</a> switch is selected),
and the latter is assumed to be a regional volume constraint (but will
only be applied if the <a href="switches.a.html">-a</a> switch is
selected). It is possible to specify just one value after the
coordinates. It can serve as both an attribute and an volume
constraint, depending on the choice of switches. A negative maximum
volume constraint allows to use the -A and the -a switches without
imposing a volume constraint in this specific region.

In the following, a 1x1x1 cube is described by the poly file format.


<pre><tt>
  # Part 1 - node list 
  # node count, 3 dim, no attribute, no boundary marker
  8  3  0  0
  # Node index, node coordinates
  1  0.0 0.0 0.0
  2  1.0 0.0 0.0
  3  1.0 1.0 0.0
  4  0.0 1.0 0.0
  5  0.0 0.0 1.0
  6  1.0 0.0 1.0
  7  1.0 1.0 1.0
  8  0.0 1.0 1.0

  # Part 2 - facet list
  # facet count, no boundary marker
  6  0
  # facets
  1            # 1 polygon, no hole, no boundary marker
  4  1 2 3 4   # front
  1
  4  5 6 7 8   # back
  1
  4  1 2 6 5   # bottom
  1
  4  2 3 7 6   # right
  1
  4  3 4 8 7   # top
  1
  4  4 1 5 8   # left
  
  # Part 3 - hole list
  0            # no hole

  # Part 4 - region list
  0            # no region
</tt></pre>
