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

    * Ready to install the hardware after several physical location restrictions have been listed.

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

- Review 32-bit Node Status

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

Compute Nodes
    We currently have 39 blades with 4 total processing cores (i.e. dual core,
    dual processor/socket blades)
    
    * Each of these blades has 8GB of physical RAM
    
    We currently have 103 blades with 8 total processing cores (i.e. quad core,
    dual processor/socket blades)
    
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

Compute Nodes
    We currently have 11 blades with 4 total processing cores (i.e. dual core, dual processor/socket blades)
        * Each of these blades has 8GB of physical RAM
    
    We currently have 131 blades with 8 total processing cores (i.e. quad core, dual processor/socket blades)
        * 66 of these blades have 16GB of physical RAM
        * 7 of these blades have 32GB of physical RAM
        * 58 of these blades have 48GB of physical RAM
  
Storage
    * 41.9TB of storage online as a GPFS filesystems
    * 675GB of storage held in reserve for ``/home``
    * 5.4TB of storage not in use from Spr 2010 purchase.
    * 15TB "in transit" from the WFUHS Enterprise Storage service.
    * 18TB (usuable) new storage from Winter 2010 purchase.

Storage Nodes
    18 Storage Nodes
        * 2 nodes dedicated for WFUHS research groups
        * 2 nodes dedicated to WFURC for WFUHS storage

Minutes
=======












.. _`deac-help@wfu.edu`: mailto:deac-help@wfu.edu
.. _`wiki.deac.wfu.edu`: https://wiki.deac.wfu.edu/index.php/Main_Page
.. _`Cluster Hardware Configuration`: Cluster:Hardware_Configuration
