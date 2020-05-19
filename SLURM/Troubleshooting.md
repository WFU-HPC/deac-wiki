# Windows Newline

If you write any scripts under Windows and transfer them to a UNIX/Linux
machine, every line will contain an extra character (^M). This character
appears as a result of different End-Of-Line (EOL) conventions\[1\].
Unfortunately, it does more than just appear annoyingly at the end of
every line. The symbols are interpreted when run by the scripts
interpreter (i.e. [PERL](Software:Perl "wikilink") or
[bash](Quick_Start_Guide:Bash "wikilink") or
[tsch](Quick_Start_Guide:Tcsh "wikilink")). Executable shell scripts
written under Windows, transferred to the cluster, and run without
change will almost certainly fail with a "Command not found" error
message.

To remove these "control" characters, there is a command line utility
called `dos2unix` which will strip the characters from the file. See the
man page for usage details.

## References

<references/>

# Memory Consumption

Memory consumption can be a primary reason for job cancellation... read
the following to assist with troubleshooting...

## Refresher

**Physical memory** is RAM. Operating systems, however, have the concept
of **virtual memory**: virtual memory includes some disk space
specifically set aside for use as program memory (as opposed to file
storage). This disk space is known as **swap**.

This is useful because it allows programs to temporarily grow in memory
usage without crashing the computer: any excess usage can be transferred
to disk. However, this imposes a huge performance penalty. Disk access
times may be a factor of a million or more slower than RAM.\[2\]

## Check Job Statistics

When you submit a job, you make a request for **mem** -- based on the
total memory used on a PER NODE basis... this differs from previous
behavior utilized in Torque. Once the job is running, the resource
manager [SLURM](SLURM "wikilink") tracks the actual resources used. If
you run "**scontrol show job JOBID**" on a running job, you will see
something like
this:

`JobId=6449 JobName=Low_Size_HPL_C11`
`  UserId=vallesd(10013) GroupId=vallesd(10013)`
`  Priority=437 Nice=0 Account=admingrp QOS=normal`
`  JobState=RUNNING Reason=None Dependency=(null)`
`  Requeue=1 Restarts=0 BatchFlag=1 Reboot=0 ExitCode=0:0`
`  RunTime=3-19:30:33 TimeLimit=4-00:00:00 TimeMin=N/A`
`  SubmitTime=2015-09-11T16:08:00 EligibleTime=2015-09-11T16:08:00`
`  StartTime=2015-09-11T16:08:01 EndTime=2015-09-15T16:08:01`
`  PreemptTime=None SuspendTime=None SecsPreSuspend=0`
`  Partition=large AllocNode:Sid=headnode:31102`
`  ReqNodeList=(null) ExcNodeList=(null)`
`  NodeList=a1a-u2-c10-b[1-4,6-8],a1a-u2-c11-b1`
`  BatchHost=a1a-u2-c10-b1`
`  NumNodes=8 NumCPUs=256 CPUs/Task=1 ReqB:S:C:T=0:0:*:*`
`  Socks/Node=* NtasksPerN:B:S:C=32:0:*:* CoreSpec=*`
`  MinCPUsNode=32 MinMemoryNode=125G MinTmpDiskNode=0`
`  Features=haswell Gres=(null) Reservation=(null)`
`  Shared=OK Contiguous=0 Licenses=(null) Network=(null)`
`  Command=/home/vallesd/hpl-2.1/bin/chassis11/test_low_problem_sizes_carlson.SLURM`
`  WorkDir=/home/vallesd`
`  StdErr=/home/vallesd/lowsizes_chassis11-6449.e`
`  StdIn=/dev/null`
`  StdOut=/home/vallesd/lowsizes_chassis11-6449.o`

This is essentially the output of all metadata SLURM tracks about your
job, including resources used and requested, directives, output
information and tracking information. Note, this output can only be seen
DURING job execution. The information is also inserted into your job
output file when the task prolog runs.

During and after job execution, you can also see resources utilized with
the [sacct](SLURM_commands#sacct "wikilink") command. To see
specifically Nodes, CPUs, and Memory requested, run:

`[username@headnode ~]$ `**`sacct`` ``--jobs=6449`` ``--format``
``JobID,JobName,NCPUS,NNodes,ReqCPUs,ReqMem`**
`       JobID    JobName      NCPUS   NNodes  ReqCPUS     ReqMem`
`------------ ---------- ---------- -------- -------- ----------`
`6449         Low_Size_+        256        8      256      125Gn`
`6449.0            orted          7        7        7      125Gn`

When a job completes you can see consumed resources (CPUs, Nodes, Memory
and Time) specifically by running:

`[username@headnode ~]$ `**`sacctr`` ``--jobs=JOBID`` ``--format``
``JobId,JobName,NCPUS,NNodes,MaxRSS,Elapsed`**
`      JobID    JobName      NCPUS   NNodes     MaxRSS    Elapsed                                          NodeList `
`------------ ---------- ---------- -------- ---------- ---------- -------------------------------------------------- `
`6449         Low_Size_+        256        8 121896960K 3-22:30:00 a1a-u2-c10-b[1-4,6-8],a1a-u2-c11-b1                `
`6449.0            orted          7        7 121896960K 3-22:30:00 a1a-u2-c10-b[2-4,6-8],a1a-u2-c11-b1     `

Jobs where MaxRSS exceeds the requested amount of memory will be
cancelled by SLURM.

If it is the first time you are running a particular class of job, it
would be good if you ran one, requesting lots of memory, and then
examine it via the [sacct](SLURM_commands#sacct "wikilink") command to
see the actual amount your job will need. Be sure to allow about 1GB per
node for system usage.

Remember that memory allocation must be requested on a **per NODE**
basis, overall memory utilization is not requested (SLURM calculates
that for us)\!

The other complication is that the cluster is a multi user system. Any
one node may have more than one job running on it, owned by more than
one user. When job requests come in, if SLURM finds a node that has
enough free resources (cpus and memory) to handle the amount requested
by a job, that job will be scheduled on that node.

Now, if that job's memory usage grows beyond its request, it will now be
given a "CANCELLED" status and the job will die. There is also a
possibility that the node could crash and end all the other jobs that
may have been allocated to that node.

## Request Memory Correctly

As it is undesirable for jobs to swap to disk, request memory generously
but accurately. Obviously, the closer your request to what is actually
needed, the better - but we don't want to risk your job dying, or the
compute node potentially crashing. In SLURM, memory requested is on a
PER NODE basis, so

It is very important to understand how much memory your job will
actually use. Requesting the minimum required may get more of your jobs
running sooner. Here is an example:

  - Job actually needs 14 GB memory
  - Job requests 16 GB memory
  - Therefore, the job cannot run on nodes with 16 GB of RAM because of
    the 16 GB, only 15 GB are available for user processes. 1 GB is
    reserved for the system. This eliminates 84 of the 16 GB nodes that
    are available in the cluster (as of 2015-09-15).

On the other hand, if the code you run does not control its memory usage
well, i.e. it can grow to an unknown amount during a run, then it is
better to request for more memory to avoid the job being cancelled if it
overruns its memory request.

Again, it is very important to understand the resource requirements for
your jobs. Make several trial runs in order to understand what your job
needs so you may request only as much as is necessary (plus a small
safety margin).

# Job Submission Troubleshooting

> ## NODE_FAIL
>
>   - Problem Symptom: (from job email)
>
> <!-- end list -->
>
>   -
>
>         Job exited with exit code 1.
>
> <!-- end list -->
>
>   - Problem Symptom: No output files
> >     created
>
> >
> >
> >     [2015-09-14T16:58:51.996] [6454] Could not open stdout file /home/username/babel/test/SAMHD1/salsbufr_test-6454.o: No such file or directory
> >     [2015-09-14T16:58:51.996] [6454] IO setup failed: No such file or directory
>
>   - Problem resolution
>
> :\* Most likely this is an admin issue with the node
>
> ::\* Often the primary culprit is research group filesystems are not
> mounted and proper output files are not created.
>
> ::\* If output files are attempting to write to these filesystems,
> prolog scripts die without logging information
>
> ::\* The job will often sit in a "Running" state without doing
> anything until the NODE_FAIL message is sent
>
> :\* Reply to the email and send it to deac-help@wfu.edu and the HPC
> team will investigate.
>
> ## (PartitionTimeLimit)
>
>   - Problem Symptom: (from *squeue -u username* output)
>
> >
> >
> > ```
> >  $ squeue -u username
> >              JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
> >               1234     small     test username PD       0:00      1 (PartitionTimeLimit)
> > ```
>
>   - Problem Symptom: Job does not run
>
> <!-- end list -->
>
>   - Problem resolution
>
> :\* You are requesting resources that exceed the defined limits of the
> specified partition
>
> ::\* Check partition limits by running *scontrol show partition small*
> (for this case)
>
> ::\* Check requested job resources by running *scontrol show job 1234*
>
> :\*Change partition requested by canceling your job and editing the
> batch script, OR by running
>
> ::\***scontrol update JobID=1234 Partition=medium** to change
> partition requested
>
> :\*Change requested resources by canceling your job and editing batch
> script, OR by running
>
> ::\*Change Timelimit: **scontrol update JobID=1234
> TimeLimit=\<24:00:00** (for this case)
>
> ::\*Change Requested Nodes (and CPU\# if possible): **scontrol update
> JobID=1234 \[NumCPUs=(total needed)\]** (for this case)
>
> :::\*Remember, it is possible to request up to 32 CPUs per node, but
> be sure constraints don't prevent that as a possible option if
> changing

# Job Stuck in Queue or Stalled

# Potential Reasons

  - Resource request has conflicting resource specifications that result
    in no viable nodes on which to run the job
  - Resource request is so specific only a few nodes exist to fulfill
    the request
  - Resource request needs resources that are not available yet

## Resource Specification Collisions

  - "I need all the memory on a
>     node"

>
>
>     ############################## SLURM directives ##########################
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=20
>     #SBATCH --mem=128gb
>     #SBATCH --constraint=tengig
>     ##########################################################################
>
>   - We have nodes with 128GB of RAM. This should work. Right? Wrong\!
>
> <!-- end list -->
>
>   - Explanation of Resource Allocation
>
> <!-- end list -->
>
>   - The SLURM workload manager knows that your job requires 128GB of
>     RAM.
>   - SLURM will only schedule your job on a node that has 128GB of
>     ***available*** RAM.
>   - Operating systems, system services, and the cluster filesystems
>     consume memory too. A good rule of thumb is 1GB.
>   - So, a 128GB blade really only has 127GB of RAM for use by jobs.
>     So, the above job will not run on our cluster of 128GB nodes.
>
> <!-- end list -->
>
>   - Corrected Resource
>     Request
>
> <!-- end list -->
>
>     ############################## SLURM directives ##########################
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=20
>     #SBATCH --mem=127gb
>     #SBATCH --constraint=tengig
>     ##########################################################################

  - "I only want to run on '16 core tengig
>     nodes'":

>
>
>     ############################## SLURM directives ##########################
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=20
>     #SBATCH --mem=128gb
>     #SBATCH --constraint=tengig&sandy
>     ##########################################################################
>
>   - Explanation of Resource Allocation
>
> <!-- end list -->
>
>   - Here, the constraint syntax is correct assuming any one particular
>     node with SANDY processors is eligible for use.
>   - Unfortunately, none of the sandy blades do not have the **20**
>     CPUS.
>   - As a result, the sandy constraint and 20 CPU requirement are
>     mutually exclusive and result in a "null" set of nodes to run on.
>
> <!-- end list -->
>
>   - Corrected Resource
>     Request
>
> <!-- end list -->
>
>     ############################## SLURM directives ##########################
>     #SBATCH --nodes=1
>     #SBATCH --tasks-per-node=20
>     #SBATCH --mem=128gb
>     #SBATCH --constraint=tengig&ivy
>     ##########################################################################
>
>   - As a best practice, ***if*** you really want only nodes with 20
>     processors, you want to reduce all other optional resource
>     requests to avoid the possibility of mutually exclusive resource
>     requests. IE (exclude the ivy, and tengig constraint).
>   - Note: it's not considered a best practice to restrict your jobs to
>     only ONE, SPECIFIC type (in this case, ivy) unless there is a
>     REALLY good reason.
>
> :\* Clarification: It's okay for your job to be restricted to ONE
> GROUP (especially for parallel jobs). However, you should include as
> many candidate clans as possible using the "constraint=X|Y|Z" OR
> capability of SLURM's constraint directive so that your job has better
> chances of running on the cluster.

# Potential Job Termination Issues

> ## Resource Utilization Violation
>
> >   - Problem Symptom (from job email)
> >
> >         Job cancelled by the system administrator.
> >
> > <!-- end list -->
> >
> >   - Resource Required (from job email)
> >
> > >
> > >
> > >     Requested time limit:   23:00:00
> > >     Requested memory:     48000M (per Node)
> > >     Total CPU time :          00:00:30
> > >     Total Allocated CPUs:  1
> > >     Total Allocated Nodes: 1
> >
> >   - Resource Usage (from job email)
> >
> > >
> > >
> > >     JOB ID:      6398.batch
> > >     # CPUS:     1
> > >     # NODES:  1
> > >     MEM/task: 50385312K
> > >     JOB Name: batch
> >
> >   - Analysis of request
> >     Job requested 1 processors (nodes=1, CPUS=1)
> >     Job requested 48GB of memory (mem=48gb)
> >     Job consumed 48.05GB overall (MEM: 50385312K)
> >
> > <!-- end list -->
> >
> >   - Problem resolution
> >     Increase the requested memory value
> >     Resolve the memory request mismatch.
> >     As soon as memory is exceed, the job will be cancelled by the
> >     scheduler.
>
>   - Memory Resource Consumption fails before reaching request
>     If a job fails due to a malloc error before the requested memory
>     limit has been reached, it could be due to ulimits
>     Include **'ulimit -v hard**' below your directives, and above the
>     script portion of your job to see if that fixes the issue.
>
> ## Job Deleted
>
> >   - Problem Symptom (from job email)
> >
> >         Job cancelled by the system administrator.
> >
> > <!-- end list -->
> >
> >   - Probable Causes
> >     The job was simply deleted by a user. No resolution needed.
> >     The job was deleted because of a system software bug.
> >
> > <!-- end list -->
> >
> >   - Problem Solution
> >     If you did not delete the job, contact deac-help@wfu.edu to
> >     report the
>     problem.

# Email from SLURM

>
>
>     Job <test_48gb.slurm> was executed on node(s) <a1a-u2-c10-b1>, in partition <small>, as user <username> from group <researchgrp>.
>     The initial working directory of this job was /deac/researchGrp/username/output.
>
>     Job cancelled by the system administrator.
>
>     Job Times:
>     =======
>         Submitted:  2015-09-04 16:40:17
>         Started:      2015-09-04 16:40:17
>         Ended:       2015-09-04 16:40:47
>         Elapsed:    00:00:30
>
>     Job Resource Usage Summary:
>     ======================
>
>         JOB ID:      6398
>         # CPUS:     1
>         # NODES:  1
>         MEM/task: n/a
>         JOB Name: test_48gb.slurm
>
>         JOB ID:      6398.batch
>         # CPUS:     1
>         # NODES:  1
>         MEM/task: 50385312K
>         JOB Name: batch
>
>
>     Requested Resources and Totals:
>     =======================
>         Requested time limit:   23:00:00
>         Requested memory:     48000M (per Node)
>         Total CPU time :          00:00:30
>         Total Allocated CPUs:  1
>         Total Allocated Nodes: 1

# Job Error Output File from SLURM (on filesystem)

>
>
>     slurmstepd: Job 6398 exceeded memory limit (50385312 > 49152000), being killed
>     slurmstepd: Exceeded job memory limit
>     slurmstepd: *** JOB 6398 CANCELLED AT 2015-09-04T16:40:47 *** on a1a-u2-c10-b1
>     slurmstepd: task_p_post_term: rmdir(/dev/cpuset/slurm6398/slurm6398.4294967294_0) failed Device or resource busy

<references/>

[Category:SLURM](Category:SLURM "wikilink")

1.  [Newline article at Wikipedia](http://en.wikipedia.org/wiki/Newline)
2.  [Disk vs. Memory speed discussion at Joel on Software
    forums](http://discuss.joelonsoftware.com/default.asp?joel.3.731942.7)---
title: SLURM:Troubleshooting
permalink: /SLURM:Troubleshooting/
---

