# .neigh files

<ul>
<li> First line:  &lt;# of tetrahedra&gt; &lt;# of nei. per tet (always 4) &gt;
<li> Remaining lines list of # of neighbors:<br> 
     &lt;tetrahedron #&gt; &lt;neighbor1&gt; &lt;neighbor2&gt; &lt;neighbor3&gt; &lt;neighbor4&gt;<br>
     ...
</ul>

A .neigh file associates with each tetrahedron its neighbors (adjacent
tetrahedra), which are indices into the corresponding .ele file. An
index of <tt>-1</tt> indicates no neighbor (because the tetrahedron is on a
boundary of mesh domain).  The first neighbor of tetrahedron <tt>i</tt> is
opposite the first corner of tetrahedron <tt>i</tt>, and so on. It is output
by TetGen when -n switch is used.

