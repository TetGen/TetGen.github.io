# .node files


<ul>
<li> First line:  &lt;# of points&gt; &lt;dimension (must be 3)&gt;
&lt;# of attributes&gt; &lt;# of boundary markers (0 or 1)&gt;
<li> Remaining lines list # of points:<br> 
     &lt;point #&gt; &lt;x&gt; &lt;y&gt; &lt;z&gt; [attributes]
     [boundary marker]<br>
     ...
</ul>

A .node file contains a list of three-dimensional points. Each point
has three coordinates (x, y and z), probably has one or several
attributes, and a boundary marker as well. It is used as both input
and output files to represent the point set of a PLC, or the point set
of a mesh, or a set of additional points (for -i switch) which need to insert
into the mesh. The example below demonstrates the layout of the
.node file.

<pre><tt>
  # Node count, 3 dim, no attribute, no boundary marker
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
</tt></pre>


The attributes, which are typically floating-point values of physical
quantities (such as mass or conductivity) associated with the points,
are copied unchanged to the output mesh.  If -p switch is used, each
new Steiner point inserted on segments of the mesh has attributes
assigned to it by linear interpolation.  Furthermore, if -q, -a, or -i
is selected, each new point added to the mesh to improve mesh quality
has attributes zero.

If the fourth entry of the first line is '1', the last column of the
remainder of the file is assumed to contain boundary markers.
Boundary markers are used to identify boundary points (points resting
on PLC facets).  The .node file produced by TetGen contains boundary
markers in the last column unless they are suppressed by the -B
switch.  The boundary marker associated with each point in an output
.node file is chosen as follows:

<ul>
  <li> If a point is assigned a nonzero boundary marker in the input
       file, then it is assigned the same marker in the output .node file.
  <li> Otherwise, if the  node lies on a PLC facet with a nonzero boundary
marker, then the node is assigned the same marker that facet has. If the node
lies on several such facets, one of the markers is chosen arbitrarily.
  <li> Otherwise, if the node occurs on a boundary of the mesh, then the node
  is assigned the marker (1).
  <li> Otherwise, the point is assigned the marker zero (0).
</ul>


TetGen can determine which points are on the boundary, input with the
boundary marker zero (or use no markers at all) will result in output
with boundary marker (1) for all points on the boundary.
