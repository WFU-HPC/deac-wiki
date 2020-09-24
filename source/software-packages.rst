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

    sed -i -e 's/vec-report0/qopt-report=0/g' configure

    ./configure --enable-mpi --with-mpi-prefix=$I_MPI_ROOT \
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

    module purge
    module load compilers/intel-2012-lp64
    cd ~/src
    mv ../autodocksuite-x.y.z.a-src.tar.gz .
    tar zxf autodocksuite-x.y.z.a-src.tar.gz
    cd src/autodock
    mkdir x86_64Linux2
    cd x86_64Linux2
    export CXXFLAGS="-O3 -xSSE4.1 -ipo"
    ../configure --prefix=$HOME
    make >& Make.out
    make check >& Make.check.out
    make install

Usage
=====

.. code-block:: none

    module load autodock/4.2.5.1-intel-2012

The executable is ``autodock4``.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

--------
RAXML-NG
--------

From the GitHub repo:

.. code-block:: none

    module load rhel7/gcc/10.1.0 rhel7/openmpi/4.0.2-gcc-4.8 rhel7/cmake/3.14
    git clone --recursive https://github.com/amkozlov/raxml-ng
    cd raxml-ng && mkdir -p build-mpi && mkdir -p build-pthreads
    cd build-mpi
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/deac/opt/rhel7/raxml-ng/0.9.0 -DUSE_MPI=ON .. && make && make install
    cd ../build-pthreads
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/deac/opt/rhel7/raxml-ng/0.9.0 .. && make && make install

For specific GitHub releases:

.. code-block:: none

    module load rhel7/gcc/10.1.0 rhel7/openmpi/4.0.2-gcc-4.8 rhel7/cmake/3.14
    wget https://github.com/amkozlov/raxml-ng/releases/download/1.0.0/raxml-ng_v1.0.0_source.zip
    mkdir -p raxml-ng && cd raxml-ng && unzip ../raxml-ng_v1.0.0_source.zip
    mkdir -p build-mpi && mkdir -p build-pthreads
    cd build-mpi
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/deac/opt/rhel7/raxml-ng/1.0.0 -DUSE_MPI=ON .. && make && make install
    cd ../build-pthreads
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/deac/opt/rhel7/raxml-ng/1.0.0 .. && make && make install

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

-------
IQ-TREE
-------

.. code-block:: none

    module load rhel7/cmake/3.14 rhel7/gcc/10.1.0 rhel7/openmpi/4.0.2-gcc-4.8 rhel7/eigen/3.3.7

    git clone https://github.com/Cibiv/IQ-TREE.git # or specific release 
    cd IQ-TREE
    mkdir -p build && cd build
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/deac/opt/rhel7/iq-tree/2.0.7 -DIQTREE_FLAGS=omp-mpi ..

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

------
Siesta
------

.. code-block:: console

    module load rhel7/gcc/6.2.0 \
                rhel7/gcc/6.2.0-libs \
                rhel7/compilers/intel-2018-lp64 \
                rhel7/openmpi/4.0.2-intel-2018
    
    PREFIX="/target/siesta/dir"
    SIESTA_ROOT="/siesta/source/dir"
    MKLLIBS=""${MKLROOT}/lib/intel64""
    
    mkdir -p ${SIESTA_ROOT}/Obj ${SIESTA_ROOT}/Obj_trans
    
    ## Siesta
    cd ${SIESTA_ROOT}/Obj
    ../Src/obj_setup.sh
    ../Src/configure --enable-mpi \
                     --with-blas="${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-lapack="${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-blacs="${MKLLIBS}/libmkl_scalapack_lp64.so ${MKLLIBS}/libmkl_blacs_openmpi_lp64.so ${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-scalapack="${MKLLIBS}/libmkl_scalapack_lp64.so ${MKLLIBS}/libmkl_blacs_openmpi_lp64.so" \
                     MPIFC="/deac/opt/rhel7/openmpi/4.0.2-intel-2018/bin/mpif90"
    make
    install siesta $PREFIX
    
    ## Transiesta
    cd ${SIESTA_ROOT}/Obj_trans
    ../Src/obj_setup.sh
    ../Src/configure --enable-mpi \
                     --with-blas="${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-lapack="${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-blacs="${MKLLIBS}/libmkl_scalapack_lp64.so ${MKLLIBS}/libmkl_blacs_openmpi_lp64.so ${MKLLIBS}/libmkl_intel_lp64.so ${MKLLIBS}/libmkl_sequential.so ${MKLLIBS}/libmkl_core.so /lib64/libpthread.so /lib64/libm.so /lib64/libdl.so" \
                     --with-scalapack="${MKLLIBS}/libmkl_scalapack_lp64.so ${MKLLIBS}/libmkl_blacs_openmpi_lp64.so" \
                     MPIFC="/deac/opt/rhel7/openmpi/4.0.2-intel-2018/bin/mpif90"
    make transiesta
    install transiesta $PREFIX
    
    ## Utils (Optional)
    cd ${SIESTA_ROOT}/Util
    ./build_all.sh
    for FILE in $(find . -type f -perm /u=x,g=x,o=x -exec ls {} \;); do cp $FILE $PREFIX; done
    cp TBTrans/MPI/int_explorer     $PREFIX
    cp TBTrans/tbtrans              $PREFIX
    cp TBTrans_rep/MPI/int_explorer ${PREFIX}/int_explorer_rep
    cp TBTrans_rep/tbtrans          ${PREFIX}/tbtrans_rep

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

------
NWChem
------

.. code-block:: console

    module load rhel7/python/3.8.5 \
           rhel7/gcc/7.5.0 \
           rhel7/compilers/intel-2018-lp64 \
           rhel7/openmpi/4.0.2-intel-2018 \
           rhel7/elpa/2020.05.001-intel

    export NWCHEM_TOP="$RESEARCHPATH/src/nwchem-7.0.0"
    export NWCHEM_TARGET=LINUX64
    export NWCHEM_MODULES="all python"
    export USE_MPI=y
    export USE_MPIF=y
    export USE_MPIF4=y
    export USE_SCALAPACK=y
    export BLAS_SIZE=8
    export SCALAPACK_SIZE=8  
    export BLASOPT="-L$MKLROOT/lib/intel64 -lmkl_intel_ilp64 -lmkl_sequential -lmkl_core -lpthread -lm -ldl"
    export LAPACK_LIB=$BLASOPT
    export SCALAPACK="-L$MKLROOT/lib/intel64 -lmkl_scalapack_ilp64 -lmkl_intel_ilp64 -lmkl_sequential -lmkl_core -lmkl_blacs_openmpi_ilp64 -lpthread -lm -ldl"
    export ELPAROOT="/deac/opt/rhel7/spack-temp/intel-18.0.1/elpa/2020.05.001-rknichg"
    export ELPA="-I$ELPAROOT/include -L$ELPAROOT/lib -lelpa"

    ## The following two options help if only shared storage is available. Since
    ## our users can run on the local /scratch directory of each node, these are
    ## not necessary.
    # export USE_NOFSCHECK=TRUE
    # export USE_NOIO=TRUE

    ## Build, takes a very long time (several hours)
    cd $NWCHEM_TOP/src && make nwchem_config && make
    
    ## Site installation, just copying several things
    export INSTALL_DIR="/deac/opt/rhel7/NWChem/7.0.0/"
    mkdir $INSTALL_DIR
    mkdir $INSTALL_DIR/bin
    mkdir $INSTALL_DIR/data
    cp    $NWCHEM_TOP/bin/${NWCHEM_TARGET}/nwchem   $INSTALL_DIR/bin
    cp -r $NWCHEM_TOP/src/basis/libraries           $INSTALL_DIR/data
    cp -r $NWCHEM_TOP/src/data                      $INSTALL_DIR
    cp -r $NWCHEM_TOP/src/nwpw/libraryps            $INSTALL_DIR/data
    chmod 755 $INSTALL_DIR/bin/nwchem
