There is a bit of an art to reporting bugs/errors in a way that helps
the support staff help you more effectively.\[1\]\[2\]

## Issue Tracking

**Please send all help requests to <deac-help@wfu.edu>**.

Requests sent to that address generate a "ticket" in our issue tracker:
this means all the support staff have access to the report, and we can
keep a running record of information pertaining to the issue. This also
means that your report won't be missed if the person you emailed
directly happens to be away.

## Key Requirements

An effective error report has two requirements:

1.  **Reproducible:** An error must be consistently reproducible. This
    means that the report must contain enough information for the
    support staff to reproduce the error: input files, specific versions
    of software, outputs (for comparison), etc. If the report involves
    [SLURM:Quick Start Guide](SLURM:Quick_Start_Guide "wikilink"),
    details about the job and the node(s) on which the job ran are
    important. Once a job is out of the queue, there may not be any
    remaining log information which can be used for debugging.
2.  **Specific:** An "error" is really a difference between expected
    output and actual output. The report should state exactly how the
    actual output/result differs from what was expected. For example,
    "Mathematica is not working" is not specific enough. What aspect of
    it is not working? Are you getting "2 + 2 = 7"?

*Neither edit (with the exception of passwords) nor interpret the
behavior you see. Verbatim logs of actions taken and output received are
absolutely necessary.*

## Specific Information for SLURM Job Issues

When having problems with SLURM jobs, there are some details that may
make the troubleshooting process easier if included when contact the HPC
team with issues.

1.  If possible, start the troubleshooting process by forwarding the job
    informational email received from SLURM when the error occurs or job
    ends.
      - If your job is not configured to send emails upon failure, or
        ending, see the [SLURM:Job Script
        Templates](SLURM:Job_Script_Templates "wikilink") page to set
        this up.
2.  In the body of the forwarded email, make attempts to include the
    following information, which will dramatically improve odds of
    diagnosing the problem.
    1.  Output of "`scontrol show job `<Job ID>" while having the
        problem.
          - This information is also inserted within the job output file
            during the prolog process.
    2.  Output of "`sinfo --long --Node -n `*`NODENAME`*" while having
        problem (if possible) if you think it should be running on that
        node.
    3.  Output of "`sacct --long --jobs=`*`YOURJOBNUM`*" if the job has
        completed.
3.  Attached to the email, please include a copy of your job script and
    error file if created.

In diagnosing SLURM issues, the more real time information related to
the job and the environment the better. Recreating that environment from
log files is not the best method to arrive at a solution.

It is understood that this is a lot of information to ask for, and it
will not be possible to include everything for every job. Your
assistance in making the best effort possible when starting the
troubleshooting process is appreciated\!

## Disk Space Issues

### Research Filesystems

When having issues concerning filesystem space on the DEAC cluster, it
is important to know some background about your shared space.

  - The /deac\* filesystems are individually assigned to research
    groups, and shared amongst the general group.
  - Each filesystem varies in size, and the only quota system enforced
    is on the general group.
  - We ask each user and group to be courteous of their usage, and to
    remove non-vital data generated as job output.

If filesystem issues occur, please include the following information
when initializing the troubleshooting process

1.  The full filesystem path attempting to be written to
2.  What you are attempting to write (file type, size, number of files)
3.  Time at which the error occurred

Additionally, when research filesystems fill up, the HPC team will seek
out highest consumers of space and the following options can occur:

  - Unimportant files will be deleted by the user
  - Many small files will be placed into a compressed tarball and only
    kept on the filesystem in this capacity.
  - Important files to keep will be archived, and then deleted from the
    filesystem.
  - Adviser groups will collectively clean up space through the
    aforementioned means.
  - Culprit jobs will be stopped (by admins or the user) and the scripts
    will have clean-up measures implemented.
  - As a last resort, if no response is given from high consumers within
    24 hours, jobs and/or data will be forcibly deleted.

### Home Directories

The /home filesystem is NOT to be used for reading/writing research
data. The aforementioned steps will be taken to clean up space if found
being used by a user.

### Inodes

Rarely, a filesystem may show as having space available, but the "no
space left on device" error message still occurs. This is caused by the
filesystem running out of metadata, or inodes. Inodes are
administratively configured and keep track of the files on the
filesystem. Just as standard filesystem space, they have a limit of how
much they can track (on the level of millions of files). Inodes may run
out when a series of jobs creates a millions of small files in order to
arrive at a result for a job. If best practices are not used and these
small files are not cleaned up, all users attempting to use that
filesystem are impacted; and most likely, the job series will not be
able to complete successfully.

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")
[Category:SLURM](Category:SLURM "wikilink")

1.  [How to Report Bugs
    Effectively](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html),
    Simon Tatham (author of PuTTY)
2.  [How to Write a Useful Bug
    Report](https://community.helixcommunity.org/2006/writingbugreport),
    Helix developer community---
title: Quick Start Guide:Error Reporting
permalink: /Quick_Start_Guide:Error_Reporting/
---

