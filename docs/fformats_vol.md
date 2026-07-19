# .vol files</font>


<ul>
<li> First line:  &lt;# of tetrahedra&gt;
<li> Remaining lines list of # of maximum volumes:<br> 
     &lt;tetrahedron #&gt; &lt;maximum volume&gt;<br>
     ...
</ul>

A .vol file associates with each tetrahedron a maximum volume which is
used for mesh refinement. It is read by TetGen in case the -r switch
is used.

As with other file formats, every tetrahedron must be represented, and
they must be numbered consecutively.  A tetrahedron may be left
unconstrained by assigning it a negative maximum volume.
