__forcetoc__

# SLURM commands

## User Commands

  - SLURM commands have many different parameters and options.
  - Any favorite custom options or detailed information should be added
    to this page down below.

<table>
<thead>
<tr class="header">
<th><p>Command</p></th>
<th><p>Slurm</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cluster Status</p></td>
<td><p><a href="http://slurm.schedmd.com/sinfo.html#OPT_node">sinfo</a> [-Nel]</p></td>
</tr>
<tr class="even">
<td><p>Queue List</p></td>
<td><p><a href="http://slurm.schedmd.com/squeue.html">squeue</a> [-u <username>]</p></td>
</tr>
<tr class="odd">
<td><p>Job Submission</p></td>
<td><p><a href="http://slurm.schedmd.com/sbatch.html">sbatch</a></p></td>
</tr>
<tr class="even">
<td><p>Job deletion</p></td>
<td><p><a href="http://slurm.schedmd.com/scancel.html">scancel</a> <job_id></p></td>
</tr>
<tr class="odd">
<td><p>Job status</p></td>
<td><p><a href="http://slurm.schedmd.com/squeue.html">squeue</a> <job_id></p></td>
</tr>
<tr class="even">
<td><p>Job information</p></td>
<td><p><a href="http://slurm.schedmd.com/scontrol.html#OPT_show">scontrol</a> show job <job_id><br />
</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p><a href="http://slurm.schedmd.com/sstat.html#OPT_jobs">sstat</a> -j <job_id>.batch</p></td>
</tr>
<tr class="even">
<td><p>Job Completion Info</p></td>
<td><p><a href="http://slurm.schedmd.com/sacct.html#OPT_jobs">sacct</a> -j <job_id> -l</p></td>
</tr>
<tr class="odd">
<td><p>Node List</p></td>
<td><p><a href="http://slurm.schedmd.com/sinfo.html#OPT_node">sinfo</a> -N</p></td>
</tr>
<tr class="even">
<td><p>Show Reservation</p></td>
<td><p><a href="http://slurm.schedmd.com/scontrol.html#OPT_show">scontrol</a> show reservation=<resname></p></td>
</tr>
<tr class="odd">
<td><p>Fairshare Info</p></td>
<td><p><a href="http://slurm.schedmd.com/sshare.html#OPT_accounts=">sshare</a> [-A <account>] [-u <user>]</p></td>
</tr>
<tr class="even">
<td><p>Job Queue Priority</p></td>
<td><p><a href="http://slurm.schedmd.com/sprio.html">sprio</a></p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Environment Variables

  - Nearly every SLURM command has an option to set an output format
    *environment variable* to change it's default output
  - Output Formatting can be made temporary by setting the environment
    variable on command line.
  - It can also be made permanent for your account by adding that
    command to your "~/.bashrc" file

:\*Before adding to your "~/.bashrc" file it is recommended that you
test setting the environment variable on command line first

:\*If not tested first, you will need to log out and back in for the
command to run from "~/.bashrc"

  - If the environment variable is successfully set, the change in
    format to the command output will be immediate.
  - Another way to confirm is to run **echo $SQUEUE_FORMAT** for
    example

:\*This will show the applied value to the variable if set.

:\*If the result returns blank, the variable was not set.

  - To undo your test, run **unset $SQUEUE_FORMAT** to unassign the
    environment variable
  - If successfully unassigned, the change in format will revert back to
    default immediately.

## squeue

  - Display list of all jobs in the queue

<!-- end list -->

    [username@headnode ~]$ squeue -u username
     JOBID PARTITION      NAME     USER ST       TIME  NODES NODELIST(REASON)
     10011     small   aweome1 username PD       0:00      1 (Resources)
     10012     small   a-groov username PD       0:00      1 (Priority)
     10013     small  a-awesom username PD       0:00      1 (Priority)
     10032     small   tubular username  R      12:43      1 a1a-u2-c2-b8
     10000    medium  cowabung username  R   23:29:13      1 a1a-u2-c11-b2
     10001    medium   radical username  R   23:29:47      1 a1a-u2-c11-b1
     10002    medium  most-exc username  R   23:30:16      1 a1a-u2-c10-b1

### Start Time

  - Display estimated start times of next jobs in the queue, as well as
    expected host nodes

<!-- end list -->

    [username@headnode ~]$ squeue --start
     JOBID PARTITION      NAME     USER ST          START_TIME  NODES SCHEDNODES           NODELIST(REASON)

     11901    medium  funstuff username PD 2017-02-21T08:40:15      8 bc12bl[01,04,06-07,0 (Resources)
     12001    medium  superman username PD 2017-02-21T09:03:25      8 a1a-u2-c5-b7,a1a-u2- (Resources)
     12022     small   yellow1 username PD 2017-02-21T09:08:24      1 a1a-u2-c10-b3        (Resources)
     12023     small   yellow2 username PD 2017-02-21T09:09:56      1 a1a-u2-c10-b5        (Priority)
     12024     small   yellow3 username PD 2017-02-21T09:10:47      1 a1a-u2-c10-b6        (Priority)
     12025     small   yellow4 username PD 2017-02-21T09:11:28      1 a1a-u2-c11-b2        (Priority)
     12026     small   yellow5 username PD 2017-02-21T09:11:28      1 a1a-u2-c11-b8        (Priority)
     12034    medium   potatoe username PD 2017-02-21T09:12:42      2 bc01bl[10,13]        (Resources)
     12035     small    turtle username PD 2017-02-21T09:12:47      1 a1a-u2-c13-b3        (Priority)

### Output Formatting

There are many output options available with squeue; to see them, run
**man squeue** and scroll down to *output_format*. From there, custom
outputs can be defined and viewed with the *-o <output_format>* option.
If you wish to see certain fields all the time when you run squeue, you
can follow the below instructions to set the SQUEUE_FORMAT environment
variable within your profiles to change your default output format of
the squeue command.

  - Example: ensure the default output has longer job names

:\*NOTE - default output format retrieved from man page

:\*Add the following line to your ~/.bashrc file

:: export SQUEUE_FORMAT="%.18i %.9P %.16j %.8u %.2t %.10M %.6D %R"

:\* In tcsh, add the following line to your ~/.cshrc file

  -

      -
        set SQUEUE_FORMAT="%.18i %.9P %.16j %.8u %.2t %.10M %.6D %R"

<!-- end list -->

  - When set, the SQUEUE_FORMAT environment variable will override the
    default format.
  - For both examples, we are using short form notation.
  - Format for each field is "%\[\[.\]size\]type"

:\* Adding a "." before the number will print the characters right
justified

  - Before adding to your .bashrc file, setting the variable can be done
    on command line to test

## sacct

### Default Output

You can check the status of a job with sacct:

    [username@headnode ~]$ sacct --jobs 1234
    JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
    ------------ ---------- ---------- ---------- ---------- ---------- --------
    1234         hello_wor_+      medium   researchgrp          1  COMPLETED      0:0
    1234.batch        batch                researchgrp          1  COMPLETED      0:0

The sacct command has a vast amount of information that can be
displayed. Adding the -l option gives more information, but adding the
-e option shows all available fields:

### Available Content

```
[username@headnode slurm_examples]$ sacct -e
AllocCPUS         AllocGRES         Account           AssocID
AveCPU            AveCPUFreq        AveDiskRead       AveDiskWrite
AvePages          AveRSS            AveVMSize         BlockID
Cluster           Comment           ConsumedEnergy    ConsumedEnergyRaw
CPUTime           CPUTimeRAW        DerivedExitCode   Elapsed
Eligible          End               ExitCode          GID
Group             JobID             JobIDRaw          JobName
Layout            MaxDiskRead       MaxDiskReadNode   MaxDiskReadTask
MaxDiskWrite      MaxDiskWriteNode  MaxDiskWriteTask  MaxPages
MaxPagesNode      MaxPagesTask      MaxRSS            MaxRSSNode
MaxRSSTask        MaxVMSize         MaxVMSizeNode     MaxVMSizeTask
MinCPU            MinCPUNode        MinCPUTask        NCPUS
NNodes            NodeList          NTasks            Priority
Partition         QOS               QOSRAW            ReqCPUFreq
ReqCPUS           ReqGRES           ReqMem            Reservation
ReservationId     Reserved          ResvCPU           ResvCPURAW
Start             State             Submit            Suspended
SystemCPU         Timelimit         TotalCPU          UID
User              UserCPU           WCKey             WCKeyID
```

### Output Formatting

To see any of the fields specified above in the command output, run
''sacct --jobs=<JOBID> --format FIELD1\[,FIELD2,etc\]

If you wish to see certain fields all the time when you run sacct, you
can follow the below instructions to set the SACCT_FORMAT environment
variable within your profile to change your output format of the sacct
command

  - In bash, add the following line to your ~/.bashrc file

<!-- end list -->

  -
    export SACCT_FORMAT="JobID,User,Account,Cluster,NodeList%-50"

<!-- end list -->

  - In tcsh, add the following line to your ~/.cshrc file

<!-- end list -->

  -
    set SACCT_FORMAT="JobID,User,Account,Cluster,NodeList%-50"

<!-- end list -->

  - When set, the SACCT_FORMAT environment variable will override the
    default format.
  - For both examples, you can set spacing of each field by placing
    "%\#\#" after the field name.

:\* Adding a "-" before the number will print the characters left
justified

## sinfo

### Default Output

You can check the status of nodes and partitions with sinfo:

    [username@headnode ~]$ sinfo
    PARTITION  AVAIL  TIMELIMIT  NODES  STATE NODELIST
    debug*        up    6:00:00      3    mix a1a-u2-c10-b[1-3]
    debug*        up    6:00:00      5  alloc a1a-u2-c10-b[4-7],a1a-u2-c11-b1
    debug*        up    6:00:00     24   idle a1a-u2-c10-b8,a1a-u2-c11-b[2-8],bc02bl[03,12],bc03bl[01-14]
    small         up 1-00:00:00      3    mix a1a-u2-c10-b[1-3]
    small         up 1-00:00:00      5  alloc a1a-u2-c10-b[4-7],a1a-u2-c11-b1
    small         up 1-00:00:00     24   idle a1a-u2-c10-b8,a1a-u2-c11-b[2-8],bc02bl[03,12],bc03bl[01-14]
    medium        up 7-00:00:00      3    mix a1a-u2-c10-b[1-3]
    medium        up 7-00:00:00      5  alloc a1a-u2-c10-b[4-7],a1a-u2-c11-b1
    medium        up 7-00:00:00     24   idle a1a-u2-c10-b8,a1a-u2-c11-b[2-8],bc02bl[03,12],bc03bl[01-14]
    large         up 365-00:00:      3    mix a1a-u2-c10-b[1-3]
    large         up 365-00:00:      5  alloc a1a-u2-c10-b[4-7],a1a-u2-c11-b1
    large         up 365-00:00:     22   idle a1a-u2-c10-b8,a1a-u2-c11-b[2-8],bc03bl[01-14]
    gpu           up 365-00:00:      1  down* gpu01
    gpu           up 365-00:00:      4   idle gpu[02-05]
    infiniband    up 365-00:00:      2   idle bc02bl[03,12]

### Available Content

The sinfo command has a vast amount of information that can be
displayed. Adding the -l option gives more information, -N groups by
node, and -p limits output to specific partitions. The commands manpage
shows all possible fields available for output, listed below:

```
             The field specifications available include:
              %all  Print all fields available for this data type with a vertical bar separating each field.
              %a    State/availability of a partition
              %A    Number  of  nodes by state in the format "allocated/idle".  Do not use this with a node state option ("%t"
                    or "%T") or the different node states will be placed on separate lines.
              %B    The max number of CPUs per node available to jobs in the partition.
              %c    Number of CPUs per node
              %C    Number of CPUs by state in the format "allocated/idle/other/total". Do not use  this  with  a  node  state
                    option ("%t" or "%T") or the different node states will be placed on separate lines.
              %d    Size of temporary disk space per node in megabytes
              %D    Number of nodes
              %E    The reason a node is unavailable (down, drained, or draining states).
              %f    Features associated with the nodes
              %F    Number  of  nodes  by state in the format "allocated/idle/other/total".  Do not use this with a node state
                    option ("%t" or "%T") or the different node states will be placed on separate lines.
              %g    Groups which may use the nodes
              %G    Generic resources (gres) associated with the nodes
              %h    Jobs may share nodes, "yes", "no", or "force"
              %H    Print the timestamp of the reason a node is unavailable.
              %l    Maximum time for any job in the format "days-hours:minutes:seconds"
              %L    Default time for any job in the format "days-hours:minutes:seconds"
              %m    Size of memory per node in megabytes
              %M    PreemptionMode
              %n    List of node hostnames
              %N    List of node names
              %o    List of node communication addresses
              %O    CPU load of a node
              %p    Partition scheduling priority
              %P    Partition name followed by "*" for the default partition, also see %R
              %r    Only user root may initiate jobs, "yes" or "no"
              %R    Partition name, also see %P
              %s    Maximum job size in nodes
              %S    Allowed allocating nodes
              %t    State of nodes, compact form
              %T    State of nodes, extended form
              %u    Print the user name of who set the reason a node is unavailable.
              %U    Print the user name and uid of who set the reason a node is unavailable.
              %v    Print the version of the running slurmd daemon.
              %w    Scheduling weight of the nodes
              %X    Number of sockets per node
              %Y    Number of cores per socket
              %Z    Number of threads per core
              %z    Extended processor information: number of sockets, cores, threads (S:C:T) per node
              %.<*> right justification of the field
              %<Number><*>
                    size of field
```

### Output Formatting

The output of sinfo can be customized based on user preference using two
different methods. One can be done on the command line using "-o
<output_format>" or "--format=<output_format>", where the desired fields
are specified at the users discretion.

If you wish for the custom sinfo output to be default for your login
session, follow the below instructions to set the SINFO_FORMAT
environment variable within your profile to change the output format:

  - In bash, add the following line to your ~/.bashrc file

<!-- end list -->

  -
    export SINFO_FORMAT='%N %.11T %.4c %.8z %.6m %.8d %.6w %.8f %20E'

<!-- end list -->

  - In tcsh, add the following line to your ~/.cshrc file

<!-- end list -->

  -
    set SINFO_FORMAT='%N %.11T %.4c %.8z %.6m %.8d %.6w %.8f %20E'

<!-- end list -->

  - When set, the SINFO_FORMAT environment variable will override the
    default format.
  - For both examples, you can set spacing of each field by placing
    "%\#\#" after the field name.

:\* Adding a "-" before the number will print the characters left
justified

[Category:SLURM](Category:SLURM "wikilink")
