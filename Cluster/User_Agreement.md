## Terminology and Conventions

While most users think in terms of jobs submitted, limitations of job
submissions primarily relate to the amount of computing resources
consumed; specifically the number of nodes/processors and amount of
memory in the DEAC cluster. It is the availability of those resources on
a reasonable time table that this User Agreement is primarily concerned
with.

Fairshare is a term that essentially apportions a target average cluster
utilization for the various user groups of the cluster. However,
fairshare is only a consideration that is enforced when the cluster is
***overutilized***. Under normal circumstances, there is far more work
to be done than cluster resources available, resulting in a many jobs in
the queue waiting to run. Fairsharing is a configuration parameter that
helps determine which of those queued jobs to run next when a cluster
resource becomes available. In an *underutilized* cluster environment,
jobs run as the resources are available (which, in most cases, is
immediately).

**Use it if you need it\!** The cluster exists to be used; however,
there are two situations where common courtesy may be required:

  - If no one else is using it and you need it, you should be using it\!
    However, in order to ensure a productive environment for all users,
    please follow the restrictions below as they mostly apply to our
    typical, non-overutilized cluster environment.
  - If everyone else is using it, submit your jobs anyway\! The cluster
    software will make sure you get your [Fairshare
    value](Cluster:Fair_Share_Policy "wikilink").

## Job Submission

  - Jobs should be submitted to the appropriate partition based upon
    their length or resource consumption. Repeat requests to extend
    TimeLimit will not be honored beyond the first instance for a batch
    of jobs.
      - No exceptions.
  - No group should exceed their group's fair share usage by more than
    25% for longer that 24 hours at a time.
      - Exception: During periods of extremely low cluster utilization
        (e.g. 10-25%), a single user may exceed this limit but the jobs
        over this 25% threshold should not exceed 96 hours of running.
        In addition, jobs ***MUST*** be submitted in a staggered fashion
        so that a quarter of the jobs exceeding the threshold complete
        every 24 hours.
      - Example: Your fairshare is 8. A single person can run on 10
        nodes without restriction under this item. However, to run on 14
        nodes for more than 24 hours, the user must stagger submission
        of those jobs on all 14 nodes so that 1 node is freed by job
        completion every 24 hours.
  - No single user should consume 75% of the available computational
    resources of the cluster for any period of time.
      - No Exceptions.
  - Excessive usage of the cluster (primarily large numbers of jobs, in
    this instance) requires staggered submission of jobs so that the
    scheduling routines can work in jobs from other user within a
    reasonable amount of time.
      - Exception: Users do not have to stagger submission if the number
        of jobs submitted is less than the total number of processors on
        the cluster and jobs are currently queued.
  - Jobs should not read/write research data to the /home filesystem.
      - No Exceptions. Users should use local /scratch space, or
        research directories.

## Head Node Usage

  - Users are not allowed to run production jobs on the cluster head
    nodes.
      - Exception: certain visualization and interactive programs can be
        run on the head nodes but not to exceed one instance of this
        program class per head node.
  - Users are allowed to run test jobs on the cluster head nodes IF:

:\#They consume less than 5 processors total, AND

:\#They consume less than 50GB of memory, AND

:\#They run for less than two hours.

::\*Exception: If test jobs need to run beyond these limits limit to
ensure functionality, then the HPC team should be contacted. A singular
instance may be allowed to run on one head node if the processes
"[priority is lowered](http://linux.die.net/man/1/nice) on the head node
to reduce impact to cluster users.

## Global Exceptions

While these limits and restrictions may appear like hard and fast rules
(simply because they are written down), these limits are flexible
***PROVIDED*** that advanced warning and collaboration with the HPC team
and fellow users is employed. We are a friendly bunch and are willing
(and have in the past) to work with each other to ensure everyone has
access to the cluster (and as much as they need) for their research
efforts.

Significant and urgent need for significant percentages of cluster
resources can be granted pending approval of the cluster community.
Simply petition the osiris-users list and make sure someone else doesn't
have similar urgent needs. You can submit some of your jobs while
waiting for everyone to chime in ***BUT*** you have to make sure
everyone speaks up before proceeding with all of your jobs.

[Category:Policy](Category:Policy "wikilink") [Category:New User
Information](Category:New_User_Information "wikilink")---
title: Cluster:User Agreement
permalink: /Cluster:User_Agreement/
---

