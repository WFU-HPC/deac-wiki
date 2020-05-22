# Overview

Typically, when it comes to using a cluster, there are generally only a
few things that introductory users must learn about working in the
environment:

1.  Clusters are hard. You are dealing with the most powerful forms of
    computing on the planet. It takes between 15-20 years to make a
    supercomputer easy\[1\]
2.  It is not "point-and-click", review the \[\[Quick Start
    Guide:Linux\] to learn about how to use the following required
    things:
    1.  Command line
    2.  Text editors
    3.  Custom programming and scripting. Many of these issues are
        addressed in the
3.  Users have to know where [\#Where To Put
    Data](#Where_To_Put_Data "wikilink") on the cluster.
4.  Users have to understand [\#Leverage the Software
    Environment](#Leverage_the_Software_Environment "wikilink") and use
    it in their jobs

# Assumptions

1.  You've never used the cluster before and have an empty home
    directory.
2.  Your username is **myacct** (the same as your WFU account).
3.  You are assigned to a research group, called **advisorGrp**.
4.  You are assigned a *fairshare* group, called **fairshareGrp** (often
    the same name as **advisorGrp**).
5.  You have a research directory for your data, called
    **/deac/advisorGrp**.
6.  You have logged into a cluster head node by following the
    instructions in [Cluster:Access and
    Layout](Cluster:Access_and_Layout "wikilink")

# Where To Put Data

First and foremost, you have to know where to put your files on the
cluster.

>   - /home/myacct
>     This is your *home directory*. When your account is created, it
>     will only have some default environment configuration files that
>     are hidden.
>
> <!-- end list -->
>
>   - Your home directory is configured to store only a limited amount
>     of data crucial to your ***interactive*** use of the cluster,
>     primarily through the head nodes. For general uses, your research
>     software (source codes, binaries) can be stored there.
>       - Users should NOT store files that define jobs, or are created
>         by your jobs in their *home directory*.
>       - Users should NOT use their *home directory* as a job's WORKDIR
>         or OUTPUT path when submitting jobs to the cluster
>           - Doing so can cause sluggish behavior for users and jobs
>             running on the cluster
>           - Every single login session and job running need basic
>             access to this path, adding additional load degrades the
>             aforementioned ***interactive*** use of the cluster by
>             delaying system response.
>
> <!-- end list -->
>
>   - /deac/advisorGrp
>     This is the *research directory* for research groups, and is owned
>     by faculty advisors. Advisors are the ultimate owner of research
>     data after users leave the group (by graduation, transfer to
>     another group, or leaving the University for another position).
>
> <!-- end list -->
>
>   - These research directories are set up to handle the load of
>     multiple jobs from multiple compute nodes writing multiple files.
>     Any files referenced or created by your computational jobs should
>     go here.
>   - Depending on the research group, this directory will host shared
>     research software, common libraries, and research results.
>
> <!-- end list -->
>
>   - /deac/advisorGrp/username
>     Depending on the research group, individual user research
>     directories may exist to store individual user results that may or
>     not be shared among the group.

Second, within either directory, sub-directories need to be structured
in a logical way so that research data and conducted results are easy to
navigate. For example, break things down by project, job type, or even
individual jobs. Much of the guidance for this structure will come from
your research group colleagues and advisor; however, if you are breaking
new ground for the group, feel free to contact the HPC Team for
guidance.

# Leverage the Software Environment

The WFU DEAC Cluster has software provided by Red Hat (through the base
OS distribution), the Fedora Project (through the EPEL project), and by
WFU (through licensing or user request of generally available software).
To successfully use the cluster, users must:

1.  Know what software is available
2.  Know how to use it

Use the wiki to search for specific names of desired software, or read
general software articles such as
[Software:Overview](Software:Overview "wikilink"). The HPC Team relies
upon users taking the initiative to read generally available software
documentation online to conduct basic troubleshooting and learn how to
use programs specific to their research.

To help configure user environments for the different compilers we
support, [environment-modules](http://modules.sourceforge.net/) are
used. Be sure to read [Quick Start Guide:Environment
Modules](Quick_Start_Guide:Environment_Modules "wikilink") in order to
understand the tool and how to use it.

To see how to utilize software for submitted jobs, next see the
[SLURM:Quick Start Guide](SLURM:Quick_Start_Guide "wikilink").

# References

<references/>

[Category:Cluster](Category:Cluster "wikilink") [Category:New User
Information](Category:New_User_Information "wikilink")

1.  <http://www.tgdaily.com/mobility-brief/55861-apples-ipad-2-is-as-fast-as-a-supercomputer-from-1985>
