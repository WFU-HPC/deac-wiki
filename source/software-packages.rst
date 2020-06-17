=================
Software Packages
=================

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

------
ABINIT
------

Website: https://www.abinit.org
Keywords: Electronic Structure, Ab Initio, Density Functional Theory

Introduction
============

ABINIT is a package whose main program allows one to find the total energy,
charge density and electronic structure of systems made of electrons and nuclei
(molecules and periodic solids) within Density Functional Theory (DFT), using
pseudopotentials and a planewave basis.

Method
======

Compiling completely from scratch using Intel tools:

.. code-block:: none

    $ sed -i -e 's/vec-report0/qopt-report=0/g' configure

    $ ./configure --enable-mpi --with-mpi-prefix=$I_MPI_ROOT \
                  --with-linalg-flavor=mkl+scalapack \
                  --with-linalg-incs=-I${MKLROOT}/include \
                  --with-linalg-libs="$MKL_SCALAPACK_SEQUENTIAL"

To-Do
-----

* Prepare for ABINIT 9
* Hybrid parallelism (probably not needed)
* https://forum.abinit.org/viewtopic.php?f=3&t=3823

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------------------------
Affymetrix Power Tools (APT)
----------------------------

Website: http://www.affymetrix.com/partners_programs/programs/developer/tools/powertools.affx

Introduction
============

The Affymetrix Power Tools (APT) are a set of cross-platform command line
programs that implement algorithms for analyzing and working with Affymetrix
GeneChip arrays. APT is an open-source project licensed under the GNU General
Public License (GPL).

As of 2013-07-01, installed versions include:

    * 1.10.2
    * 1.15.1

Usage
=====

Load the module for the appropriate version:

.. code-block:: none

    module load apt/1.10.2
    module load apt/1.15.1

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

--------
AutoDock
--------

Website: http://autodock.scripps.edu/

Introduction
============

AutoDock is a suite of automated docking tools. It is designed to predict how
small molecules, such as substrates or drug candidates, bind to a receptor of
known 3D structure. Current distributions of AutoDock consist of two generations
of software: AutoDock 4 and AutoDock Vina.

Current versions installed on the cluster:

    * 4.2.5.1

## Compiling

Download the source from the website, and execute the following:

.. code-block:: none

    $ module purge
    $ module load compilers/intel-2012-lp64
    $ cd ~/src
    $ mv ../autodocksuite-x.y.z.a-src.tar.gz .
    $ tar zxf autodocksuite-x.y.z.a-src.tar.gz
    $ cd src/autodock
    $ mkdir x86_64Linux2
    $ cd x86_64Linux2
    $ export CXXFLAGS="-O3 -xSSE4.1 -ipo"
    $ ../configure --prefix=$HOME
    $ make >& Make.out
    $ make check >& Make.check.out
    $ make install

Usage
=====

.. code-block:: none

    module load autodock/4.2.5.1-intel-2012

The executable is ``autodock4``.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################
