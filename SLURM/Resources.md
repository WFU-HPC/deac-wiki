# Resource Requests

## Standard Resource Request

Resources for a job are requested with 4 primary directives. In a SLURM
script:

`   #SBATCH --nodes=1`
`   #SBATCH --tasks-per-node=8`
`   #SBATCH --cpus-per-task=1`
`   #SBATCH --mem=16gb`

Which requests 1 node, 8 CPUs, and 16GB of RAM.

## Generic Resource Request - GPUs

Generic resource scheduling (GRES) is used for requesting GPU resources
with one primary directive. In a SLURM script:

`   #SBATCH --partition="gpu"`
`   #SBATCH --nodes=1`
`   #SBATCH --gres=gpu:1`

Which requests 1 GPU to be used from 1 node belonging to the GPU
partition. Obviously, GPU resources are requested differently that
standard resources. Official documentation is available from SchedMD on
GRES configuration\[1\] and SBATCH GRES specification\[2\].

# Partitions

### *debug*

  -   - Purpose: Default partition, for testing only - check if your job
        starts.
      - Limits: \<06:00:00
      - Priority: 10

### *small*

  -   - Purpose: Small consumption, short serial or parallel jobs
      - Limits: \<24:00:00, 1 node
      - Priority: 40

### *medium*

  -   - Purpose: Mid-range jobs
      - Limits: \<7-00:00:00, \<8 nodes
      - Priority: 30

### *large*

  -   - Purpose: Large consumption, long running jobs
      - Limits: \<365-00:00:00, no node limit
      - Priority: 20

### *gpu*

  -   - Purpose: GPU required jobs
      - Limits: \<365-00:00:00, no node limit
      - Priority: 50

# List of Resource Specifiers

Below is a list of all resource specifications and their definitions.
Please see the official documentation for a requesting resources and
detailed definitions with batch submission.\[3\] There are many SLURM
users, so a Google search is bound to find great documentation as well,
like this page at the Leibniz Supercomputing Centre\[4\].

  - **tasks-per-node**=
      - *integer* -- processes per node (*not* processors)
  - **nodes**=
      - *integer* -- number of nodes OR
      - *string* -- name of specific node
  - **mem**
      - *string* -- memory allocation per node, 90gb, 16gb, 512mb, etc
  - **time**
      - *string* -- time specification, ((d-)hh:mm:ss; Maximum amount of
        real time during which the job can be in the running state.
  - **gres**= (Generic Resources Scheduling)
      -   - ''string\[\[:string\]:number -- **GPU** allocation example,
            gpu:4

### cpusets

In brief:

> In the Linux kernel, the cpuset facility provides a mechanism for
> creating logical entities called "cpusets" that encompass definitions
> of CPUs and NUMA Memory Nodes (if NUMA is available). Cpusets
> constrain the CPU and Memory placement of a task to only the resources
> defined within that cpuset. These cpusets can then be arranged into a
> nested hierarchy visible in the "cpuset" virtual filesystem. Sets of
> tasks can be assigned to these cpusets to constrain the resources that
> they use. The tasks can be moved from one cpuset to another to utilize
> other resources defined in those other cpusets.\[5\]

## Node Features

  - In SLURM, nodes may be tagged with a number of strings. These
    strings are called *features*. You can query any particular node to
    see its
properties:

`$ scontrol show node bc03bl01`
`NodeName=bc03bl01 Arch=x86_64 CoresPerSocket=4`
`   CPUAlloc=0 CPUErr=0 CPUTot=8 CPULoad=0.47 Features=`**`ethernet,clan03,scr9gb`**
`   Gres=(null)`
`   NodeAddr=152.17.40.65 NodeHostName=bc03bl01 Version=14.11`
`   OS=Linux RealMemory=96732 AllocMem=0 Sockets=2 Boards=1`
`   State=IDLE ThreadsPerCore=1 TmpDisk=0 Weight=1`
`   BootTime=2015-07-29T15:21:51 SlurmdStartTime=2015-09-11T13:58:01`
`   CurrentWatts=0 LowestJoules=0 ConsumedJoules=0`
`   ExtSensorsJoules=n/s ExtSensorsWatts=0 ExtSensorsTemp=n/s`

  - A node with GPU resources available has the following listed in it's
    properties:

`$ scontrol show node gpu05 `
`NodeName=gpu05 Arch=x86_64 CoresPerSocket=6`
`  CPUAlloc=0 CPUErr=0 CPUTot=6 CPULoad=0.10 Features=`**`gpu`**
`  Gres=`**`gpu:4`**
`  NodeAddr=152.17.36.141 NodeHostName=gpu05 Version=14.11`
`  OS=Linux RealMemory=23986 AllocMem=0 Sockets=1 Boards=1`
`  State=IDLE ThreadsPerCore=1 TmpDisk=0 Weight=1`
`  BootTime=2015-12-16T12:55:25 SlurmdStartTime=2015-12-16T12:55:54`
`  CurrentWatts=0 LowestJoules=0 ConsumedJoules=0`
`  ExtSensorsJoules=n/s ExtSensorsWatts=0 ExtSensorsTemp=n/s`

# References

<references/>

[Category:SLURM](Category:SLURM "wikilink")
[Category:GPU](Category:GPU "wikilink")

1.  [GRES Configuration](http://slurm.schedmd.com/gres.html)
2.  [SBATCH GRES
    Specification](http://slurm.schedmd.com/sbatch.html#OPT_gres)
3.  [Slurm Sbatch Documentation - Job
    Submission](http://slurm.schedmd.com/sbatch.html)
4.  [Leibniz Supercomputing Centre - Resource
    Specification](https://www.lrz.de/services/compute/linux-cluster/batch_parallel/specifications/)
5.  [cpuset (cset) tutorial - Novell,
    Inc.](https://www.suse.com/documentation/slerte_11/slerte_tutorial/data/slerte_tutorial.html)---
title: SLURM:Resources
permalink: /SLURM:Resources/
---

