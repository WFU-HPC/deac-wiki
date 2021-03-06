.. DEAC Docs documentation master file

Welcome to the Official Documentation for the WFU DEAC cluster
==============================================================

.. code-block:: none

    ******************************************************************************
    *   Wake Forest University  Distributed Environment for Academic Computing   *
    *                                                                            *
    * __/\\\\\\\\\\\_____/\\\\\\\\\\\\\____/\\\\\\\\___________/\\\\\\\_________ *
    * __\/\\\///////\\\__\/\\\/////////___/\\\\\\\\\\\\______/\\\//////_________ *
    * ___\/\\\_____\//\\\_\/\\\___________/\\\////////\\\___/\\\/_______________ *
    * ____\/\\\______\/\\\_\/\\\\\\\\\____\/\\\______\/\\\__/\\\________________ *
    * _____\/\\\______\/\\\_\/\\\/////_____\/\\\\\\\\\\\\\\_\/\\\_______________ *
    * ______\/\\\______\/\\\_\/\\\__________\/\\\////////\\\_\//\\\_____________ *
    * _______\/\\\______/\\\__\/\\\__________\/\\\______\/\\\__\///\\\__________ *
    * ________\/\\\\\\\\\\\/___\/\\\\\\\\\\\\\\/\\\______\/\\\____\////\\\\\\\__ *
    * _________\///////////_____\/////////////_\///_______\///________\///////__ *
    *                                                                            * 
    ******************************************************************************

The WFU DEAC HPC Cluster is a centrally funded resource, meaning it is a free
tool for all Wake Forest University Reynolda Campus researches and students
(excluding the School's of Business, Law, Divinity, and Medicine). The HPC Team
is here to train users, troubleshoot scripts, upgrade hardware and software,
and support user needs.

* This wiki is the starting point reference for all cluster users.
* It is intended to be a community resource for information sharing.

    * Any new entries should aim to make the Cluster user experience easier.
    * We encourage all users (regardless of experience) to check the wiki
      periodically for updates.

* Wiki entries are categorized for convenience, listed below.

    * In general, lower level categories are for newer, less experienced
      cluster users.
    * Higher level categories get into more advanced information and steps.
    * Alphabetized categories are linked to special pages.

For help, send email to `deac-help@wfu.edu <mailto:deac-help@wfu.edu>`_

Quick start video
-----------------

This screencast will help you get started!

.. raw:: html

    <div style="text-align: center; margin-bottom: 2em;">
    <iframe width="100%" height="480" src="https://www.youtube.com/embed/vnkmdQqXeFg?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>

What's New
----------

* 01 Apr 2020: The cluster is supporting COVID-19 research through `Folding@home <https://stats.foldingathome.org/team/257105>`_!
* 05 Feb 2020: R 3.6.2 is now available!
* 30 Aug 2019: New semester is underway! Welcome new researchers!
* 31 Jul 2019: Mathematica 12 is now available!
* 30 Jun 2019: Python 3.7 is now available!
* 20 Sep 2018: **SLURM 18.08** for cluster resource management is now installed!
* 25 Jun 2018: New ticketing service is live! Transition should be seamless, and much less buggy than before!
* 03 Aug 2018: **Mathematica 11.3.0** for mathematic computations is available!
* 26 Jun 2018: **OpenMPI 3.1.1** for multinode job parellization is available!
* 25 May 2018: **R 3.5** for statistical and data analysis (module load R/3.5)
* 14 May 2018: **OpenMPI 3.1.0** for multinode job parellization is available!
* 07 Mar 2018: **IDL 8.7** for plot generation
* 20 Feb 2018: **2018 Intel Compiler and MKL Library Files - Cluster Edition**
  are now available in the cluster! Learn about its new features `here
  <https://software.intel.com/en-us/intel-parallel-studio-xe>`__
* 09 Feb 2018: All legacy hardware has been removed from the cluster! Reduced physical footprint saves us \$\$\$!
* 31 Jan 2018: **RAxML 8.2.10** for Maximum-likelihood based phylogenetic inference.
* 16 Jan 2018: SVN is no longer officially supported by the HPC team. We highly recommend GitHub or BitBucket!

Note: Users must be on a WFU network or connected via VPN to login to the head nodes!

To-Do
-----

* Some inspiration:

    * https://hpc.uni.lu/
    * https://hpc.uni.lu/users/docs/
    * https://ulhpc-tutorials.readthedocs.io/en/latest/

* Create a template for the software pages, i.e. website, versions, tested, etc.


.. toctree::
   :maxdepth: 2
   :caption: Level 0 - Beginner Resources

   faq
   guide-quick
   guide-beginner
   guide-linux


.. toctree::
   :maxdepth: 2
   :caption: Level 1 - Advanced Topics
   
   guide-advanced
   cluster
   software-slurm
   software-primer


.. toctree::
   :maxdepth: 2
   :caption: Reference Documentation

   software-packages
   software-python
   software-compilers
   software-licenses
   scc
   research
   repcom


.. toctree::
   :maxdepth: 2
   :caption: Admin Documentation

   admin-intel
   admin-spack
