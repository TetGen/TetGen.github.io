# .edge files</font>

<ul>
<li> First line:  &lt;# of edges&gt;
<li> Remaining lines list of # of edges:<br> 
     &lt;edge #&gt; &lt;node&gt; &lt;node&gt;<br>
     ...
</ul>

A .edge file contains a list of edges, which are (sub)segments of a
PLC. Each edge has two endpoints which are indices into the
corresponding .node file. It is part of TetGen's output when -e switch
is used.
