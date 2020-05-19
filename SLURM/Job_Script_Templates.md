## Prerequisites and Provisos

  - Before submitting any jobs, please read **and** understand the
    [Cluster:User Agreement](Cluster:User_Agreement "wikilink").
  - Be sure to read the [SLURM:Torque Conversion
    Script](SLURM:Torque_Conversion_Script "wikilink") instructions for
    converting legacy scripts.
  - Note that any given system is using approximately 1GB of its memory
    for operating system and filesystem purposes.
  - When configuring your jobs, please use 1GB less of memory than the
    blade claims to have.
  - The *generalGrp* fair share group is provided here. Please replace
    that with your designated fair share group.
  - You **must** specify an email address even if you do not want
    notifications

## Serial Jobs

  - Serial jobs only use a single processor

### Single processor job, 128MB RAM with 96 Hour Time Limit

    #!/bin/bash
    #SBATCH --partition=medium
    #SBATCH --job-name="single_proc_128mb"
    #SBATCH --constraint="skylake"
    #SBATCH --nodes=1
    #SBATCH --tasks-per-node=1
    #SBATCH --time=0-96:00:00
    #SBATCH --account="generalGrp"
    #SBATCH --mail-type=BEGIN
    #SBATCH --mail-user=my_username@wfu.edu
    #SBATCH --output="single_proc_128mb-%j.o"
    #SBATCH --error="single_proc_128mb-%j.e"
    #SBATCH --mem=128MB
    # Note: SLURM has no batch input for cputime, excluding.
    # Note: NCPUS directive is redundant from expected nodes#:ppn# input, excluding.

    # set up your environment - this is for bash. For csh/tcsh: source /etc/profile.d/modules.csh
    umask 027
    . /etc/profile.d/modules.sh
    module load rhel7/compilers/intel-2018-lp64

    cd /scratch/${SLURM_JOBID}
    ###Now do your stuff

    ###  Don't forget to copy results out of /scratch to a /deac directory!

### Single processor job, 128MB RAM with 2 Day Time Limit

    #SBATCH --partition=small
    #SBATCH --job-name="single_proc_two_day"
    #SBATCH --constraint="haswell"
    #SBATCH --nodes=1
    #SBATCH --tasks-per-node=1
    #SBATCH --time=0-48:00:00
    #SBATCH --account="generalGrp"
    #SBATCH --mail-type=BEGIN
    #SBATCH --mail-user=my_username@wfu.edu
    #SBATCH --output="single_proc_two_day-j%.o"
    #SBATCH --error="single_proc_two_day-j%.e"
    #SBATCH --mem=128MB

    umask 027
    cd /scratch/${SLURM_JOBID}
    ###Now do your stuff

    ###  Don't forget to copy results out of /scratch to a /deac directory!

## Multiple Processor Jobs

### Parallel Job Type 1

  - N nodes using X processors per node, using ethernet enabled nodes
  - A program needing 128MB of RAM per processor, totaling 1GB per node
  - 16 Hour Time Limit
      - Even though the time limit is \<24hours, the node requirement
        requires the job to run on the medium partition

<!-- end list -->

```
#SBATCH --partition=medium
#SBATCH --job-name="multinode_job"
#SBATCH --nodes=4
#SBATCH --tasks-per-node=8
#SBATCH --cpus-per-task=1
#SBATCH --time=0-16:00:00
#SBATCH --account="generalGrp"
#SBATCH --mail-type=BEGIN
#SBATCH --mail-user=my_username@wfu.edu
#SBATCH --output="multinode_job.o"
#SBATCH --error="multinode_job.e"
#SBATCH --mem=1gb
#SBATCH --constraint="ucs3-2|ucs3-3|ucs3-4"

umask 027
cd /scratch
cd $SLURM_JOBID

###Now do your stuff

###  Don't forget to copy your data from /scratch to your /deac* directory
```

  - Important items to note
      - SLURM has no **cput** directive\! Base your time value purely on
        the overall estimated runtime.
      - The **mem** directive is the overall total (per CPU requirement
        \* nodes \* CPUs = mem).
          - An available directive to use is **--mem-per-cpu=memory**,
            which allocates memory on a per-CPU basis.
      - The list of *ucs\#-\#* in the **--constraint** directive should
        be customized to the type of parallel job you wish to run. For
        more information on hardware features, see [Cluster:Hardware
        Configuration](Cluster:Hardware_Configuration "wikilink").

## Job Script for GPU

    #!/bin/bash
    #SBATCH --job-name=GPUJOB
    #SBATCH --nodes=1
    #SBATCH --ntasks-per-node=1
    #SBATCH --time=0-12:00:00
    #SBATCH --output="1_HPL-CISCO-%j.o"
    #SBATCH --error="1_HPL-CISCO-%j.e"
    #SBATCH --mail-user=username@wfu.edu
    #SBATCH --mail-type=BEGIN,END,FAIL
    #SBATCH --account="researchGrp"
    #SBATCH --partition=gpu
    #SBATCH --mem=120gb
    #SBATCH --workdir="/deac/researchGrp/user/CUDA"
    #SBATCH --gres=gpu:P100:1

  - IMPORTANT DIRECTIVES

:\*--gres=gpu\[type:\#\]

::\* This directive specifies the type of GPU required and the number of
cards

::\* By default, a singular GPU of anytype will be used.

::\* Optionally, users can specify the GPU type by name and number of
cards required.

::\* Valid types are:
[m6](Information:GPU_Computing#Tesla_M6_GPU_Nodes "wikilink") and
[s2050](Information:GPU_Computing#Tesla_S2050_GPU_Nodes "wikilink")

:::\* See
[Information:GPU_Computing](Information:GPU_Computing "wikilink") for
most up to date list of DEAC cluster GPU information

:\*--partition=gpu

::\* The GPU partition will assign higher priority to GPU type jobs for
using the hardware for their designated purpose

## Job Script for UCS Blades

  - The new blade specs:
      - 32/44 processing cores available per blade
      - 128GB/188GB/256GB of RAM
      - 10Gbps Bandwidth per ethernet channel (dual-channel)
      - 300G of storage, 50GB/220G/250G/425GB for scratch

### Recognized Constraints

  - In order for jobs to run on the newer CISCO UCS nodes, the job
    scripts have to be modified to the following features:
  - These attributes have been placed to the blades:
      - haswell -- (The Haswell Intel Architecture)
      - broadwell -- (The Broadwell Intel Architecture)
      - skylake -- (The Skylake Intel Architecture)
      - scr50gb -- (50G of /scratch space available)
      - scr220gb -- (220G of /scratch space available)
      - scr250gb -- (250G of /scratch space available)
      - scr425gb -- (425G of /scratch space available)
      - ucs\#-\#\# -- (Specific Name of UCS Chassis in SLURM)

<!-- end list -->

  - Node details of a 32-Core UCS
blade

`NodeName=a1a-u3-c5-b1 Arch=x86_64 CoresPerSocket=16`
`  CPUAlloc=0 CPUTot=32 CPULoad=32.15`
`  AvailableFeatures=ucs3-5,scr50gb,haswell,rhel7`
`  ActiveFeatures=ucs3-5,scr50gb,haswell,rhel7`
`  Gres=(null)`
`  NodeAddr=10.1.52.129 NodeHostName=a1a-u3-c5-b1 Version=19.05.5`
`  OS=Linux 3.10.0-957.21.3.el7.x86_64 #1 SMP Fri Jun 14 02:54:29 EDT 2019 `
`  RealMemory=128000 AllocMem=0 FreeMem=2292 Sockets=2 Boards=1`
`  State=IDLE ThreadsPerCore=1 TmpDisk=50000 Weight=1 Owner=N/A MCS_label=N/A`

  - Node details of a 44-Core UCS
blade

`NodeName=a1a-u3-c6-b1 Arch=x86_64 CoresPerSocket=22`
`  CPUAlloc=0 CPUTot=44 CPULoad=32.01`
`  AvailableFeatures=ucs3-6,scr220gb,skylake,rhel7`
`  ActiveFeatures=ucs3-6,scr220gb,skylake,rhel7`
`  Gres=(null)`
`  NodeAddr=10.1.52.137 NodeHostName=a1a-u3-c6-b1 Version=19.05.5`
`  OS=Linux 3.10.0-957.21.3.el7.x86_64 #1 SMP Fri Jun 14 02:54:29 EDT 2019 `
`  RealMemory=188000 AllocMem=0 FreeMem=2518 Sockets=2 Boards=1`
`  State=IDLE ThreadsPerCore=1 TmpDisk=220000 Weight=1 Owner=N/A MCS_label=N/A`

### UCS Job Script Template

  - A generic example of job script of UCS (tengig) nodes:
      - The small partition has a 24 hour maximum run time

<!-- end list -->

    #SBATCH --partition=small
    #SBATCH --job-name="generic_ucs"
    #SBATCH --constraint="skylake"
    #SBATCH --nodes=1
    #SBATCH --tasks-per-node=16
    #SBATCH --time=06:00:00
    #SBATCH --account="fairshareGrp"
    #SBATCH --mail-type=BEGIN,END,FAIL
    #SBATCH --mail-user=username@wfu.edu
    #SBATCH --output="generic_ucs-%j.o"
    #SBATCH --error="generic_ucs-%j.e"
    #SBATCH --mem=127gb

  - All UCS (tengig) nodes have:
      - 32 or more cores, so the above generic example will run on any
        available ucs node
      - 128gb of memory. Using the previous recommendation, the max
        value you should request is 127gb

<!-- end list -->

  - If you wish to be more specific on which type of need to be more
    specific on the resources needed for specific UCS blades:
      - For a **32-core** single UCS blade only:

>
>
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=32
>     #SBATCH --constraint="haswell"

  - For a **44-core** single UCS blade only:

>
>
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=44
>     #SBATCH --constraint="broadwell|skylake"

  - This template was used during a testing period. If you encounter
    errors or incidents, please send them to <deac-help@wfu.edu>

[Category:SLURM](Category:SLURM "wikilink")---
title: SLURM:Job Script Templates
permalink: /SLURM:Job_Script_Templates/
---

