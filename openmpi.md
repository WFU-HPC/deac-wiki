# Open MPI


## Introduction

The Open MPI Project is an open source Message Passing Interface implementation
that is developed and maintained by a consortium of academic, research, and
industry partners. Open MPI is therefore able to combine the expertise,
technologies, and resources from all across the High Performance Computing
community in order to build the best MPI library available. Open MPI offers
advantages for system and software vendors, application developers and computer
science researchers.


## Installation

The build process for Open MPI is can be quite time consuming, but the configure
script does a good job of auto-detecting most options. The following process is
for using the Intel 2020 compilers.


### Prerequisites

* Intel compilers (`module load compilers/intel/2020`)


### Compilation

Configure the software to automatically link with SLURM, enable the low-latency
usNIC connectivity, and the FORTRAN and CXX interfaces.

```
./configure --prefix=/deac/opt/rhel7/openmpi/4.0.3-intel-2020 --with-usnic --with-slurm --enable-mpi-fortran --enable-mpi-cxx --enable-mpi-cxx-seek CC=icc CXX=icpc FC=ifort
```

Start the make process using 4 processors,

```
make -j 4 all
```

noting that this can be very time consuming (30+ min.). After a successful
build, run the built-in tests,

```
make check
```

If the tests pass, install your new software,

```
make install
```

Even the final installation command can take longer than 5 minutes so do not
despair.
