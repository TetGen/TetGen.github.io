# .smesh files

A .smesh file represents a <a href="plc.html">piecewise linear
complex</a> (PLC) as well as some additional information.  The .smesh
file format is a simplified version of the <a
href="fformats.poly.html">.poly</a> format, that each facet only has
exactly one polygon, no holes, no segment and point inside. It is less
flexible than the .poly file format but is much simpler and useful
when the surface mesh is created by other programs.

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
     &lt;# of corners&gt; &lt;corner 1&gt; &lt;corner 2&gt; ... &lt;corner #&gt; [boundary marker]<br>
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
the format of .node files. &lt;\# of points&gt; may be set to zero to
indicate that the points are listed in a separate .node file.

<a href="#part2">Part 2</a> lists all the facets. It is different from
the facet format of .poly file. Each facet in .smesh file only
consists of exactly one polygon. The corner list of each polygon can
be distributed over a number of lines. The optional boundary marker of
each facet is given at the end of the corner list.

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
the `-A` switch is used or `-a` switch without a number is invoked.
Regional attributes and volume constraints are propagated in the same
manner as holes. 

If two values are written on a line after the x, y and z coordinate,
the former is assumed to be a regional attribute (but will only be
applied if the `-A` switch is selected),
and the latter is assumed to be a regional volume constraint (but will
only be applied if the `-a` switch is
selected). It is possible to specify just one value after the
coordinates. It can serve as both an attribute and an volume
constraint, depending on the choice of switches. A negative maximum
volume constraint allows to use the -A and the -a switches without
imposing a volume constraint in this specific region.
