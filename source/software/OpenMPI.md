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
usNIC connectivity, and the FORTRAN and CXX interfaces,

```
./configure --prefix=/deac/opt/rhel7/openmpi/4.0.3-intel-2020 --with-usnic --with-slurm --enable-mpi-fortran --enable-mpi-cxx --enable-mpi-cxx-seek CC=icc CXX=icpc FC=ifort
```

If you wish to provide the best compatability with Spack, you can configure as follows,

```sh
./configure --with-usnic --with-slurm --enable-mpi-fortran --disable-silent-rules --enable-shared --disable-builtin-atomics --enable-static --enable-mpi1-compatibility --disable-memchecker --with-hwloc=/deac/opt/rhel7/hwloc/2.2.0 --disable-mpi-java --without-cuda --enable-wrapper-rpath --disable-wrapper-runpath --enable-mpi-cxx --enable-mpi-cxx-seek --disable-cxx-exceptions --with-wrapper-ldflags="-Wl,-rpath,/deac/opt/rhel7/gcc/10.1.0/lib64 -Wl,-rpath,/deac/opt/rhel7/gcc/10.1.0/lib -Wl,-rpath,/deac/opt/rhel7/intel/oneapi/compiler/2021.1.1/linux/compiler/lib/intel64_lin" --prefix=/deac/opt/rhel7/openmpi/4.1.0-intel-2021 CC=icc CXX=icpc FC=ifort
```

while being mindful of the correct compiler paths. Start the make process using 4 processors,

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
