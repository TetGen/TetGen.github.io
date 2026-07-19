# .var files</font>

<ul>
<li> One line:  &lt;# of facet constraints&gt;
<li> Remaining lines list of # of facet constraints:<br> 
     &lt;constraints #&gt; &lt;boundary marker&gt; &lt;maximum area&gt;<br>
     ...
<li> One line:  &lt;# of segment constraints&gt;
<li> Remaining lines list of # of segment constraints:<br> 
     &lt;constraints #&gt; &lt;point1&gt; &lt;point2&gt; &lt;maximum
     length&gt;<br>
     ...
</ul>

A .var file allows you to specify variant constraints on
facets and segments. Like the maximum volume bound set to a region,
each facet can have a maximum area bound. On the output, no subface of
the facet has area larger that bound. Likewise, each segment can have
a maximum length bound, hence, the subsegments of that segment will no
longer than it.


Facet constraint is set on facet by specifying the boundary marker
which is the integer assigned that facet in the corresponding .poly or
.smesh file. Segment constraint is set to a segment by specifying two
indices of endpoints of the segment.


The following example illustrates the layout of a .var file. It can be used
together with the included file ``example.poly''.

<pre><tt>
# Facet constraints 
1             # 1 constraint  
1  2  0.5     # Set maximum area constraint (0.5) on all facets
              #   having boundary marker 2.

# Segment constraints
10               # 10 constraints
1  32 33  0.05   # Set maximum edge length constraint (0.05) on
                 #   segment with endpoints 32 and 33.
2  33 34  0.05
3  34 35  0.05
4  35 36  0.05
5  36 37  0.05
6  37 38  0.05
7  38 39  0.05
8  39 40  0.05
9  40 41  0.05
10 41 42  0.05
</tt></pre>
