# .face files

<ul>
<li> First line:  &lt;# of faces&gt; &lt;boundary marker (0 or 1)&gt;
<li> Remaining lines list of # of faces:<br> 
     &lt;face #&gt; &lt;node&gt; &lt;node&gt; &lt;node&gt; [boundary marker]<br>
     ...
</ul>

A .face file contains a list of triangular faces, which may be
boundary faces (if -p or -r switch is used), or convex hull
faces. Each face has three corners and possibly has a boundary
marker. Nodes are indices into the corresponding .node file.<p>

After generating a mesh or Delaunay tetrahedralization, TetGen default
outputs the boundary faces or the convex hull into a .face
file. However, this file can be omitted by -F switch.  If -r switch is
used, TetGen can also read the .face file for identifying boundary
faces in a reconstructed mesh. The optional column of Boundary markers
is suppressed by the -B switch.<p>

If the boundary marker in the first line is '1', each face has an
additional boundary marker (an integer) in the last column.  Boundary
markers of facets are defined in the .poly or the .smesh files. They
are tags used mainly to identify which faces of the tetrahedralization
are associated with which PLC facet, and to identify which faces occur
on a boundary of the tetrahedralization.  A common use is to determine
where different boundary condition types should be applied on boundary
faces.

