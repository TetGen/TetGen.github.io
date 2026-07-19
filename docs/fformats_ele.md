# .ele files

<ul>
<li> First line:  &lt;# of tetrahedra&gt; &lt;nodes per tetrahedron&gt;
&lt;# of attributes&gt;
<li> Remaining lines list of # of tetrahedra:<br> 
     &lt;tetrahedron #&gt; &lt;node&gt; &lt;node&gt; &lt;node&gt; &lt;node&gt; ... [attributes]<br>
     ...
</ul>

A .ele file contains a list of tetrahedra. Each tetrahedron has four
corners or ten corners (if -o2 switch is used).  Nodes are indices
into the corresponding .node file.  The first four nodes are the
corner vertices. If -o2 is used, the remaining six nodes are generated
on the midpoints of the edges of the tetrahedron. The following
picture shows how these nodes are numbered.

<img src="../figs/10-nodes.gif">


If the region attribute in the first line is '1', each tetrahedra has
an additional region attribute (an integer) in the last column.
Region attributes of tetrahedra are tags used mainly to identify which
tetrahedra of the tetrahedralization are associated with which
facet-bounded region of the PLC, set in the part 4 of a .poly or a
.smesh file.  Region attributes do not diffuse across facets, all
tetrahedra in the same region have exactly the same region
attribute. A common use of the region attribute is to determine which
material a tetrahedron has.

The .ele file is the default output file of TetGen if it generated a
mesh or tetrahedralization. However, it can be omitted by -E switch.
If -r switch is used, TetGen reads a .ele file and reconstructs a
tetrahedral mesh from it.


The following example illustrates the layout of the .ele file.


<pre><tt>
  154  4  0
      1       4   107     3    50
      2       4   108     3   107
      3       9    97    95    94
      4       4   107    50    93
      5      56     1    50    47
      6      94    98    97    95
      7      97     9    95    55
      8      52    55     5    51
      ...
</tt></pre>

