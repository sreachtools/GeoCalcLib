# GeoCalcLib: An interface for David Avis' LRS library

GeoCalcLib is an interface to lrs and redund developed by
Rainer Schaich. For the original repository and website, see
http://worc4021.github.io/GeoCalcLib. This fork serves to
provide detailed installation instructions and possible
improvements to this repository.

## What does GeoCalcLib do?

The geometric calculation library uses David Avis'
[LRS library](http://cgm.cs.mcgill.ca/~avis/C/lrs.html), to
compute the vertex enumeration of a polyhedral set `P = {x:
A*x<=b}`. It also computes the facet enumeration to `P =
conv(V) + cone(R)`.  It has a function to compute the
projection of a polyhedron, as well as reduction functions
to obtain minimal representations of both V and
H-representations of polyhedra.


## Installation

### Requirements

- MATLAB (Tested with R2018b, 2020a)
- Requires `GMP` library and `gcc`, `make`, `m4`.
    > :warning: MATLAB may complain that it found a version
       of `gcc` that is not in its list of supported
       compilers https://www.mathworks.com/support/requirements/supported-compilers.html. Ignoring this warning has not proved to be fatal yet! We were able to get MATLAB R2020a accept gcc-5.5 version as well.
   

### Linux/MacOS

Your standard gcc should have GMP installed. Else, see the
instructions in troubleshooting below.

1. Download a zip file of this repository **OR** clone this
   repository using 
   ```
   git clone https://github.com/sreachtools/GeoCalcLib
   ```
1. Edit `User.make` file to include the path to MATLAB root
   folder. 
   - Note that `<FULL-PATH-TO-YOUR-MATLAB-INSTALLATION>` is the parent
   directory of MATLAB bin folder and does not end with a
   `/`.
   - See
      [https://www.mathworks.com/matlabcentral/answers/66570-what-is-the-default-installation-path-for-matlab-on-architecture-x#answer_78163](https://www.mathworks.com/matlabcentral/answers/66570-what-is-the-default-installation-path-for-matlab-on-architecture-x#answer_78163)
   for hints on how to identify your matlab root folder for your OS.
1. Run in MATLAB command prompt
   ```
   mex -v setup
   ``` 
   to make sure that that MATLAB's `mex` knows where `gcc` is. 
1. Run in Unix command prompt after changing directory to the `GeoCalcLib`
   folder,
   ```
   make
   ``` 
1. Add `/path/to/GeoCalcLib/mexfiles` to MATLAB path. If you want to use this
   across sessions, we recommend adding the following command to your MATLAB
   startup.
   ```
   addpath('/path/to/GeoCalcLib/mexfiles');
   ```

#### Troubleshooting: GMP installation

**Issue**: `make` fails to find `gmp.h`

**Solution**: Install [GMP](https://gmplib.org/) ---  a free
library for arbitrary precision arithmetic, operating on
signed integers, rational numbers, and floating-point
numbers.

**Steps**:  There are two options to resolve this issue.
1) Download via `apt`.
Specifically, do `sudo apt install libgmpXX`, where for
Ubuntu 16.04, it was `libgmp10`.

2) Build GMP from sources. 
    1. Get the tar ball from
       [https://gmplib.org/#DOWNLOAD](https://gmplib.org/#DOWNLOAD)
    1. Follow the installation instructions
       [https://gmplib.org/manual/Installing-GMP.html#Installing-GMP](https://gmplib.org/manual/Installing-GMP.html#Installing-GMP)
       1. Run `./configure` in the folder containing the
          extracted gmp files.
       1. Run `make`
       1. Run `sudo make install` to add the files.
   1. You should now be able to run the mex files from MATLAB.

### Windows

A major issue is the LRS's requirement of GMP. If anyone
figures out how to jump that hoop, please let me know.
