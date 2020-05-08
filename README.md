# GeoCalcLib: An interface for David Avis' LRS library

This file is part of the geometric calculation library.

The geometric calculation library uses David Avis' [LRS library][lrs], to
compute the vertex enumeration of a polyhedral set `P = {x: A*x<=b}`. It also
computes the facet enumeration to `P = conv(V) + cone(R)`.  It has a function to
compute the projection of a polyhedron, as well as reduction functions to obtain
minimal representations of both V and H-representations of polyhedra.

## Installation

The geometric calculation library offers an interface to Matlab for all its
functionality. It requires the GMP library.

### Linux

1. Install [GMP](https://gmplib.org/) ---  a free library for arbitrary
   precision arithmetic, operating on signed integers, rational numbers, and
   floating-point numbers.
    1. Get the tar ball from
       [https://gmplib.org/#DOWNLOAD](https://gmplib.org/#DOWNLOAD)
    1. Follow the installation instructions
       [https://gmplib.org/manual/Installing-GMP.html#Installing-GMP](https://gmplib.org/manual/Installing-GMP.html#Installing-GMP)
1. Download the zip file from
   [https://github.com/worc4021/GeoCalcLib/archive/master.zip](https://github.com/worc4021/GeoCalcLib/archive/master.zip).
1. Extract the contents of this zip file to a desired location, whose full path
   is referred to here as `/path/to/GeoCalcLib`
1. Open a terminal and change directory to GeoCalcLib by `$cd
   /path/to/GeoCalcLib`. We will refer to this location as the GeoCalcLib root
   folder.
1. Create a folder `mexfiles` in GeoCalcLib root folder. 
1. Create a file named `User.make` in GeoCalcLib root folder using your favorite
   editor with the following contents, and save it. See
   [https://www.mathworks.com/matlabcentral/answers/66570-what-is-the-default-installation-path-for-matlab-on-architecture-x#answer_78163](https://www.mathworks.com/matlabcentral/answers/66570-what-is-the-default-installation-path-for-matlab-on-architecture-x#answer_78163)
   for hints on how to identify your matlab root folder for your OS.
    ```
    # Specify the absolute path to the root folder of your Matlab installation
    where <FULL-PATH-TO-YOUR-MATLAB-INSTALLATION>/bin/mex exists
    MATLABROOT = <FULL-PATH-TO-YOUR-MATLAB-INSTALLATION>
    
    # Path to which everything should be installed
    INSTALLDIR = ../mexfiles/
    ```
1. In the command prompt in GeoCalcLib root folder, execute `$ make`.
1. Add `/path/to/GeoCalcLib/mexfiles` to MATLAB path. If you want to use this
   across sessions, we recommend adding the following command to your MATLAB
   startup.
   ```
   addpath('/path/to/GeoCalcLib/mexfiles');
   ```
1. You should now be able to run the mex files from Matlab.

### Windows

[Click here for the full description][home]

[lrs]: http://cgm.cs.mcgill.ca/~avis/C/lrs.html
[home]: http://worc4021.github.io/GeoCalcLib
