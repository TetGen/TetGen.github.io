# Piecewise Linear Complex

Three-dimensional geometric objects are often more complicated than
polyhedra, TetGen uses a more general input called <em>piecewise
linear complex</em> (PLC).  A PLC <em>X</em> is a set of vertices,
segments and <em>facets</em> as shown in the following figure:

<center>
<img src="../figs/plc-1.gif">
</center>

 
Each facet is a polygonal region, it may have any number of sides and
may be non-convex, possibly with holes, segments and vertices in it. A
facet can represent any <em>planar straight line graph</em> (PSLG),
which is a popular input model used by many two-dimensional mesh
algorithms. A facet is actually a PSLG embedded in three
dimensions. An example is given in the above figure, the shaded area
highlights a facet.

PLCs have restrictions like any other complex. For a PLC <em>X</em>, the
elements of <em>X</em> must be closed under intersection. For example, two
segments only can intersect at a common vertex which is also in
<em>X</em>. Two facets of <em>X</em> may intersect only at a shared segment or
vertex or a union of shared segments and vertices (because facets are
non-convex). The following figures show non-closed configurations
for examples.

<center>
<img src="../figs/non-plc1.gif">
<img src="../figs/non-plc2.gif">
</center>

Another restriction of the facets of PLCs is that the point set which
used to define a facet must be coplanar.

Any polyhedron is a PLC. Furthermore, PLCs are more flexible than
polyhedra to represent three-dimensional geometric objects. For
example, the shaded facet in the above figure can not be represented
by any polygon. For domains having curved surfaces (which are not
piecewise linear), the surface triangulations are previously required,
hence, PLCs can approximately represent any three-dimensional domain.
Following are some examples of PLCs represented by surface meshes.

<center>
<img src="../figs/engine-plc-s.gif">
<img src="../figs/hand-plc-s.gif">
</center>

