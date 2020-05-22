# Compiling ABINIT on Deac


## Todo

* Prepare for ABINIT 9
* Hybrid parallelism (probably not needed)
* https://forum.abinit.org/viewtopic.php?f=3&t=3823


## Compiling completely from scratch using Intel tools

```
sed -i -e 's/vec-report0/qopt-report=0/g' configure
```

```
./configure --enable-mpi --with-mpi-prefix=$I_MPI_ROOT --with-linalg-flavor=mkl+scalapack --with-linalg-incs=-I${MKLROOT}/include --with-linalg-libs="$MKL_SCALAPACK_SEQUENTIAL"
```


Use only if compiling with Intel MPI?
```
sed -i -e 's/mpicc/mpiicc/g' -e 's/mpicxx/mpiicpc/g' -e 's/mpif90/mpiifort/g' configure
```

