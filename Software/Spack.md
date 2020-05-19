# Using Spack for software management on DEAC


## Introduction

Spack is a package manager for supercomputers, Linux, and macOS. It makes
installing scientific software easy. Spack isn't tied to a particular language;
you can build a software stack in Python or R, link to libraries written in C,
C++, or Fortran, and easily swap compilers or target specific
microarchitectures.


## Motivation

Researchers across all disciplines will often develop software to tackle their specific research problems. Many of these packages will be re-used and modified by other researchers, which leads to significant growth in both research scope and quality. These applications increasingly leverage the substantial power of modern HPC systems; in fact, many of them are developed with this in mind. Thus, researchers have significant interest in their software being available and functional on many different platforms.

Obviously, this software can be quite complex, with many dependencies and difficult install procedures.























## To-Do

* default opimizations on packages?
* views relevant for stack? Seem more for activating and using environments within spack
* spack job submission `srun -N 2 -n 6 spack install -j 8 trilinos`
* audit build recipes
* module autoloading desirable? maybe this could alleviate some of the module naming strictness
* spack `dev-build` for working with your own software
* spack works with mathematica, matlab too
* FOSS vs. Intel, numerical accuracy
* catalog idea, but with databases obtained from spack or via Lmod spider JSON
* consider just adding spack to path, rather than sourcing

* Compile a good standard toolchain

* Lmod
* Autoload modulefiles?
* Special modulefiles (bundles/toochain)?

* If extension modules blacklisted, no way for loading/autoloading?
* config files in custom directory or system-wide?
* Automation: `packages.yaml` that defines everything we need
* Automation: [Spack python scripting](https://spack-tutorial.readthedocs.io/en/latest/tutorial_spack_scripting.html)
* Automation: Spack stacks via environments (python, R, dft, cuda, etc.)


```sh
spack install gcc@8.4.0 && spack install gcc@9.3.0 && spack install gcc@7.4.0
```

```sh
spack install python
spack install py-pybind11
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
