========================
Intel Parallel Studio XE
========================

Advanced Usage: Sourcing Directly from Installation
---------------------------------------------------

The PSXE is installed cluster-wide, and is divided into a variety of
subdirectories that contain the various components and necessary scripts that
load the appropriate environment variables; these are broken down as follows.
There are two main scripts that load the majority of the PSXE components. First,

.. code-block:: console
    
    source $PSXE/compilers_and_libraries_2020.0.166/linux/bin/compilervars.sh intel64

which will load the compilers (C, FORTRAN, MPI), libraries (MPI, MKL, TBB, IPP,
DAAL, PSTL), and the Intel Debugger; and

.. code-block:: console

    source $PSXE/parallel_studio_xe_2020/bin/psxevars.sh

which will load everything listed at the beginning of this document. ``$PSXE`` is
assumed to be the path to the PSXE root installation directory. Only load one
file in given session; for compiling software and running with MPI, the latter
will suffice. These scripts actually load individual scripts for each component.
These can be manually loaded in order to fine-tune your shell environment as
follows,

.. code-block:: console

    # From compilervars.sh
    . $PSXE/compilers_and_libraries_2020/linux/bin/compilervars_arch.sh intel64 linux # Compilers only
    . $PSXE/compilers_and_libraries_2020/linux/mpi/intel64/bin/mpivars.sh             # MPI compilers and libs
    . $PSXE/compilers_and_libraries_2020/linux/mkl/bin/mklvars.sh intel64             # MKL
    . $PSXE/compilers_and_libraries_2020/linux/tbb/bin/tbbvars.sh intel64 linux       # TBB Library
    . $PSXE/compilers_and_libraries_2020/linux/pstl/bin/pstlvars.sh intel64           # PSTL
    . $PSXE/compilers_and_libraries_2020/linux/ipp/bin/ippvars.sh intel64 linux       # IPP Library
    . $PSXE/compilers_and_libraries_2020/linux/daal/bin/daalvars.sh intel64           # DAAL
    . $PSXE/debugger_2020/bin/debuggervars.sh intel64                                 # Debugger
    
    # Extra stuff from psxevars.sh
    . $PSXE/parallel_studio_xe_2020/clck_2019/bin/clckvars.sh                         # Cluster Checker
    . $PSXE/parallel_studio_xe_2020/itac_2020/bin/itacvars.sh                         # ITAC
    . $PSXE/parallel_studio_xe_2020/inspector_2020/inspxe-vars.sh quiet               # Inspector
    . $PSXE/parallel_studio_xe_2020/vtune_profiler_2020/vtune-vars.sh quiet           # VTune
    . $PSXE/parallel_studio_xe_2020/advisor_2020/advixe-vars.sh quiet                 # Advisor
    . $PSXE/intelpython3/bin/activate                                                 # Intel Python

Advanced Usage: Creating Modulefiles
------------------------------------

Modulefiles can be created directly from the above scripts using the
``createmodule.sh`` tool that comes bundled with the Environment Module package.
Run this tool on each of the above scripts (including positional arguments, if
any). The resulting outputs can be formatted to taste; see the DEAC Modulefiles
repository for examples.
