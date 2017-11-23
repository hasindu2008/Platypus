# Cache optimised Platypus Variant Caller

Cache optimised version of the Platypus variant caller. The de Bruijn graph construction process during the local re-assembly step of the original Platypus variant callers consumes more than 66% of the computational time. In this version of Platypus, the graph construction algorithm has been changed such that the memory hierarchy of the computer system is effectively used. 

The main Web site for the original Platypus Variant Caller is https://github.com/andyrimmer/Platypus. This repository has been forked from https://github.com/andyrimmer/Platypus. Code for the local re-assembly step is found in src/cython/assembler.pyx.

##Installation and execution

To build Platypus, do the following:

    make

Then to run do

    python bin/Platypus.py --bamFiles=BAM.bam --refFile=REF.fa --output=variants.vcf

Platypus has been tested with Python 2.6 and 2.7, and requires Cython 0.20.2 or later
to build.

####Prerequisites

Platypus requires HTSlib 1.2.1 or greater. HTSlib can be downloaded from the [HTSlib Web site](http://www.htslib.org/download/).

To build and install HTSlib, cd into HTSlib source and type `make install`. This will install HTSlib under `/usr/local/` (see note below). To install HTSlib in any other directory use `make install prefix=/path/to/dir`.

NOTE: HTSlib should be installed in a standard location (e.g. `/usr/local/`). If not installed in a standard location, you will need to set your library paths:

For GNU/Linux:

    export C_INCLUDE_PATH=/path/to/dir/include
    export LIBRARY_PATH=/path/to/dir/lib (only for making)
    export LD_LIBRARY_PATH=/path/to/dir/lib

Note the `/include` and `/lib` sub-directories. e.g. if you installed HTSlib under `/Users/me/htslib` then set

    export C_INCLUDE_PATH=/Users/me/htslib/include
    export LIBRARY_PATH=/Users/me/htslib/lib
    export LD_LIBRARY_PATH=/Users/me/htslib/lib

HTSlib will automatically make the `include` and `lib` directories on install.

For OSX:

    export C_INCLUDE_PATH=/path/to/dir/include
    export LIBRARY_PATH=/path/to/dir/lib (only for making)
    export DYLD_FALLBACK_LIBRARY_PATH=/path/to/dir/lib
