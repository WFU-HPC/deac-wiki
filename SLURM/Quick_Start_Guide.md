## What is SLURM?

The SLURM Workload Manager is *an open source, fault-tolerant and highly
scalable cluster management and job scheduling system*\[1\] used on the
DEAC cluster. Formerly known as Simple Linux Utility for Resource
Management (aka **SLURM**)\[2\], it provides three key functions:

1.  Allocates exclusive and/or non-exclusive access to resources
    (compute nodes) to users for X period of time
2.  Provides a framework for starting, executing, and monitoring work on
    allocated nodes
3.  Arbitrates contention for resources by managing a queue of pending
    jobs

## Example Usage

### Training Videos

  - SLURM Job-Submission Part 1 - [Batch Scripts and
    Components](https://youtu.be/ChcsBE6tJr8?list=PL-g8n27Db1XfPrRvZMBSxK55_lIy39sqZ)
  - SLURM Job-Submission Part 2 -
    [Commands](https://youtu.be/yjDwCnLTVPk?list=PL-g8n27Db1XfPrRvZMBSxK55_lIy39sqZ)
  - SLURM Job-Submission Part 3 - [Resource
    Availability](https://youtu.be/awspKUrvRIg?list=PL-g8n27Db1XfPrRvZMBSxK55_lIy39sqZ)

### Job Submission

This is a trivial example of using a SLURM script to submit a job
consisting of a single program (called `hello_world`). Further details
are in the *SLURM Sbatch Guide* online,\[3\] or found on multiple other
college websites.\[4\] The program prints "hello, world\!" to stdout,
and then sleeps for 30 seconds before terminating. We run it
interactively here:

`   `**`[username@headnode]>`**` pwd`
`   ~/Code/Sandbox/trunk/slurm/NiceCode/`
`   `**`[username@headnode]>`**` ./hello_world`
`   hello, world!`

Here's the job/batch script **`myjob.slurm`**. The lines starting with
`#SBATCH` specify SLURM directives. They are basically glorified
comments as far as the bash script would be concerned, but sbatch
requires them for job submission. Most of them can be specified as
options to the **sbatch** command, which overrides directives within the
script. It's important to set your email address with "\#SBATCH
--mail-user=username@wfu.edu" so that you receive notifications about
your job.

    #!/bin/bash -l
    #SBATCH --partition=medium
    #SBATCH --job-name=hello01
    #SBATCH --mail-type=BEGIN,END,FAIL
    #SBATCH --mail-user=username@wfu.edu
    #SBATCH --account=researcherGrp
    #SBATCH --nodes=2
    #SBATCH --tasks-per-node=8
    #SBATCH --mem=4gb
    #SBATCH --time=0-00:30:00

    $HOME/Code/Sandbox/trunk/slurm/NiceCode/hello_world

This sbatch script sets some SLURM-specific variables, and then calls
the actual program **hello_world**. The job is submitted with `sbatch`:

`   `**`[username@headnode]>`**` sbatch myjob.slurm`
`   Submitted batch job 1234`

### Test Submission

To see if you job will submit successfully, you can use the
**--test-only** flag with sbatch. It will show the approximate start
time, resources used, and node name to be assigned to your
job:

`   `**`[username@headnode]$`**` sbatch --test-only ./myjob.slurm `
`   sbatch: Job 1234 to start at 2016-04-29T15:17:22 using 16 processors on bc04bl[06,08]`

### Job Status

You can check the status of a job with
`sacct`:

`   `**`[username@headnode]>`**` sacct --jobs 1234`
`   JobID    JobName  Partition    Account  AllocCPUS      State ExitCode `
`   ------------ ---------- ---------- ---------- ---------- ---------- -------- `
`   1234         hello_wor_+      medium   researchgrp          1  COMPLETED      0:0 `
`   1234.batch        batch                researchgrp          1  COMPLETED      0:0`

Check the [SLURM commands](SLURM:Commands#sacct "wikilink") page for
more information on output formatting\!

### Email Messages

You should receive an email message when the job
    begins:

    Job <hello_world> was executed on node(s) <compute_node1>, in partition <partition>, as user <username> from group <researchgrp>.
    The initial working directory of this job was /home/username/Code/Sandbox/trunk/slurm/NiceCode/.

    Job has started execution.

    Job Times:
    =======
        Submitted:  2015-09-04 09:16:12
        Started:    2015-09-04 09:16:12


    Summary email to be sent upon job completion.

And then another when the job
    completes:

    Job <hello_world> was executed on node(s) <compute_node1>, in partition <partition>, as user <username> from group <researchgrp>.
    The initial working directory of this job was /home/username/Code/Sandbox/trunk/slurm/NiceCode/.

    Job successfully completed.

    Job Times:
    =======
        Submitted:  2015-09-04 09:16:12
        Started:    2015-09-04 09:16:12
        Ended:      2015-09-04 09:16:25
        Elapsed:    00:00:13

    Job Resource Usage Summary:
    ======================

        JOB ID:   1234
        # CPUS:   8
        # NODES:  2
        MEM/task: n/a
        JOB Name: hello_world

        JOB ID:   6352.batch
        # CPUS:   8
        # NODES:  2
        MEM/task: 19540K
        JOB Name: batch


    Requested Resources and Totals:
    =======================
        Requested time limit:  0-00:30:00
        Requested memory:      4G (per Node)
        Total CPU time :       00:00:13
        Total Allocated CPUs:  8
        Total Allocated Nodes: 2

### Output Files

When the job completes, by default there is one output file created in
the working path when the job was submitted: **slurm-<jobid>.out**. This
file will contain data written to *stdout* (printed output messages) and
*stderr* (generated error messages) information. To change this default
action and create separate files, use the following directives:

Create a starndard output file with whichever name you desire (best
practice - include the job name), and containing job id:

`  #SBATCH --output="hello_world-%j.o"`

Create a standard error file with whichever name you desire, and
containing job id:

`  #SBATCH --error="hello_world-%j.e"`

These files are also created by default in the working path when the job
was submitted. To change the path where the file is created, add the
following directive to your batch script.

`  #SBATCH --workdir="`<PATH>`"`

The job output file(s) will then be created in that specified workdir
path.

## Job Submission Details

A job script is a normal script. It can be a shell script (bash, tcsh,
sh, csh, zsh) or even any other scripting language (Perl, Python, etc).
SLURM will set environment variables before executing the script, and
the job script has access to these environment variables. If your script
is not a shell script, then you would have to use the script language
features to get access to the environment variables.

A job script may consist of SBATCH directives, comments, and executable
statements. SBATCH directives -- lines beginning with "**\#SBATCH**" --
specify job attributes as well as (sbatch) command line options. Lines
where the first non-whitespace character is "`#`" are comments (other
than the "`#SBATCH`" lines).

When a job script is submitted with sbatch, it parses the script for
\#SBATCH directives. These directives correspond to sbatch command line
options; any directive given via command line during submission will
override matching directives within the job script.

### Convert Torque Scripts to SLURM

See [SLURM:Torque Conversion
Script](SLURM:Torque_Conversion_Script "wikilink") page for how to
convert your legacy Torque scripts.

### SLURM to Torque Equivalent Commands

See the "[SLURM:Torque Command
Equivalents](SLURM:Torque_Command_Equivalents "wikilink")" page to
quickly lookup SLURM equivalents to your legacy Torque commands.

### Sample SLURM Job Script Templates

See "[SLURM:Job Script
Templates](SLURM:Job_Script_Templates "wikilink")" for several templates
for typical usage.

### sbatch

There are many sbatch options, all of which may be put into the SLURM
batch script with "\#SBATCH" directives. This helps you avoid typing
long sbatch commands. See the sbatch man page for complete details. Look
at the for the [sbatch](https://slurm.schedmd.com/sbatch.html) online
documentation, or on command line by running **sbatch -h**. You can run
sbatch with the **--test-only** parameter to test syntax and logic of
your directives and determine if submission would be successful. Another
helpful resource is the official SLURM cheatsheet\[5\]. NOTE that
**srun** usage is not normally used on the cluster.

### Requesting Resources

Within SLURM, CPU and Memory are used as consumable resources. This
means that when these resources are requested, they are the primary
deciding factor in node assignment. CPU specifies the number of cores,
and memory specifies the amount of RAM required. Jobs should also
specify the number of nodes and time required. All resource requests
should be explicitly listed within the job script using the \#SBATCH
directive. More details on consumable resources are in SLURM
documentation
online.\[6\]

`   # Example of requesting 16 total CPUS across 2 nodes, with 32 GB of memory, to run for 24 hours`
`   #SBATCH --nodes=2`
`   #SBATCH --tasks-per-node=8`
`   #SBATCH --mem=32gb`
`   #SBATCH --time=24:00:00`

Every node sets aside 1 GB of RAM for system use, so the amount
available for user jobs is less than the total installed RAM. This means
that, if your job requires less than 96 GB of RAM, it is better to
request \<= 95 GB. This is because there are nodes with 96 GB of RAM
installed, and requesting exactly 96 GB means the job will not run on
these otherwise available nodes.

Also, there is no consideration for CPU Time within SLURM, all time
estimates should be based on actual run time (walltime) only.

### Partitions

Partitions are used within SLURM to provide additional weight for job
types allocated on the DEAC cluster. To specify a partition, use the
following directive:

`   #SBATCH --partition=`<NAME>

A partition must be specified to run jobs on the cluster, the default
partition is not designed to work outside of testing. See
[SLURM:Resources\#Partitions](SLURM:Resources#Partitions "wikilink") for
a full list of available SLURM partitions to submit jobs to.

### Scratch Disk Space

For jobs which do a lot of disk i/o, it may be advantageous to use a
local disk during execution. Local disk i/o is much faster than network
disk i/o. Every compute node has at least 40GB of scratch disk space on
a local disk, with newer nodes having 250GB. A constraint can be used to
specify desired scratch space availability on nodes.

When a job starts up on a compute node, a scratch directory is
automatically created in `/scratch/$SLURM_JOBID`. Make sure to write
your job scripts to use that directory as scratch space. If you need
more scratch disk space than available, you can A) Reduce the job output
and run into smaller chunks, B) Intermittently clean up output in
scratch space, or C) Use your research data directory. Option C will
incur a performance penalty as disk i/o over the network is slower than
local disk i/o.

**IMPORTANT**: DO NOT use your home directory for writing out files
created during a run, especially if there is a lot of data and/or a lot
of files. This will be slow for your job, and will cause interactive
sessions on the head node to slow down, too. To prevent slow down,
admins may terminate suspect jobs that are actively performing many
read/writes to home directories.

Please see [Quick Start Guide:Disk
Space](Quick_Start_Guide:Disk_Space "wikilink") for more information.

### Permissions of Output Files

Files created by the job script (not the output file(s) mentioned
[previously](SLURM:Quick_Start_Guide#Output_Files "wikilink") are
created by default with permissions of 775 (people in your group can
read and write; everyone else can read) that only allow the owner to
read them. To make it so only you can access files created by your
script, insert the following after the directives in your job script:

`   umask 0077`

SLURM also has a built in variable, SLURM_UMASK, but it does not
function properly at this time. If you want your output files to be
accessable by your group, but not to everyone else, insert the following
after the directives in your job script:

`   umask 0027`

### Environment Variables

SLURM has two types of environment variables. INPUT environment
variables\[7\] are read and used during execution; they override options
set in the batch script, but command line options override any
environment variables. OUTPUT environment variables\[8\] are set by the
controller daemon, and can not be overridden in a batch script. Both
types contain information about the runtime environment, e.g. the
working directory, the node on which it is running, etc. See the
referenced source pages for more information.

### SLURM constraints

When running parallel processing jobs, users typically will want all of
the nodes assigned to the job to be similar (e.g. on the same chassis).
In most cases, it doesn't matter which chassis the job is run on so long
as all the nodes are in the same one.

This scenario requires the use of SLURMs constraint functionality.
Constraints are matched against a nodes' assigned features, which are
dependent upon a node's **[Hardware
Configuration](Cluster:Hardware_Configuration#SLURM_Node_Features "wikilink")**.
To use the constraint function, simply include one of the following line
within your script:

  - Single flag

>
>
>     #SBATCH --constraint="x"

  - Multiple flags allowed

>
>
>     #SBATCH --constraint="x|y|z"
>     ###This allows different constraints to be selected across multiple nodes

  - Matching Multiple flags

>
>
>     #SBATCH --constraint="[x|y|z]"
>     ###This matches a singular constraint against all selected nodes

  - Multiple flags required

>
>
>     #SBATCH --constraint=[x&y&z]
>     ###This requires all constraint listed to be present for a node to be selected

When using constraints, be careful not to require groupings of
constraints that do not exist. For example, do not require
\[broadwell\&haswell\] as that does not exist; meaning the jobs will
never run.

### Job Chaining and Dependencies

Job execution can be dependent on other jobs completing (successfully or
not). This dependency feature is an advanced capability requires
submitting a job that references an existing job on which to be
dependent
via:

`   sbatch --dependency=`<AFTER>`:`<JOB_ID>`[:`<JOB_ID>`...] <mywaitingjob.slurm>`

Along with the *<JOB_ID>* to depend on, an '<AFTER>' clause must be
included. Those options are:

  - after - Can begin after the specified job starts running
  - afterok - Can begin running after the specified jobs ends
    successfully
  - afternotok - Can begin running after the specified job ends with
    failure
  - afterany - Can begin running after specified job ends, regardless of
    status.

A job can have multiple JOB_IDs that it depends upon, which are
delimited with a colon. Dependencies are usually used within job chains,
which are long sequences of small jobs that run sequentially. A simple
bash script example that creates a singular job chain is shown below:

    #!/bin/bash

    FIRST=$(sbatch --parsable $1)
    COUNTER=1
    while [ $COUNTER -lt $2 ]; do
       SECOND=$(sbatch --parsable --dependency=afterany:$FIRST $1)
       let COUNTER=COUNTER+1
       FIRST=$SECOND
    done

The above example requires two input parameters to create a job chain.

1.  Path to the job file to execute: "myscript.slurm"
2.  An integer representing the number of dependent iterations: "100"

### Job Arrays

Job arrays used to start more than one job with a single job script
submission. The --array directive must be used to create an array Job
arrays will have two additional environment variabels set.
**SLURM_ARRAY_JOB_ID**, which is set to the first job ID of the
array, and **SLURM_ARRAY_TASK_ID**, which is the index value for that
job. Essentially, the "SLURM_JOBID" environment variable will only
match the "SLURM_ARRAY_JOB_ID" of the first job. To create output an
output file containing the assigned Array JOB_ID value with special
environment variables, define the output directive as follows within
your job:

`  #SBATCH --output=JOB_NAME-%A_%a.o`

The **%A** will automatically inherit the **SLURM_JOBID** if used
outside of an array; whereas **%a** will be assigned "4,294,967,294
(equivalent to 0xfffffffe or NO_VAL) if used. Please see the [Official
Slurm Job Array Support](http://slurm.schedmd.com/job_array.html)
article for more in depth information.

### Interactive Jobs

  - Though batch submission is the recommended way to submit jobs to the
    cluster
  - Interactive jobs can also be run in the foreground, which can be
    useful for things like:
      - Iterative data exploration at the command line
      - RAM intensive graphical applications like MATLAB or SAS.
      - Interactive "console tools" like R and iPython
  - Interactive jobs can be submitted using the **srun** command with
    the **--pty** option
      - The below example will open a bash command line shell on a node
        for 6 hours with 2GB of RAM.
          - The --pty option allows the session to act like a standard
            terminal on the assigned
>     node.

>
>
>     srun -p small --pty -n 1 --mem=64G --time=6:00:00 --reservation=x11_2 /bin/bash

### X11 forwarding

  - Interactive srun jobs can submit **--x11=\[first|last|all\]** to
    enable
> forwarding

>
>
> ```
>  srun -p small --pty --x11 -n 1 --mem 4000 -t 0-06:00 /usr/bin/bash -i
> ```

## Job States

A job may have one of several states during its lifetime. If you run
**squeue -l**, the job state is reported as *STATE*, in its full or
abbreviated name. See [Official Slurm Listing of Job State
Codes](http://slurm.schedmd.com/squeue.html#lbAG) for the full listing
of states, below are the most common you will see on our cluster:

  - CANCELLED (CA) : Job was explicitly cancelled by the user or system
    administrator. The job may or may not have been initiated.
    COMPLETED (CD) : Job has terminated all processes on all nodes.
    FAILED (F) : Job terminated with non-zero exit code or other failure
    condition.
    NODE_FAIL (NF) : Job terminated due to failure of one or more
    allocated nodes.
    PENDING (PD) : Job is awaiting resource allocation.
    RUNNING (R) : Job currently has an allocation.

## Querying the Cluster

SLURM provides several commands which allow you to query the state of
the queue, the state of a partition, the state of your job, or the state
of the compute nodes. Some officially supported plugins are available
and installed on the cluster to provide even more command line options.
Some of which are designed to replicate output of previously used Torque
commands. See the \[<https://github.com/ubccr/stubl>| official STUBL
support page\] for more information.

### Job information

  - squeue \[--start --job <JOBID>\]
    Use this command to query the list of jobs currently running and
    queued on the cluster
    Use the optional input to determine estimated start time and node(s)
    for a job
  - scontrol show job JOB_ID
    Show detailed information about an active job
  - sinfo --jobs=<JOBID> \[<JOBID> etc\]
    Show detailed information about a completed job

### Changing jobs

  -
    NOTE: you can only modify your own job
  - scontrol update JobID=<JOBID> TimeLimit=d-hh:mm:ss
    Change wall time of a job to d-hh:mm:ss
  - scancel <JOBID>
    Terminate a queued or running job

### Partition information

For information on partitions, visit the
[SLURM:Resources\#Partitions](SLURM:Resources#Partitions "wikilink")
page.

Commands used to query nodse and gather partition information is as
followS:

  - sinfo -p <partition>
    Queries the specified partition
  - sinfo --long --Node --summarize
    Shows an overall listing of nodes sorted by partition
  - scontrol show partition \[<partition>\]
    Show detailed information for all or specified partition
  - spinfo (STUBL)
    Custom designed output for partition information

### Node information

  - sinfo -Nel
    Shows an overall listing of nodes, sorted by nodes
  - sinfo -t idle
    Show only idle nodes
  - scontrol show nodes \[<node>\]
    Shows hardware details for all or specified node, including features
  - snodes (STUBL)
    Displays node information in an easy-to-interpret format

## Matlab Jobs

To submit Matlab to the queue, please see
[Software:Matlab](Software:Matlab "wikilink")

## See Also

  - [SLURM:Job Script Templates](SLURM:Job_Script_Templates "wikilink")
  - [SLURM:Resources](SLURM:Resources "wikilink")
  - [SLURM:Troubleshooting](SLURM:Troubleshooting "wikilink")
  - [Troubleshooting](http://slurm.schedmd.com/troubleshoot.html) on the
    official SLURM support page
  - [FAQ](http://slurm.schedmd.com/faq.html) on the official SLURM
    support page
  - [Unofficial SLURM Cheat
    Sheet](https://confluence.csiro.au/download/attachments/342229594/SLURM.pdf?version=1&modificationDate=1466993467567&api=v2)
    (pdf document)
  - [SLURM Node
    Features](Cluster:Hardware_Configuration#SLURM_Node_Features "wikilink")
    -- specify nodes that you want for your job by their specific
    features

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")
[Category:SLURM](Category:SLURM "wikilink")
[Category:Software](Category:Software "wikilink")

1.  [SLURM Quickstart Guide](http://slurm.schedmd.com/quickstart.html)
    at Department of Energy's National Nuclear Security Administration
2.  [Slurm Workload Manager
    article](https://en.wikipedia.org/wiki/Slurm_Workload_Manager) at
    Wikipedia
3.  [Job Submission](http://slurm.schedmd.com/sbatch.html) under
    *OPTIONS*
4.  Google Search
    [1](https://www.google.com/search?q=slurm+sbatch+edu+examples&oq=slurm+sbatch+edu+examples);
    or type sbatch --help on the command line
5.  [SLURM Cheat Sheet](https://slurm.schedmd.com/pdfs/summary.pdf)
6.  [Resources in
    SLURM](http://slurm.schedmd.com/cons_res.html#Consumable)
7.  [Sbatch Input Variables](http://slurm.schedmd.com/sbatch.html#lbAF)
    at SchedMD
8.  [Sbatch Output Variables](http://slurm.schedmd.com/sbatch.html#lbAG)
    at SchedMD---
title: SLURM:Quick Start Guide
permalink: /SLURM:Quick_Start_Guide/
---

