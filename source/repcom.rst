========================
WFU DEAC RepCom Meetings
========================

.. toctree::


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

* Brought in WFUHS accounts. Made minor corrections. Added Non-disclosure requirements.
    
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













.. _`deac-help@wfu.edu`: mailto:deac-help@wfu.edu
.. _`wiki.deac.wfu.edu`: https://wiki.deac.wfu.edu/index.php/Main_Page
.. _`Cluster Hardware Configuration`: Cluster:Hardware_Configuration
