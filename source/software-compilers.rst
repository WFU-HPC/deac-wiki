====================
Compiler Information
====================

------------------------
Intel Parallel Studio XE
------------------------

Introduction
============

The Intel Parallel Studio XE (PSXE) is a software development product developed
by Intel that facilitates native code development on Windows, macOS and Linux in
C++ and Fortran for parallel computing. Parallel programming enables software
programs to take advantage of multi-core processors from Intel and other
processor vendors. The Cluster Edition consists of the following components:

* Build

    * Intel C/C++ Compiler
    * Intel Fortran Compiler
    * Intel Distribution for Python
    * Intel Math Kernel Library (MKL)
    * Intel Data Analytics Acceleration Library (DAAL)
    * Intel Integrated Performance Primitives (IPP)
    * Intel Threading Building Blocks (TBB)
    * Intel Parallel STL (PSTL)

* Analyze

    * Intel Debugger
    * Intel Advisor
    * Intel Inspector
    * Intel VTune Profiler

* Scale

    * Intel MPI Library
    * Intel Trace Analyzer and Collector (ITAC)
    * Intel Cluster Checker

General Usage
-------------

Generally speaking, scientific applications obtain enhanced performance using
the Intel toolset when running on Intel hardware. The DEAC cluster compute nodes
use several models of Intel Xeon processors, making this toolset a valuable tool
for all researchers and software developers who make use of the DEAC cluster.

For most activities, only three components of the Intel PSXE are needed:

* The Intel C and FORTRAN compilers (``icc`` and ``ifort``)
* The Intel MKL (as an alternative for SCALAPACK, FFTW, BLAS, LAPACK, etc.)
* The Intel MPI libraries and compilers (``mpiicc`` and ``mpiifort``)

The Intel MKL offers a variety of high performance library interfaces that can
be used even when using other compilers, such as the GNU C and FORTRAN
compilers. The Intel MPI library and compilers can be used to build applications
that rely on MPI parallelization, which is extremely popular in HPC
environments. However, we suggest using Open MPI over Intel MPI due to the Open
MPI's ability to access the low latency Cisco usNIC hardware that is available
on the compute nodes. In most other areas either MPI library should yield
similar performance under most conditions.


The DEAC cluster has several versions of the PSXE available to you via standard
modules; we will use the PSXE 2020 as our working example in this guide.
Individual components have been separated into standalone modules:

.. code-block:: console

    compilers/intel/2020
    libs/intel/daal/2020
    libs/intel/ipp/2020
    libs/intel/mkl/2020
    libs/intel/pstl/2020
    libs/intel/tbb/2020
    mpi/intel/2020
    utils/intel/advisor/2020
    utils/intel/clck/2020
    utils/intel/debugger/2020
    utils/intel/inspector/2020
    utils/intel/itac/2020
    utils/intel/vtune/2020

Each module will automatically set up your environment to have access to the
relevant software and libraries.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

The **Intel Cluster Studio XE 2012**\[1\] is a suite of compilers,
optimized math libraries (including BLAS, LAPACK, and some FFTW2/3), and
MPI2 implementation. Also included are a debugger, and analysis and
profiling tools.

## How to Use

There are two "flavors" of the compiler suite: one with 32-bit ints
(called "lp64" \[that's an ell\]) and one with 64-bit ints (called
"ilp64"). In most cases, the lp64 flavor is recommended. Your
application may have a special requirement for 64-bit ints, in which
case you would use ilp64. To use them, [load the appropriate
module](Quick_Start_Guide:Environment_Modules "wikilink")
with:

.. code-block:: console

    $ module load modulename

where ``modulename`` is one of these two: ``compilers/intel-2012-lp64`` or ``compilers/intel-2012-ilp64``

This sets many environment variables required for using all the
components of the compiler suite.

Before running the compiled program, the same module environment must be
in effect. When writing a job script, the "module load *modulename*"
line should be included in the script before the program is invoked.

Component Products
==================

The Cluster Studio is a suite of products\[2\]:

* C/C++ compilers (``icc``, ``icpc``)
* Fortran 77/95 compiler (``ifort``)
* Intel Cilk Plus - concurrent and parallel programming language
* Debugger (idb)
* Integrated Performance Primitives (IPP) - a library of
* multicore-ready functions for data analysis and communication
* Math Kernel Library (MKL) 10.3 - includes BLAS, LAPACK, ScaLAPACK1,
* interfaces for FFTW2/3, etc.
* Threading Building Blocks
* Intel MPI Library
* Intel Inspector XE
* Intel VTune Amplifier XE
* Intel Trace Analyzer and Collector

Using the Math Kernel Library (MKL) and MPI
===========================================

MKL
---

One of the advantages of using the Intel suite is that it includes
highly optimized numerical routines. The MKL (version 10.3 is installed)
provides BLAS, LAPACK, ScaLAPACK1, and interfaces to FFTW2/3.
Unfortunately, using the MKL is fairly complex.

To link to the MKL, and possibly other components of the compiler suite,
the link line must be obtained from the [Intel MKL Link Line
Advisor](http://software.intel.com/en-us/articles/intel-mkl-link-line-advisor/)
a web application. You provide the following inputs;

* Intel Product: Intel(R) MKL 10.3
* OS: Linux
* Processor architecture: Intel(R) 64
* Compiler: (select the one you are using)
* Dynamic or static linking: of the three choices provided, "Single Dynamic
  Library" results in the least complex link line -- it leaves some decisions
  about sequential versus multi-threaded execution to run time. However, this
  precludes use of MPI. If your application needs MPI, you must select "Dynamic
  Library".
* Interface layer: generally, LP64 (32-bit integers) should be used; your
  application may require ILP64 (64-bit ints)
* OpenMP Library: Intel(R) (libiomp5) -- there is no choice
* Cluster library: select one or more; MPI programs will require BLACS (Basic
  Linear Algebra Communication Subprograms)
* MPI library: Intel(R) MPI -- instead of a pre-installed MPICH
* Fortran95 interfaces: select BLAS and/or LAPACK if applicable
* Link with MKL libraries explicitly: check ON

The output at the bottom of the page gives you a link line (all the
``-Ldir`` and ``-lbar``), and a compile flag specifying the directory where
include files reside. Copy them and paste into the appropriate portions
of your Makefile.

Intel MPI
---------

Do not use Intel's MPI implementation. We have found that it does not work
correctly. Use Open MPI 1.6 -- load the "openmpi/1.6-intel" module. See [Quick
Start Guide:GNU OpenMPI](Quick_Start_Guide:GNU_OpenMPI "wikilink").

Running Programs compiled with Intel
====================================

Programs compiled with the Intel compilers need certain environment
variables set in order to run. These specify, amongst other things, the
location of dynamic libraries. Before running a program, run the same
"module load" command that was used to select the Intel compiler. In job
scripts, the "module load" command should come before the program
invocation.

Integrated Development Environment
==================================

The Intel Cluster Studio XE may be used with
[Eclipse](http://www.eclipse.org), an open source integrated development
environment. Eclipse is a [Java](http://java.oracle.com/) program. To
use the Intel compiler suite and toolchain within Eclipse, use Eclipse's
[C/C++ Development Tooling (CDT)](http://www.eclipse.org/cdt/). We do
not support Eclipse: it may be installed in your own directory.

Typical Optimization Options
============================

Here are some typical options used to control the optimization used when
producing compiled code:

* ``-O3``: optimize for maximum speed and enable more aggressive optimizations
  that may not improve performance on some programs
* ``-xSSE4.1``: May generate Intel(R) SSE4.1 instructions for Intel processors.
  Optimizes for the Intel NetBurst(R) microarchitecture. All cluster nodes,
  except for those in clan06, support SSE4.1. Nodes which support SSE4.2 will
  also support SSE4.1 (i.e. SSE is backwards-compatible).
* ``-no-prec-div``: do *not* improve precision of floating-point divides
* ``-mieee-fp``: improve floating-point precision (impacts speed)
* ``-openmp``: links to OpenMP\[3\] library. N.B. this is *not* MPI or MPI-2.

For each compiler, you can see a long listing of available options and flags by
doing:

.. code-block:: console

    $ ifort -help | less

(hit "Space" to advance, "B" to scroll back up, and "Q" to quit the
pager).

**N.B.** The option ``-fast`` produces code for static linking only. This
will not work for MPI programs. See the compiler help for more details.

## Further Information

* [Intel Learning Lab Portal](http://software.intel.com/en-us/articles/intel-learning-lab/)
    
    * resources for learning how to use Intel software products

* [Intel Cluster Studio documentation](http://software.intel.com/en-us/articles/intel-cluster-toolkit-documentation/)
* [Resources for learning more about Intel Cluster Studio](http://software.intel.com/en-us/articles/intel-cluster-studio-xe/#resources) (includes links to PDF documents for each of the compiler components)

References
==========

1.  [Intel Cluster Studio XE](http://software.intel.com/en-us/articles/intel-cluster-studio-xe/) (Retrieved 2012-03-28.)
2.  [OpenMP article at Wikipedia](http://en.wikipedia.org/wiki/OpenMP)

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

-------------------------------------------------------
Portland Group, Inc. (PGI) Cluster Development Kit 12.1
-------------------------------------------------------

To use the PGI compiler suite, load one of these
[modules](Quick_Start_Guide:Environment_Modules "wikilink") depending on
your MPI
requirements:

.. code-block:: console

    $ module load modulename

where ``modulename`` is one of: ``compilers/pgi-12.1``, ``compilers/pgi-12.1-mpi``, ``compilers/pgi-12.1-mpi2``, ``compilers/pgi-12.1-mvapich``.

Commands
========

These are some of the more commonly used commands in the PGI suite --
most have a "-help" option that prints out usage information:

* pgcc - C compiler
* pgc++ - C++ compiler
* pgfortran - Fortran compiler
* pgdbg - debugger (will also debug MPI programs)

Further Information
===================

* [PGI Documentation](http://www.pgroup.com/resources/docs.htm)

References
==========

1.  [PGI Cluster Development Kit](http://www.pgroup.com/products/pgicdk.htm) (Retrieved 2012-03-29.)
