There are a few locations where you can store your files (data and
programs). The choice of which one to use depends on what you will be
using those files for.

## Home Directory

Your **home directory**, `/home/`<i>`username`</i>, is a general purpose
space. Typically, your source code and compiled programs will be kept
here. If you have very large data files (multiple gigabytes, say), they
should be stored elsewhere as described below. Submitted jobs are not to
be executed, nor data written to/read from, this path.

If you install your programs in `~/bin`, just add `~/bin` to your `PATH`
environment variable. Set it in .bashrc or .cshrc/.tcshrc depending on
your shell.

## Research Group Directory

Each research group has a path created to store that group's shared
research data. These paths are designed to be used as your primary
working directory for job output and file creation. They should also be
used for long-term storage of data that the entire group can use.

Wake Forest University research groups have their paths created on the
cluster's [primary storage
array](Cluster:Hardware_Configuration#Storage "wikilink"). They are
shared via NFS to all cluster nodes, and fall under the following
categories based on group type:

1.  *'/deac/*<researchGrp>'' '''- These paths are created for
    contributing research groups only. These groups can be identified by
    those who submit to their own fairshare account in SLURM. Each
    group's path lies on it's own standalone filesystem with dedicated
    storage. Access to research data is limited only to those who belong
    to the overarching research group.
2.  *'/deac/generalGrp/*<researchGrp>'' '''- These paths are created for
    non-contributing research groups. These groups can be identified by
    those who submit to the generalGrp fairshare account in SLURM. Each
    group's path lies on the same filesystem, sharing the same dedicated
    storage. Access to research data is not shared between
    non-contributing research groups; it is limited at non-contributing
    research group level (unless otherwise specified).
3.  *'/deac/generalGrp/usershare/*<username>'' '''- These paths are
    created for individual users that do not belong to an overarching
    research group. They can also be identified by submitting to the
    generalGrp fairshare account in SLURM. These individual users share
    the dedicated 10TB of storage with other generalGrp users, but do
    not share access to their research data with other users.

WF Baptist Hospital groups have dedicated storage primarily found at
*'/isilon/wfuhpc/*<researchGrp>'' ''', as well as other dedicated paths.
These paths are shared via NFS from WFBH storage that is maintained by
WFBH admins, not the HPC Team. Collaboration with the hospital does
ensure these paths are shared to all cluster nodes and available for use
on the DEAC cluster.

See how to report [Disk Space
Issues](Quick_Start_Guide:Error_Reporting#Disk_Space_Issues "wikilink")
if your filesystem runs out of space.

## `/scratch` Directories (Per Node)

Each compute node has a **`/scratch` directory**, which is a local
SCSI-attached disk. Since it is a device local to the compute node, disk
operations to that device will tend to be much faster than to user home
or research group directories, both of which are accessed over the
network.

/scratch is meant purely for transient data to be used during the
lifetime of a job. The amount of space is not guaranteed because other
jobs may use /scratch, too. Scratch data is automatically removed when
your job completes; you do not need to clean up this data, but it is
appreciated.

If your job performs a lot of disk I/O, it will likely be better for you
to run your job using files stored in /scratch. In your
[SLURM](SLURM "wikilink") job script, you will have to write commands to
copy the files over to the appropriate directory. A useful
\[<https://slurm.schedmd.com/sbatch.html#lbAH>| SLURM Environment
Variable\] is `SLURM_JOBID` -- the i.d. of the job that is executing.
Use this variable to write to and read from the scratch directory:

  - csh/tcsh
version

`   setenv SCRATCHDIR /scratch/$SLURM_JOBID`
`   setenv DATAFILE myNiceInput.dat`
`   `
`   # Copy program and inputs to scratchdir`
`   cp ~/bin/giantProgram $SCRATCHDIR`
`   cp /deac/researchGrp/${DATAFILE} $SCRATCHDIR`
`   `
`   # go into scratchdir and run program`
`   cd $SCRATCHDIR`
`   ${SCRATCHDIR}/giantProgram ${DATAFILE}`
`   `
`   # Clean up after we're done`
`   #    copy outputs back to home`
`   cp ${SCRATCHDIR}/giantOutputs_${SLURM_JOBID}.dat /deac/researchGrp/`
`   `
`   #    delete scratchdir and its contents`
`   /bin/rm -rf ${SCRATCHDIR}`

  - bash
version

`   export SCRATCHDIR=/scratch/$SLURM_JOBID`
`   export DATAFILE=myNiceInput.dat`
`   `
`   # Copy program and inputs to scratchdir`
`   cp ~/bin/giantProgram $SCRATCHDIR`
`   cp /deac/researchGrp/${DATAFILE} $SCRATCHDIR`
`   `
`   # go into scratchdir and run program`
`   cd $SCRATCHDIR`
`   ${SCRATCHDIR}/giantProgram ${DATAFILE}`
`   `
`   # Clean up after we're done`
`   #    copy outputs back to home`
`   cp ${SCRATCHDIR}/giantOutputs_${SLURM_JOBID}.dat /deac/researchGrp/`
`   `
`   #    delete scratchdir and its contents`
`   /bin/rm -rf ${SCRATCHDIR}`

To request nodes with at least a certain size of scratch disk space, use
the "constraint" request:

`   #SBATCH --constraint=scr40gb`
`   ###40GB scratch`

`   #SBATCH --constraint=scr250gb`
`   ###250GB scratch`

## See Also

  - <https://slurm.schedmd.com/sbatch.html#lbAH> -- SLURM Environment
    Variables
  - [Information:Moving Files
    Efficiently](Information:Moving_Files_Efficiently "wikilink") --
    Guide on moving data efficiently

[Category:Quick Start](Category:Quick_Start "wikilink")
