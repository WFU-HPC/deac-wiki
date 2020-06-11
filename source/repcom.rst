========================
WFU DEAC RepCom Meetings
========================

.. toctree::

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2008/11/03
----------

Agenda
======

* David Chin, new systems analyst from Michigan, LIGO, and Brigham's Woman's
  hospital, computational radiation physics, as postdoc.

Changes to Cluster User Policy
==============================

* Tim's showed changes. minor changes made to Representative Committee ("will
  provide a single representative" to "may provide representation")
* added text to make it clear that only WFUHS people are bound by WFUBMC
  policies, and that everyone is bound by WFU CIT policies.

Changes to Cluster Account policy
=================================

* Brought in WFUHS accounts. Made minor corrections. Added Non-disclosure
  requirements.
    
    * everyone has to sign a non-disclosure requirements to disclose any
      confidential information in the event of accidential disclosure.
    * Can be done electronically.
    * If not signed then accounts are disabled.
    * Request to add more reminders to the account termination process; more
      than just 1 reminder.
    * Nodes purchase
    * Plan is 1024 cores with 2GB total.
    * Shutdown of cluster
    * Friday of Dec 5th noon. Intederminate time-length to bring back cluster.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2010/04/05
----------

Attendance
==========

* Rick Matthews
* Lynn Berry
* Tim Miller
* Stacy Howerton
* Bill Kerr
* Natalie Holzwarth
* Greg Cook
* Akbar Salam

Agenda
======

* 32-bit node update
* Storage Remediation Efforts
* Annual Purchase Status

    * Ready to install the hardware after several physical location restrictions
      have been listed.

* Grant Funding Agency Requirements

    * Any security requirements?
    * Any data retention requirements?

* Support Wiki Status

Minutes
=======

Attendees: Natalie Holzwarth, Stacy Howerton, Bill Kerr, Greg Cook, Akbar Salam,
Rick Matthews, Dave Chin, Tim Miller, Lynn Berry

1.  32 bit node retirement update: Two 32 bit head nodes and 7 compute nodes are
    still running. They will remain up until all code can be converted to 64
    bit. The two head nodes will be virtualized.
2.  Storage Remediation: All performance issues appear to be resolved. Tim
    Miller moved the metadata and data to separate drives. The data resides on 6
    dedicated drives and the metadata has 3 dedicated drives. GPFS0 is complete.
    RC1 and RC2 will need to be moved.
3.  Annual Purchase: Hardware has arrived. Power is complete. We're targeting
    April 13/14 for installation. The list of attributes for the new nodes will
    be added to the wiki.
4.  Security: Grant funding agencies are adding requirements for data retention
    and security. Please send an email to Tim Miller, if you encounter these
    requirements.
5.  Support Wiki: Dave Chin demonstrated the new wiki. The link for the wiki is
    `wiki.deac.wfu.edu`_. Please send updates or suggestions to
    `deac-help@wfu.edu`_. Also, feel free to update the pages.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

.. _`RepCom meeting`:

----------
2010/09/07
----------

Attendance
==========

Agenda
======

* Review Old Business

    * Virtualization Environment
    * Storage Remediation Status
    * Review 32-bit Node Status

* Operational Changes to Rep Com Meetings

    * Meeting frequency
    * Meeting content
    * Usage of Email instead of meetings? (fixed response time)

* State of the Cluster

Minutes
=======

Old Business
------------

* Virtualization Environment

    * 6 VMware ESXi servers deployed for an approximate "high availability" VM
      environment.

* Storage Remediation Status

    * Progress on reducing/removing ``/gpfs0`` stalled
    * Still storage left to allocate from Spring purchase
    * 15TB of storage is coming from WFUHS

* Review 32-bit Node Status

    * Are these still in use?
    * Can we finish the decommissioning?

New Business
------------

RepCom Operational Changes
```````````````````````````

* Meeting frequency
* Meeting content
* Usage of Email (fixed response time)
* How much integration with IS functional groups is desired?

    * Might need to ask faculty for assistance in filling out IS internal
      business case documents for the initial service requests.

State of the Cluster
````````````````````

* Cluster Usage Reporting

.. image:: images/Cluster_Memory_Usage_2009-01_to_2010-08.png
.. image:: images/Cluster_Processor_Usage_2009-01_to_2010-08.png

* Review 64-bit Hardware Status

    * 50% of storage nodes are out of warranty next month
    * 100% of head nodes are out of warranty next month
    * 2 clans of dual core nodes are out of warranty
    * 1.5 clans of quad core nodes are out of warranty

* Maintenance tasks/Downtime (nothing pressing yet)

    * Core network switch code update (compute node downtime required)
    * Storage updates (filesystem downtime required, whole cluster preferred)

FY11 Hardware Purchases
```````````````````````

* Cost to upgrade HS21XM with 16GB to 48GB is $6100/blade
* Cost of new HS22 with 48GB is $5800/blade
* Known Computational Needs

    * GPU computing Infrastructure (head node with some GPUs)
    * Test Bed Network Simulation Infrastructure (new chassis needed)

* Known Infrastructure Needs

    * Replacement storage blades
    * Additional storage blades (new WFUHS storage)
    * Second infrastructure chassis ??
    * Globus Grid/SURAgrid infrastructure
    * May need some SAN switch replacement funding
    * 10Gbps connectivity to research networks

Action Items
------------

* Digital Measures - API available to extract publications related to the
  cluster. Expand their functionality on the site to select a "cluster" check
  box.
* Send email to cluster users reminding to correct legacy scripts to remove
  ``gpfs0`` and replace with ``wfurc*``
* Send email to users requesting resource needs as a final chance to provide
  input to purchase needs.
* List of what's getting removed, what's getting added
* Present whole pictures not just deltas

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2010/11/01
----------

Attendance
==========

* Tim will attempt to hold this discussion over email. Should the committee
  request an in-person meeting, these "minutes" will be

Agenda
======

* FY11 Cluster Hardware Purchase

* Presentation of Current State
* Presentation of Changes
* Presentation of New State

Virtual Discussion
==================

Cluster Hardware Purchase
-------------------------

Short, short version
````````````````````

Replace 28 Compute Nodes
    Remove/retire 8GB blades that have 4 total processing cores and replace with
    48GB blades having 8 total processing cores.

Refresh Storage Hardware Device "FASTT1"
    Use WFUHS Enterprise Storage to retire "end of life" storage device.

Increase maintainability of storage subsystem
    Purchase IBM v7000 storage device with 24TB of RAW storage

Refresh Storage Server Blades
    Replace 8 aging storage blades with 10 new, smaller form factor storage blades

Summary
```````

    * As we discussed at previous Rep Comm meetings, we need to increase the
      "per processor" memory on each blade and the most cost effective means of
      doing that is replacing the older "dual core" technology blades with the
      latest "quad core" based blades.
    * We also have some hardware devices that are approaching the point where
      they need replacement (such as the storage blades and one storage device).
      We will leverage some of the free storage from the hospital to assist in
      this replacement effort.
    * However, we'll still need some additional storage for projected increases
      in usage.
    * We've also encountered support issues with two of our newer storage
      devices. There are in essence very few controls or commands that can be
      used to resolve any performance or control issues the devices may be
      having, leaving us no other option than having to power cycle the storage
      device. After discussing the product space with IBM, I've identified a
      potential device (v7000) that could address these issues and at a price
      point that is not significantly higher than our previous storage devices.

Current Cluster State
`````````````````````
See `Cluster:Hardware Configuration`_ for specifics...

* Compute Nodes

    * We currently have 39 blades with 4 total processing cores (i.e. dual core,
      dual processor/socket blades)
    
        * Each of these blades has 8GB of physical RAM
    
    * We currently have 103 blades with 8 total processing cores (i.e. quad
      core, dual processor/socket blades)
    
        * 66 of these blades have 16GB of physical RAM
        * 7 of these blades have 32GB of physical RAM
        * 30 of these blades have 48GB of physical RAM

* Storage

    * 41.9TB of storage online as a GPFS filesystems
    * 675GB of storage held in reserve for ``/home``
    * 5.4TB of storage not in use from Spr 2010 purchase.
    * 15TB "in transit" from the WFUHS Enterprise Storage service.

* Storage Nodes
    
    * 16 Storage Nodes
        
        * Two of these nodes are WFUHS purchased nodes for their storage.

Final Cluster State
```````````````````

* Compute Nodes

    * We currently have 11 blades with 4 total processing cores (i.e. dual core,
      dual processor/socket blades)
    
        * Each of these blades has 8GB of physical RAM
    
    * We currently have 131 blades with 8 total processing cores (i.e. quad
      core, dual processor/socket blades)
    
        * 66 of these blades have 16GB of physical RAM
        * 7 of these blades have 32GB of physical RAM
        * 58 of these blades have 48GB of physical RAM
  
* Storage
  
    * 41.9TB of storage online as a GPFS filesystems
    * 675GB of storage held in reserve for ``/home``
    * 5.4TB of storage not in use from Spr 2010 purchase.
    * 15TB "in transit" from the WFUHS Enterprise Storage service.
    * 18TB (usuable) new storage from Winter 2010 purchase.

* Storage Nodes

    * 18 Storage Nodes

        * 2 nodes dedicated for WFUHS research groups
        * 2 nodes dedicated to WFURC for WFUHS storage

Minutes
=======

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2011/04/04
----------

Attendance
==========

* Tim Miller (chair)
* Greg Cook
* Bill Kerr
* Natalie Holzwarth
* Sam Cho
* Stacy Howerton

Agenda
======

* CY2011 Shutdown
* 10Gbps Network Upgrade
* RHEL 6 Upgrade
* New HPC Team Management

Discussion
==========

CY2011 Shutdown
---------------

* Definitely need one

    * 10Gbps Network Changes (required downtime)
    * Storage Device Code Upgrades (required downtime)
    * Network Switch Code Upgrades (required downtime for one switch, optional for two others)
    * GPFS Filesystem Software Upgrades (downtime makes it convenient)

* Proposed date: Aug 29 - Sep 2

10 Gbps Network Upgrade
-----------------------

    * Reviewed what we are planning on doing.
    * Awaiting NC-REN detailed quote.
    * Required WFU hardware purchased and received.
    * 95% chance this will happen.
    * There are connectivity and service availability implications.

RHEL 6 Upgrade
--------------

* We are starting the infrastructure work to support RHEL6 cluster node imaging.
* Goal is to have a development environment by June 1 (very optimistic)
* RHEL4 Support Ends January 2012\!
* Core WFU DEAC Software for RHEL6

    * GNU Compilers
    * Portland Compilers
    * Intel Compilers
    * Absoft Compilers
    * GPFS Filesystem
    * OpenMPI/MPICH/MVAPICH (builds, variants, etc. to be determined at project time)
    * Matlab, Maple, Mathematica, ITT IDL
    * BLAS, LAPACK, ATLAS,
    * FFTW 2.x, 3.x
    * (wish list) PETSC

* Software for RHEL6:

    * What software should be centrally supported?
    * What should not?
    * What does "supported" mean?
    * Do we want "SLAs" (or something written somewhere) about the answers to these questions?

* Software licensing, support, and costs we need to be worried about (question for users)?

    * Gaussian?
    * CHARMM
    * LS-DYNA (costs covered by WFUBMC)

* TTD for Tim

    * email users regarding the difficult software licenses/costs
    * Proposal from Greg
 
        * First group does compilation with single compiler
        * Provide explicit instructions on how to build it, how to validate the results
        * We provide secondary compiler support
        * Could send out an email requesting whether someone has started using it

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2011/08/08
----------

Attendance
==========

* Tim Miller (chair)

Agenda
======

* Introductions
* Annual Cluster Purchase
* Updates from the Summer

    * CY2011 Shutdown
    * 10Gbps Network Upgrade
    * RHEL 6 Upgrade

Discussion
==========

Annual Cluster Purchase
-----------------------

* Given projected work for fall, deferring annual purchase to the spring.
* Some grant money needs to be spent now (in next couple weeks).

    * Natalie Holzwarth
    * Jacque Fetrow
    * Joel Stitzel (WFU BME)
    * Others?

* What to purchase?

    * Stitzel group will be looking for more Infiniband resources
    * Do we need 96GB nodes?
    * If no specialized needs, will continue hardware refresh plan (replace
      another 14 nodes of 16GB nodes with 48GB nodes)

CY2011 Shutdown
---------------

* Change from April meeting: Date changed to Sep 6-9 (from 8/29-9/2)

    * Lots of hardware firmware updates

        * Storage Device Code Upgrades
        * Network Switch Code Upgrades
        * GPFS Filesystem Software Upgrades (at risk, due to compressed
          timeline)

10 Gbps Network Upgrade
-----------------------

* 100% chance it will happen
* Timeline contingent:

    * University's 10Gbps Internet link upgrades
    * Fiber optic cable route validation

* Ideal to happen during downtime. This is still the goal.
* It is possible to handle the upgrade "live" but connectivity from the cluster
  to campus/internet will have some minor interruptions.

RHEL 6 Upgrade
--------------

* We have made almost zero progress toward a RHEL6 development environment.
* RHEL4 Support Ends January 2012!
* User community will have very limited testing time on RHEL6 environment before
  having to make cutover.
* Software licensing, support, and costs we need to be worried about (question
  for users)?

    * Gaussian - desired version?
    * CHARMM - update from Fred: licensed to a particular research group, not by
      site. Probably not a good candidate for central funding.
    * LS-DYNA (costs covered by WFUBMC)
    * Matlab - Any expected growth in cluster usage? We have licensed DCS now.
      Need to install.
    
        * Tim might submit a capital request for this.

    * Mathematica - now at 30 licenses (still need to load license)

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2011/12/15
----------

Attendance
==========

Agenda
======

* RHEL6 Upgrade Status
* User Survey (in preparation)
* FY12 purchase in Winter/Spring
* Narrow choice of meeting dates

Discussion
==========

RHEL 6 Upgrade Status
---------------------

* Research into infrastructure components has begun.
* We will finalize the framework and scope of work in the next two weeks and
  start building out the system image.

User Survey
-----------

* Sent a cluster user "satisfaction" survey to all users on Friday.

    * Goals: Get a quick pulse reading on our efforts. Produce a second survey
      to drill deeper if needed.

* Sent a research group "resource" survey to all users on Friday.
    
    * Goals: Quick gauge on some services we don't offer but other HPC groups
      do. Use the questions to start the creative juices. Facilitate a
      discussion.

FY12 purchase in Winter/Spring
------------------------------

* What to buy?
* Discussion centered around:

    * Current hardware status:
        
        * Estimated 30-40% of the compute nodes are out of warranty (which is
          okay so long as that percentage stays stable)
        * Infiniband hardware in BC01 and BC02 (24-port switch) will no longer
          have hardware support as of Fall 2012
        * We need to retire the 2 DS3000 and 2 DS4000 storage devices to recover
          a significant cost in annual maintenance (frees up for compute node
          purchases)
        * We have one last clan of dual core blades that must be replaced (4
          cores and 8GB on each blade)

    * Tentative needs

        * More storage - Need two more V7000 expansion shelves to replace DS3000
          and DS4000 devices
        * Infiniband refresh - Need minimum of two chassis of new 40Gbps IB
          gear, ideally three.
        * Compute refresh - Need at least one more clan of compute nodes: dual
          socket quad-core (total 8 cores), 96GB blades.

    * Potential needs
        * Infiniband switch to connect the chassis?
        * Third V7000 expansion shelf to add ~18TB of \*new\* storage to the
          cluster


* Memory and processor usage plots were not ready in time for the meeting. Once
  finished and understood, they will be emailed to the committee.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2012/01/17
----------

Attendance
==========

Agenda
======

* User Survey Results
* Cluster Usage Data
* FY12 purchase in Winter/Spring
* ISILON Storage Proof of Concept
* RHEL6 Upgrade Status

Discussion
==========

User Survey Results
-------------------

(*Results are cut-n-pasted as is. For "satisfaction" questions, the percentage
is based on total number of responses. Raw answer count is listed after each
percentage.*)

Please specify the three most significant aspects of the WFU DEAC Cluster that are the most crucial to your regular use of the cluster.
```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````

* First Most Significant

    1. Available programming languages
    2. space on disk
    3. Fortran 77
    4. Reasonable waiting time in the queue
    5. Inifiniband available
    6. Speed
    7. infiniband (for md simulations)
    8. large number of cores for use in parallel computation
    9. Centralized data storage
    10. Availability of compute nodes to run jobs
    11. Large number of available nodes for running jobs
    12. It is very well maintained and I don't have to worry about anything.

* Second Most Significant

    1. Fair sharing of processor time
    2. memory
    3. Head nodes to do editing and run short programs
    4. Reasonable speed for computer jobs
    5. generally short queue times
    6. Availability
    7. access/cost
    8. infiniband
    9. Large number of CPUs to handle variable demands
    10. Having updated compilers and standard libraries
    11. The cluster is of good size and I can get all my research done.

* Third Most Significant

    1. Significant storage space
    2. up to date libraries
    3. Mathematica
    4. Ease of Use
    5. good availability
    6. Central administration
    7. Having help with computing issues; for example help with compiling code and linking to appropriate libraries.

Please specify the three most significant aspects that are missing in your regular use of the cluster
`````````````````````````````````````````````````````````````````````````````````````````````````````

* First Most Significant

    1. None, I just have cyclical projects
    2. python not up to date
    3. None
    4. Queue status sometime doesn't reflect the real job status. Once, status showed the job was running, and the job was actually hanging there.
    5. limited availability of some resources during peak usage times
    6. SAS program capability (though I know it's coming)
    7. infiniband nodes fill up with jobs not running infiniband
    8. more infiniband nodes
    9. Massive storage space
    10. An easy way to know if the cluster resources for any given job are being used efficiently.
    11. Disk space
    12. The wiki is great, but still need some improvement. I really dislike the fact that you need your password to log in---lots of users use key pairs to log in and don't remember their password (like me).

* Second Most Significant

    1. space on disk for DASP updates
    2. more infiniband nodes for a single job
    3. Support for the latest software
    4. Occasionally it has been hard to get a job through the queue, although it is relatively rare.

* Third Most Significant

    1. more cores per node
    2. It is sometimes hard to compile code and link to installed libraries. While we appreciate Dave's excellent help, perhaps it might be possible to make it easier for us?

Are you satisfied with the overall cluster service you are receiving (hardware resources, resource availability, user support, etc)?
````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````

* Somewhat satisfied 33.3% (4)
* Completely satisfied 66.7% (8)

Are you satisfied with the types of clusters resources made available (Gigabit Ethernet, Infiniband, Types of Storage, Types of Processors, Memory, Intel x86_64 processors, etc)?
``````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````

* Somewhat Dissatisfied 8.3% (1)
* Somewhat Satisfied 25.0% (3)
* Completely Satisfied 58.3% (7)
* No Opinion 8.3% (1)

Are you satisfied with the amount of resources available?
`````````````````````````````````````````````````````````
  
* Somewhat Dissatisfied 8.3% (1)
* Somewhat Satisfied 41.7% (5)
* Completely Satisfied 50.0% (6)

Are you satisfied with the user support you receive?
````````````````````````````````````````````````````

* Completely Dissatisfied 8.3% 1
* Somewhat Satisfied 8.3% 1
* Completely Satisfied 83.3% 10

Do you receive timely responses to your support requests?
`````````````````````````````````````````````````````````

* Completely Dissatisfied 8.3% (1)
* Somewhat Satisfied 8.3% (1)
* Completely Satisfied 83.3% (10)

Are the resources provided by the HPC team meeting your research needs?
```````````````````````````````````````````````````````````````````````

* Completely Dissatisfied 8.3% (1)
* Somewhat Satisfied 50.0% (6)
* Completely Satisfied 41.7% (5)

Cluster Usage Data
------------------

Summary
```````

* Average Infiniband Job Wait Time = 2 hr
    
    .. image:: images/2011-12-10_Infiniband_Job_Wait_Times.png

* Average Ethernet Job Wait Time = 20 mins
    
    .. image:: images/2011-12-10_Ethernet_Job_Wait_Times.png

* **Maybe** some better processor utilization after 48GB nodes were added
  (BC07/BC08)
    
    .. image:: images/2011-12-10_Processor_Utilization_Historical_30mBins.png

* **Maybe** some increase in memory utilization too
    
    .. image:: images/2011-12-10_Memory_Utilization_Historical_30mBins.png


Time Ranges
```````````

* entire survey range: 02 Aug 2010 -- 02 Dec 2011
* start of survey to before BC13 was installed (10 Nov 2010)
* between BC13 installation and BC07 installation (01 Mar 2011)
* between BC07 installation and BC14 installation (01 Nov 2011)
* after BC14 installation

FY12 purchase in Winter/Spring
------------------------------

Drivers in the Decision
```````````````````````

    * Suggestions drawn from the survey (for the purchase)
    
        1.  Disk Space
        2.  Infiniband
    
    * Hardware Support
    
        1.  24-port Infiniband switch (end of support = 12/31/2012)
        2.  8 of 14 clans are out of support
    
    * Cluster usage
    
        1.  Infiniband is somewhat of a resource constraint.
        2.  Anecdotal indications are that it will continue to be so.
        3.  Software development is producing more IB capable programs.
    
    * Cost estimates
    
        1.  Disk Space (24TB raw = $28k, ~18TB usable)
        2.  Infiniband (~$18k for each chassis)
        3.  One clan of 96GB Nodes (~$60000)

* Tim's Recommendation

    1.  **Storage** (3 Shelves)
    2.  **Infiniband** (3 Chassis - replacement for 2 chassis, add one new chassis)
    3.  **Clan03** (14 blades)
    4.  Clan05

* Infiniband

    1.  Re-use 24-port switch to interconnect chassis' to determine need for multi-chassis' IB

Future Hardware Issues
----------------------

* Storage Node Remediation

ISILON Proof of Concept
-----------------------

* WFBH testing ISILON NAS device
* Dual connected between WFBH and WFU
* Performance testing now
* Workflow testing in the next week or so
* May opt for much of WFBH provided storage to get migrated to new device

RHEL 6 Upgrade Status
---------------------

* Work on the configuration server underway.
* Pressure is on to get a test environment by February.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2014/05/14
----------

Attendance
==========

* Conducted via Email

Agenda
======

* New staff!
* Cluster Usage Data for RHEL6 (~Summer 2012 until Present)
* Cluster Annual Purchase for Fiscal Year 2014
* Current Cluster Configuration
* Cluster Shutdown for September 2014

Material from Tim
=================

New Staff!!!
------------

Damian Valles
    Joined us in January 2014.

Adam Carlson
    Joined us in late-April 2014.

* They have already been working on your support requests and have been doing a
  great job getting up to speed on the cluster. Please understand that they are
  various levels of familiarity with **our** cluster and our community so some
  extra grace would be appreciated. Please make them feel welcome!
* You can read more information on their backgrounds at our `about page`_.

Cluster Usage Data for RHEL6
----------------------------

* This information is used to inform the research community on how the cluster
  is being used as a whole.
* We like to have some information regarding which resources are constrained
  (processors or memory) in order to alleviate those bottlenecks.

    * See this :ref:`RepCom meeting` for examples of information we like to
      present.

* **Bad News**: The script used for this task was broken in multiple ways.

    * While I have been able to fix the language specific issues (depracated
      features, e.g.), I have not had the time to successfully convince myself
      that the calculations are accurate.
    * Honestly, had I an inkling of the amount of time required, I would have
      been better off writing it from scratch.
    * **Result**: I do not have any data to present and there is simply no time
      left to generate it.

Simplistic TORQUE Reports
`````````````````````````

* The best I can do is some of the standard TORQUE reporting tools which only
  look at CPU requests and walltimes and have no reporting on memory. You can
  see those reports throughout this document.

Cluster Annual Purchase
-----------------------

* **Good News**: The choice of solution from a financial and performance
  perspective is very suggestive of a best course of action.

+---------------+---------------------------------------+---------+---------------+------------------------+------------+--------------------+--------------+-------------+
| Option Number | Option Description                    | GB/core | Total CPU-GHz | Price per unit CPU-GHz | Total CPUs | Price per unit CPU | Total Blades | Total Price |
+===============+=======================================+=========+===============+========================+============+====================+==============+=============+
| 1             | E5-2697v2 (12core, 2.7GHz), 256GB RAM | 10.67   | 1231.2        | $216.69                | 456        | $585.08            | 19           | $266,794.44 |
+---------------+---------------------------------------+---------+---------------+------------------------+------------+--------------------+--------------+-------------+
| 2             | E5-2660v2 (10core, 2.2GHz), 128GB RAM | 6.4     | 1188          | $197.70                | 540        | $434.94            | 27           | $234,865.83 |
+---------------+---------------------------------------+---------+---------------+------------------------+------------+--------------------+--------------+-------------+
| 3             | E5-2697v2 (12core, 2.7GHz), 128GB RAM | 5.3     | 1231.2        | $211.38                | 456        | $570.74            | 19           | $260,257.11 |
+---------------+---------------------------------------+---------+---------------+------------------------+------------+--------------------+--------------+-------------+
| 4             | E5-2665 (8core, 2.4GHz), 128GB RAM    | 8       | 1036.8        | $269.43                | 432        | $646.64            | 27           | $279,346.87 |
+---------------+---------------------------------------+---------+---------------+------------------------+------------+--------------------+--------------+-------------+

All options include 10GE, one 300GB 10K SAS drive, 3 years 8x5xNBD support

    * Options 1 and 2 leverage pre-configured bundles available from Cisco at
      significant discount levels.
    * Options 3 and 4 are custom configurations and the pricing assumes the same
      pre-approved discount in options 1 and 2. However, we've been told that
      almost certainly wouldn't happen.
    * Options 1, 2, and 3 are Ivy Bridge processors - die-shrink version of
      Sandy Bridge processors (which is option 4)
    * Option 4 is the same configuration we purchased last year.
    * CPU-GHz is merely the number of cores times the clock frequency
    * CPU is number of physical cores (not sockets)

* Option 2, to me, to be the best deal for the funds we have available.

    * Compared to last year's order (using previous processor generation), we
      get 15% more processor cycles at 27% less per cycle cost.
    * Compared to the only other attractive option (option 1), we get 4% less
      processor cycles but by spending 9% less per cycle cost (overall cost
      savings is only 12%).

        * Admittedly, a portion of that difference is less memory per node.

    * Compared to option 3 (which compares the 2660v2 against the 2697v2 at the
      same memory size), we get 4% less processor cycles but by spending 6.5%
      less per cycle cost (overall cost savings is 10%)

* The only other consideration is that while option 1 has higher costs at the
  CPU/blade level, the density allows us to realize savings on the
  infrastructure side (2 chassis instead of 3). That does count for something
  (about $12k).
* Finally, our target available spending amount is about $250,000.00

    * Other options than #2 would require additional funding sources or
      reduction of blades (2 or 3 blades)

Current Cluster Configurations
------------------------------

For some perspective, here is the current cluster configuration:

* **Qty 238 - IBM Blades (8 cores each) - 1904 cores total**

    * 120 Blades with 16GB RAM
    * 28 Blades with 48GB RAM
    * 84 Blades with 96GB RAM
    * 6 Blades with 144GB RAM

* **Qty 29 - Cisco B-series blades (16 cores each) - 464 cores total**

    * Each with 128GB RAM

**Total - 2368 cores (note -The Cisco blades are coming online in the next week)**

Our new cluster configuration (with existing Cisco blades online, and new blades online):

* **Qty 210 - IBM Blades (8 cores each) - 1680 cores total**

    * 92 Blades with 16GB RAM (Retiring 28 old blades)
    * 28 Blades with 48GB RAM
    * 84 Blades with 96GB RAM
    * 6 Blades with 144GB RAM

* **Qty 56 - Cisco B-series blades (128GB RAM each) - 1004 cores total**

    * 29 Blades with 16 cores
    * 27 Blades with 20 cores

**Total - 2684 cores**

* If the power and cooling loads of the new equipment permit, we may be able to
  leave the 2 chassis of old blades online for an additional capacity of 464
  cores.
* However, the older the equipment becomes, the more thought that has to be
  invested into code development, compilation, optimizations, etc. In an attempt
  to reduce operating costs, we may be urged to not keep (5 year old nodes)
  online.
* Please note: no Infiniband blades are affected by this year's purchase plan.

Cluster Shutdown in September 2014
----------------------------------

* Cluster firewalls must be upgraded (annual network refresh). The entire
  cluster network will be down for the activity.
* Would like to reserve the entire week of Labor Day (Tuesday through Sunday) to
  complete the work.

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2014/07/01
----------

Attendance
==========

Agenda
======

* Staff introductions
* Overview of Service Issues
* New hardware testing
* September Shutdown
* Policy Matters

Notes
=====

Staff Introductions
-------------------

* Damian Valles
* Adam Carlson

Service Issues
--------------

* Large Queue Backlogs

    * Hardware issues in a couple chassis' in May and early June

* Maui

    * Becoming much less stable than in the past
    * Working on SLURM as replacement

* Large queue backlogs

    * Running at near 100% CPU capacity

* IBM DS3400 storage

    * ``/archive0`` or retire?

New Hardware Coming Online
--------------------------

* FY13 hardware online (16-core SandyBridge processors, 128GB RAM, 10GE)

    * Some performance testing and benchmarking, as well as burn in

* FY14 hardware will be installed beginning with September shutdown

September Shutdown
------------------

* Cluster firewalls being replaced
* GPFS software and kernel upgrades
* BladeCenter Hardware Relocations
* (non-critical path) UCS Hardware Installations
* Potential change to scheduler

Policy Discussion
-----------------

* Gentleman's Agreement/Fair Share

    * Infiniband versus Ethernet versus TenGigabit
    * 2 days for tagging, 4 days for limit

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

----------
2015/05/05
----------

Attendance
==========

* Tim Miller
* Damian Valles
* Adam Carlson
* Brian Pearce
* Fed Salsbury
* Greg Cook
* Natalie Holzwarth
* Georgia Saylor
* Bill Kerr
* Scott Gayzik

Agenda
======

* Graduation Maintenance Day
* FY15 Annual Purchase
* Performance Data
* SLURM
* State of Cluster
* Upcoming Tasks

Maintenance Day
===============

* **Scheduled: 5/18 - Graduation Day**

    * Reservation starts at 8AM
    * Ends 5/19 at 8AM (not expected)
    * We will send notification when the cluster is available

* **UCS Firmware update**

    * Not on the UCS nodes
    * Purpose: UCS M4 nodes will require the update

* **V7000 Storage**

    * Firmware update:
    * Possible disk firmware update

        * If no jobs are running on the cluster

Performance Data
================

* Data was started to be collected in late October 2014 on Job and Node numbers
* **Average ratios of utilized, idle and under repair cluster nodes for each month**

.. image:: images/Nodes20142015.png

* **Average ratios of running and waiting cluster jobs for each month**

.. image:: images/Jobs20142015.png

* Data was started to be collected in early March 2014 on Core and Memory numbers

* **Average ratios of utilized, idle and under repair number of cores for each month**
    
    * March:
    
        * Max Utilized Avg = 95.46%
        * Utilized Avg = 78.21%
    
    * April:
    
        * Max Utilized Avg = 97.05%
        * Requested Avg = 79.38%
        * Utilized Avg = 76.41%

.. image:: images/Cores20142015.png

* **Average ratios of utilized and idle of the total memory in cluster for each month**

    * March:

        * Max Utilized Avg = 12.5%
        * Utilized Avg = 8.61%

    * April:

        * Max Utilized Avg = 36.93 %
        * Requested Avg = 26.15%
        * Utilized Avg = 9.53%

.. image:: images/Memory20142015.png

FY15 Annual Purchase
====================

General Approach
----------------

* Primary focus on purchases is core count, not memory
* Still maintaining a UCS standard memory configuration of 128GB

    * All UCS nodes are capable of at least 384GB

General Funding Status
----------------------

* No external grant funding identified.
* Changes at WFBH required us to purchase $11k in storage (16TB raw)
* GPFS licensing changes reduced maintenance budget surplus
* Would greatly appreciate any supplemental department, startup, or indirect funding

Proposed Configuration
----------------------

* 2 Chassis, 16 blades total
* 512 total cores (Dual Intel E5-2698 v3 processors, 2.30 GHz, 16-cores/processor)
* 2TB RAM total (128GB/blade on 16 blades)
* 300GB/blade (SSD drives *almost* cheap enough)
* 20GE/blade network connectivity, 40GE/chassis

    * Will reduce two original chassis from 40GE/chassis to 20GE/chassis

* Received an extra 10% in discounting from Cisco in order to meet the budget
  target and fill out the chassis.

SLURM
=====

:download:`Final paper <pdfs/SLURM_repcom_final.pdf>`

State of the Cluster
====================

* **New ARCHIVE Space**

    * EMC VNX 5600
    * On the headnodes: /archive1
    * 16TB - Raw
    * 12TB - Usable

* **UCS Additional Nodes**

    * Chassis: two nodes in 5; full 6, 7, 8
    * Total 540 cores; 20 per node

* **OFFLINED Nodes**

    * BC13BL14 - Bad Hard Drive (Out of Warranty)
    * BC14BL11 - Bad Memory DIMM (Out of Warranty)

* **Decommisioned**

    * DS3400 Storage Array
    * BC08BL05 - Bad Hard Drive (Out of Warranty)
    * BCG01 Nodes
    * BCG03 Nodes

* **Out of Warranty**

    * BC03 Nodes 4/20/15
    * BC06 Nodes 4/20/15

* **Upcoming IBM Expirations**

    * RHEL6HEAD1 6/30/15
    * RHEL6HEAD2 6/30/15
    * RHEL6HEAD3 6/30/15
    * BC05 Nodes 8/2/15
    * BC101BL02 9/5/15
    * BC101BL13 9/5/15
    * BC102BL02 9/5/15
    * BC102BL13 9/5/15
    * BC09[BL09-BL14] 1/6/16

Upcoming Tasks
==============

* RHEL7 upgrade to head and compute nodes

    * GPFS is now supported on RHEL7
    * Testing and collaboration for

        * Compiling software
        * Software installation options
        * Software operation
        * Software versions

    * RHEL4 tools still required??




.. _`deac-help@wfu.edu`: mailto:deac-help@wfu.edu
.. _`wiki.deac.wfu.edu`: https://wiki.deac.wfu.edu/index.php/Main_Page
.. _`Cluster Hardware Configuration`: Cluster:Hardware_Configuration
.. _`about page`: http://www.deac.wfu.edu/about/staff.html
