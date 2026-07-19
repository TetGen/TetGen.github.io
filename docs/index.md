
TetGen - A Quality Tetrahedral Mesh Generator and a 3D Delaunay Triangulator
=============================================================================
This  is a draft homepage for the TetGen mesh generator. For up-to-date information,
see the [TetGen repository](https://codeberg.org/Tetgen/TetGen).

<center>
<img src="figs/Delaunay-Voronoi-3D.gif" width="200" height="241">
[Explanation of the logo](logo.md)
</center>

## Purpose
TetGen is a program to generate tetrahedral meshes of any 3D
polyhedral domains. TetGen generates exact constrained Delaunay
tetrahedralizations, boundary conforming Delaunay meshes, and Voronoi
partitions. The following pictures respectively illustrate a 3D
polyhedral domain (left), a boundary conforming Delaunay tetrahedral
mesh (middle), and its dual - a Voronoi partition (right).
<center>
<img src="figs/thepart-plc.gif" width="230"> 
<img src="figs/thepart-dt.gif" width="230"> 
<img src="figs/thepart-vd.gif" width="230"> <p>
</center>
TetGen provides various features to generate good quality and adaptive
tetrahedral meshes suitable for numerical methods, such as finite
element or finite volume methods. For more information of TetGen,
please take a look at a list of [features](features.md).


TetGen is written in C++. It can be compiled into either a standalone
program invoked from command-line or a library for linking with other
programs.  All major operating systems, e.g. Unix/Linux, MacOS,
Windows, etc, are supported.<p>

## Download & License
The source code of TetGen is available from the git repository [https://codeberg.org/TetGen/TetGen](https://codeberg.org/TetGen/TetGen). 
It is licensed under [AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0.html).

The following versions are available for download:

- [v1.4.3, 2011](https://codeberg.org/TetGen/TetGen/archive/v1.4.3.tar.gz): [MIT license with noncommercial clause](https://raw.githubusercontent.com/TetGen/TetGen/refs/tags/v1.4.3/LICENSE).
- [v1.5.0, 2013](https://codeberg.org/TetGen/TetGen/archive/v1.5.0.tar.gz): [AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0.html).
- [v1.5.1, 2018](https://codeberg.org/TetGen/TetGen/archive/v1.5.1.tar.gz): [AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0.html), recommended as most stable version.
- [v1.6.0, 2020](https://codeberg.org/TetGen/TetGen/archive/v1.6.0.tar.gz): [AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0.html), most recent version with some rough edges.

## Commercial licensing

TetGen versions up to v1.6.x are distributed under a dual licensing scheme.  As an alternative to the use of TetGen under the AGPLv3 license, consider the option to obtain a commercial license for a fee.  These licenses are offered by the Weierstrass Institute for Applied Analysis and Stochastics (WIAS). As a rule, licenses are provided "as-is", unlimited in time for a one time fee.  Please send corresponding requests to: `tetgen at wias-berlin.de`.  Please do not forget to include some description of your company and the realm of its activities.

Details about the extension of this dual licensing scheme for future versions of TetGen will be announced in due time.


## Documentation & Technical information
- Manuals are available from the git repository  [https://codeberg.org/TetGen/Manuals](https://codeberg.org/TetGen/Manuals).
- A technical paper about TetGen is available at [Hang Si, "TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator". ACM Trans. on Mathematical Software. 41 (2), 2015](http://doi.acm.org/10.1145/2629697)

