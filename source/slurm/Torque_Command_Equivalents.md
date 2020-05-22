# Slurm to Torque/Maui Equivalents

  - Summary of equivalent commands can be found
    [here](http://slurm.schedmd.com/rosetta.pdf)
  - A good transition reference guide can be found
    [here](https://wiki.csiro.au/display/ASC/Reference+Guide%3A+Migrating+from+Torque+to+SLURM)

## User Commands

  - SLURM commands have many different parameters and options.
  - Any favorite custom options should be added to the [SLURM
    commands](SLURM_commands "wikilink") wiki page.

<table>
<thead>
<tr class="header">
<th><p>Command</p></th>
<th><p>Slurm</p></th>
<th><p>Torque/Maui</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cluster Status</p></td>
<td><p><a href="http://slurm.schedmd.com/sinfo.html#OPT_node">sinfo</a> [-Nel]</p></td>
<td><p>viewnodes OR qstat -a</p></td>
</tr>
<tr class="even">
<td><p>Queue List</p></td>
<td><p><a href="http://slurm.schedmd.com/squeue.html">squeue</a> [-u <username>]</p></td>
<td><p>showq OR qstat -Q</p></td>
</tr>
<tr class="odd">
<td><p>Job Submission</p></td>
<td><p><a href="http://slurm.schedmd.com/sbatch.html">sbatch</a></p></td>
<td><p>qsub</p></td>
</tr>
<tr class="even">
<td><p>Job deletion</p></td>
<td><p><a href="http://slurm.schedmd.com/scancel.html">scancel</a> <job_id></p></td>
<td><p>qdel <job_id></p></td>
</tr>
<tr class="odd">
<td><p>Job status</p></td>
<td><p><a href="http://slurm.schedmd.com/squeue.html">squeue</a> <job_id></p></td>
<td><p>qstat <job_id></p></td>
</tr>
<tr class="even">
<td><p>Job information</p></td>
<td><p><a href="http://slurm.schedmd.com/scontrol.html#OPT_show">scontrol</a> show job <job_id><br />
</p></td>
<td><p>qstat -f <job_id><br />
</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p><a href="http://slurm.schedmd.com/sstat.html#OPT_jobs">sstat</a> -j <job_id>.batch</p></td>
<td><p>checkjob <job_id><br />
</p></td>
</tr>
<tr class="even">
<td><p>Job Completion Info</p></td>
<td><p><a href="http://slurm.schedmd.com/sacct.html#OPT_jobs">sacct</a> -j <job_id> -l</p></td>
<td><p>tracejob</p></td>
</tr>
<tr class="odd">
<td><p>Node List</p></td>
<td><p><a href="http://slurm.schedmd.com/sinfo.html#OPT_node">sinfo</a> -N</p></td>
<td><p>pbsnodes -l</p></td>
</tr>
<tr class="even">
<td><p>Show Reservation</p></td>
<td><p><a href="http://slurm.schedmd.com/scontrol.html#OPT_show">scontrol</a> show reservation=<resname></p></td>
<td><p>showres <resename></p></td>
</tr>
<tr class="odd">
<td><p>Fairshare Info</p></td>
<td><p><a href="http://slurm.schedmd.com/sshare.html#OPT_accounts=">sshare</a> [-A <account>] [-u <user>]</p></td>
<td><p>diagnose -f</p></td>
</tr>
<tr class="even">
<td><p>Job Queue Priority</p></td>
<td><p><a href="http://slurm.schedmd.com/sprio.html">sprio</a></p></td>
<td><p>diagnose -p</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Batch / Script Parameters

  - Review the [SLURM conversion
    script](SLURM:Torque_Conversion_Script "wikilink") wiki page to see
    how to use the DEAC cluster's custom conversion script and convert
    your old Torque batch scripts to
SLURM.

| Environment        | Slurm                                            | Torque/Maui                                     |
| ------------------ | ------------------------------------------------ | ----------------------------------------------- |
| Directive          | \#[SBATCH](http://slurm.schedmd.com/sbatch.html) | \#PBS                                           |
| Queue              | \--partition=<queue>                             | \-q <queue>                                     |
| Name               | \--job-name=<name>                               | \-N <name>                                      |
| CPU/Node Resources | \--nodes=1                                       |                                                 |
|                    | \--tasks-per-node=8                              | \-l nodes=1:ppn=8:ethernet                      |
|                    | \--constraint=”ethernet”                         |                                                 |
| Memory Size        | \--mem=2048                                      | \-l mem=2048mb                                  |
| Memory Per CPU     | \--mem-per-cpu=2048                              | \-l pmem=2048mb                                 |
| Time               | \--time=\[days-\]hh:mm:ss                        | \-l walltime=\[dd:\]hh:mm:ss                    |
|                    |                                                  | \-l cput=48:00:00                               |
| Error Output File  | \--error=%j.job_id_error                       | \-j oe                                          |
|                    | \--output=%n.node_name_output                  |                                                 |
| Charge Account     | \--account=<account>                             | \-W group_list=<group>                         |
| Email Address      | \--mail-user=carlsoas@wfu.edu                    | \-M carlsoas@wfu.edu                            |
| Run Variables      | \--export=“var1=X\[,var2=Y\]“                    | \-v var1=X,var2=Y                               |
| Specify Feature    | \--constraint=“\[clan03|clan04\]“                | \-W x=\\”NODESET=ONEOF:FEATURE:clan03:clan04\\” |

[Category:SLURM](Category:SLURM "wikilink")
