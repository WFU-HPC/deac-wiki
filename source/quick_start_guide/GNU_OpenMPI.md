**Open MPI** is an open source implementation of the MPI-2 standard.
Several academic, research, and commercial entities contribute the the
Open MPI Project.\[1\]

## Available Versions

The recommended version is 1.6, the latest "stable" version, available
by loading the modulefile:

`    module load openmpi/1.6-gnu`

Also available is version 1.5.5, available with the module
openmpi/1.5.5-gnu. The Open MPI project recommends version 1.6 for all
users.

## Using Open MPI to Compile

Once the modulefile is loaded, the MPI compiler commands are available:
mpicc, mpicxx, mpif77, and mpif90. The module also defines environment
variables for these compilers:

`    MPICC = mpicc`
`    MPICXX = mpicxx`
`    MPIF77 = mpif77`
`    MPIF90 = mpif90`

Please see the official documentation for details on programming with
MPI-2 and with Open MPI in particular.\[2\]\[3\]

## Using Open MPI to Run Cluster Jobs

We have compiled Open MPI with Torque support, but SLURM still runs on
it. This means that you do not have to generate a host file and figure
out the distribution of jobs over each node. Open MPI's mpirun command
will examine the job properties given by the "nodes" and
"tasks-per-node" directives and act accordingly.

For a brief summary on usage of the mpirun program, type the following
at the command line:

`    mpirun --help`

Further details are available in the official documentation.\[4\]

## Infiniband

Open MPI has support for [Infiniband](Infiniband "wikilink"). To use
Infiniband, you must do two things:

1.  request Infiniband nodes in your job script: <tt>
      - \#SBATCH --partition=infiniband</tt>
      - `#SBATCH --switches=1`
2.  pass options to mpirun to use the Infiniband network (instead of the
    default Ethernet):

`    mpirun --mca btl ^tcp  ./my_program --my-options=foo --my-flag`

The "^tcp" argument means "NOT tcp", i.e. "NOT ethernet".

## Intel Compilers

To run with OpenMPI + Intel Compilers, the module to use is

`    openmpi/1.6-intel`

The rest of the instructions should be the same.

## References

<references/>

[Category:Software](Category:Software "wikilink")
[Category:Compiling](Category:Compiling "wikilink") [Category:Quick
Start](Category:Quick_Start "wikilink")

1.  [Open MPI Project official web page](http://www.open-mpi.org/)
2.  [Open MPI Official Documentation](http://www.open-mpi.org/doc/)
3.  [Official MPI Documents from the MPI Forum](http://www.mpi-forum.org/docs/docs.html)
