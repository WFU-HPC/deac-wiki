# Spack Stack

## Initial Toochain

```sh
spack install gcc@8.4.0 && spack install gcc@9.3.0 && spack install gcc@7.4.0
```

```sh
spack install gcc@9.3.0 target=x86_64
spack install openmpi@4.0.3 %gcc

spack install openmpi@4.0.3
spack install libxc
spack install fftw
spack install fftw -mpi
spack install hdf5
spack install elpa

spack spec -I quantum-espresso %intel hdf5=parallel +epw +scalapack
spack spec -I abinit %intel +hdf5 +scalapack
spack spec -I abinit %intel +hdf5 +scalapack

```

```sh
export TMPDIR=/scratch/$SLURM_JOBID
spack config --scope=user/linux edit config
spack config --scope=user/linux edit compilers
spack config --scope=user/linux edit packages
spack config --scope=user/linux edit modules
spack gc
spack clean -a
spack module tcl refresh --delete-tree -y
```



## Todd

* default opimizations on packages?
* views relevant for stack? Seem more for activating and using environments within spack
* spack job submission `srun -N 2 -n 6 spack install -j 8 trilinos`
* modulefile naming (prefixes)

```yaml
modules:
  tcl:
    all:
      suffixes:
        '^intel-mpi': impi
        '^openmpi': openmpi
        '^mpich': mpich
      prefixes:
        'libs': [fftw, libxc, elpa, blas]
        'mpi': [intel-mpi, openmpi, mpich, mvapich2]
        'applications': [quantum-espresso, cp2k, abinit, namd]
        'compilers': [gcc, intel, clang]
```


## Team

* audit build recipes
* use base system utils, or compile a good standard toolchain, avoid some compiling
* module autoloading desirable? maybe this could alleviate some of the module naming strictness
* spack `dev-build` for working with your own software
* spack works with mathematica, matlab too
* FOSS vs. Intel, numerical accuracy
* catalog idea, but with databases obtained from spack or via Lmod spider JSON
* 'bundle' and 'advanced' modulefiles
