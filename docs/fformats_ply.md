# .ply - Polyhedral file format

The .ply file format is a simple object description that was designed
as a convenient format for researchers who work with polygonal
models. Early versions of this file format were used at Stanford
University and at UNC Chapel Hill.

<!---
A description as well as examples, codes of the PLY file format can be
found at this <a
href="http://astronomy.swin.edu.au/~pbourke/geomformats/ply">link</a>.
--->

Below is the complete ASCII description for a cube.  The header of a binary
version of the same object would differ only in substituting the word
"binary_little_endian" or "binary_big_endian" for the word "ascii".  The
comments in brackets are NOT part of the file, they are annotations to this
example.  Comments in files are ordinary keyword-identified lines that begin
with the word "comment".
</p>

<pre>
ply
format ascii 1.0           { ascii/binary, format version number }
comment made by Greg Turk  { comments keyword specified, like all lines }
comment this file is a cube
element vertex 8           { define "vertex" element, 8 of them in file }
property float x           { vertex contains float "x" coordinate }
property float y           { y coordinate is also a vertex property }
property float z           { z coordinate, too }
element face 6             { there are 6 "face" elements in the file }
property list uchar int vertex_index { "vertex_indices" is a list of ints }
end_header                 { delimits the end of the header }
0 0 0                      { start of vertex list }
0 0 1
0 1 1
0 1 0
1 0 0
1 0 1
1 1 1
1 1 0
4 0 1 2 3                  { start of face list }
4 7 6 5 4
4 0 4 5 1
4 1 5 6 2
4 2 6 7 3
4 3 7 4 0
</pre>


This example demonstrates the basic components of the header.  Each part 
of the header is a carriage-return terminated ASCII string that begins with a 
keyword.  Even the start and end of the header ("ply<cr>" and 
"end_header<cr>") are in this form.  The characters "ply<cr>" must be the 
first four characters of the file, since they serve as the file's magic 
number.  
</p>


<!---
Some free 3D models described in PLY file format can be found at <a
href="http://www.cs.northwestern.edu/~watsonb/teaching/351/Models">here</a>
(many thanks Edward Verbree at TU Delft for this link).
--->

