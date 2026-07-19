# .mesh - Medit's mesh file format



.mesh is the file formats of <a
href="http://www-roc.inria.fr/gamma/gamma/Accueil/index.fr.html">Medit</a> - an
interactive 3D mesh viewing program.  This file format is described in
the documentation of Medit. 

Here is an example of using TetGen to read (-p) a surface mesh
described in .mesh file format, compute its constrained Delaunay
tetrahedralization and output (-g) the CDT in .mesh file format.

<pre>
tetgen -pg input_file.mesh
</pre>

<!---
A repository of free 3D models in .mesh file format are available
at INRIA's <a href="http://www-c.inria.fr/gamma">Free 3D Meshes
Download</a>.
--->
