====================
DEAC Advanced Topics
====================

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

---------
Profiling
---------

`Profiling`_ is a form of dynamic program analysis (as opposed to static code
analysis). It is the investigation of a program's behavior using information
gathered as the program executes. The usual purpose of this analysis is to
determine which sections of a program to optimize -- to increase its overall
speed, decrease its memory requirement or sometimes both.

GCC and gprof
=============

GCC and gprof are GNU tools. :download:`Here is a contrived example
<http://www.wfu.edu/~chindw/DEAC/Examples/GprofExample.tar.gz>` please download
a copy of the source.

First, you will need to compile with the "-pg" option. Here is an example
Makefile:

.. code-block:: make

    CC=gcc
    CFLAGS=-pg -g
    
    # Unset the next three because Intel compiler installation
    # sets them and they interfere
    INCLUDE=
    LD_LIBRARY_PATH=
    CPATH=
    
    .PHONY: clean
    
    sieve: sieve.c
        $(CC) $(CFLAGS) -o $@ $^ -lm
    
    clean:
        /bin/rm -f sieve gmon.out

Then, run make to build. Run the program as usual: the program will
generate profiling data in a file named ``gmon.out``. To see the
profiling information, do:

.. code-block:: none

    [username@headnode GprofExample]> ./sieve 20000
    <output removed>
    [username@headnode GprofExample]> gprof sieve gmon.out
    
    Flat profile:
    
    Each sample counts as 0.01 seconds.
      no time accumulated
    
      %   cumulative   self              self     total
     time   seconds   seconds    calls  Ts/call  Ts/call  name
     62.09      0.21     0.21     2263     0.09     0.09  factorial
     35.48      0.33     0.12        1   120.63   341.80  sieve
      2.96      0.34     0.01     2263     0.00     0.00  foo
      0.00      0.34     0.00        1     0.00     0.00  init
      0.00      0.34     0.00        1     0.00     0.00  xcalloc
    <truncated>

You will notice that there are two functions which have been called the most
number of times: ``factorial``, and ``sieve``. Of these two, about 62% of the
total running time was used by the ``factorial`` function, and 35% by the
``sieve`` function.

Read the `online gprof manual`_ for more information.

See Also
--------

* `HPCToolkit`_: an integrated suite of tools for measurement and analysis of
  program performance on computers ranging from multicore desktop systems to the
  nation's largest supercomputers.
* `GprofQuickStart`_: profiling with GNU's gprof and GCC

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

---------------
Version Control
---------------

.. _github:

GitHub
======

What Is GitHub?
---------------

GitHub is a development platform inspired by the way you work. From open source
to business, you can host and review code, manage projects, and build software
alongside millions of other developers.

Getting Started
---------------

Create an Account
`````````````````

1.  Navigate to https://github.com.
2.  Create an account with your University email.
3.  Leave, "Unlimited public repositories for free" as your plan.
4.  Answer "Tailor your experience" questions and submit, or Skip
5.  Verify your email account by clicking the provided link in email sent to
    your inbox.

Get Educational Discount
````````````````````````

1.  Navigate to https:education.github.com.
2.  Select role that describes you at WFU, and enter "Individual Account"
3.  Click Next.
4.  Ensure your chosen github login name and .edu email address are entered.
    **Note**: If you are asked to upload an image of your school ID, then your
    email has not been verified!
5.  Enter school name and state how you will use Git (in general), and click
    "Submit Request"
6.  Check inbox for Discount email (within a few hours).

Using GitHub
------------

* `User guide`_ <https://guides.github.com/activities/hello-world/>
* `User tutorial`_ <https://try.github.io>

Create a Repository
```````````````````

1. In the upper right corner, next to your avatar, click "+" and then select
   New repository.
2. Name your repository.
3. Write a short description.
4. Select "Private" if discount approval has been received.

    * Leaving as public makes your repository world viewable.
    * You still specify who can commit and make changes.

5. If new repo, select "Initialize this repository with a README".

    * If importing a repo, do not select.

Using a New Repository
``````````````````````

* Command line steps to add data to

.. code-block:: none

    echo "# Testing" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin https://<username>@github.com/<GIT-REPO>/Testing.git
    git push -u origin master

* Those steps will copy your repository locally, create a new file, and push it
  remotely.

See Also
--------

* :ref:`bitbucket`
* :ref:`svn2git`

.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

.. _bitbucket:

Bitbucket
=========

What Is Bitbucket?
------------------

Bitbucket is a web-based hosting service that is owned by Atlassian, used for
source code and development projects that use either Mercurial or Git revision
control systems.

Getting Started
---------------

Create an Account
`````````````````

1. Navigate to https://www.bitbucket.org.
2. Create an account with your University email.

Afterwards, your account should automatically be converted to an unlimited
academic plan.

Create a Team
`````````````

1. Log in and click the "+" sign on the left pane.

    * You should be able to even login with Google - no password required!

2.  Under the "Create A New" submenu, click "Team".

    * Team names should follow the naming scheme: "DEAC_researchGrp".
    * This is where research group member emails are added.

3.  Once a team is created, a link to create a new Repository will appear

Create a Repository
```````````````````

1.  Click the "+" sign on the left pane.
2.  Click "Repository" under "CREATE A NEW"
3.  In the new menu, select a pre-existing "Project name" or create a new one.
4.  Provide a relevant repository name.
5.  Ensure "This is a private repository" remains checked if to be seen by your
    group only.
6.  Leave "Git" as the Version Control System

    * Under advanced, add a description and specify code type if desired.

7.  Once the repository is created, lists below "Get started with command line"
    will provide steps to use your new repo!

Using a New Repository
``````````````````````

1.  After creating your repo, an "I'm starting from scratch" link will provide
    exact steps to use from headnodes.

.. code-block:: none

    git clone https://loginName@bitbucket.org/DEAC-researchGrp/repositoryName.git
    cd repositoryName
    echo "# My project's README" >> README.md
    git add README.md
    git commit -m "Initial commit"
    git push -u origin master

1.  Those steps will copy your repository locally, create a new file, and push
    it remotely.

Troubleshooting
---------------

Academic Plan Enrollment
========================

* If not automatically enrolled into an academic plan, one of two ways can be used

    * Complete this form: https://www.atlassian.com/software/views/bitbucket-academic-license.jsp.

* or:

    * Change your plan manually
    * Log in to your account, click the user icon and "View Profile"
    * Under Plans and Billing, click "Plan Details"
    * If it does not state "You're on the Academic (tiered) plan.", click
      "Change plan"
    * Scroll down and click "apply to have your institution added."

* All users on your team should have the academic plan once fixed

See Also
--------

* :ref:`github`
* :ref:`svn2git`


.. #############################################################################
.. #############################################################################
.. #############################################################################
.. #############################################################################

.. _svn2git:

Converting a SVN repo to GIT
============================

The following is based upon an `online tutorial`_.

## Preparation

* You will need to use the pre-downloaded svn-migration-scripts.jar file on the
  headnodes

    * You can also download :download:`svn-migration-scripts.jar
      <https://bitbucket.org/atlassian/svn-migration-scripts/downloads/svn-migration-scripts.jar>`
      locally, but additional steps will need to be covered OYO via the
      referenced tutorial.
    * Verify the downloaded file if using locally: ``java -jar
      ~/svn-migration-scripts.jar verify``

* Generate an "Authors" file to convert SVN commit info to Git format

.. code-block:: none

    java -jar svn-migration-scripts.jar authors <svn-repo> > authors.txt
    j.doe = j.doe <j.doe@mycompany.com>
    m.smith = m.smith <m.smith@mycompany.com>

* This will save all users who have committed to the SVN repo, which you will
  then need to update with full name and email.
* Edit the authors.txt file and change the portion to the right of the "=" to
  the example below

.. code-block:: none

    j.doe = John Doe <john.doe@atlassian.com>
    m.smith = Mary Smith <mary.smith@atlassian.com>

Converting
----------

* Beware this process can take a significant amount of time for large repos.

    * For example, a 400MB repository with 33K commits can take around 12 hours.

* The command to convert a SVN repo with a standard layout is:

.. code-block:: none

    git svn clone --stdlayout --authors-file=authors.txt <svn-repo>/<project> <git-repo-name>

* Where ``svn-repo`` is the URI of the SVN repository you are migrating, project
  is the name to be imported, and ``git-repo-name`` is the new Git repository

.. code-block:: none

    git svn clone --stdlayout --authors-file=authors.txt <SVN_URL>/NiceCode NiceCodeAsGit

* Inspect what was migrated

    * Run ``git branch -r`` to examine branches moved
    * Run ``git tag`` to inspect tags with commits
    * It's okay if things seem out of order, as long as the content is there.

* Next, all tags and branches must be cleaned with the following command:

.. code-block:: none

    java -Dfile.encoding=utf-8 -jar svn-migration-scripts.jar clean-git --force

* Once fully converted to Git locally, the repository can be imported to Bit
  Bucket via the "I have an existing project" commands given after creating a
  repo.

Importing
---------

* Switch to your repository's directory
* Connect your existing repository to Git

.. code-block:: none

    git remote add origin https://login@<GIT-URL>/repositoryName.git
    git push -u origin master

* You can now checkout this git repo from Bit Bucket remotely!
* To test, cd to a different path and clone

.. code-block:: none
    
    git clone https://login@<GIT-URL>/repositoryName.git

SVN to GitHub real world example
--------------------------------

* Create directory for git clone

    * mkdir gitbranch

* Using a browser, login to www.github.com with login name and password
* Click on "New repository" box
* Click on "Create repository"
* On cluster headnode, within git clone directory, run the following command:

    * ``git clone https://>\[<username>@\]github.com/<GIT-REPO>/<REPO>.git``
    * Enter password if requested - Note, username only needed for PRIVATE repo

* Enter git branch

    * ``cd <REPO>``

* Initialize as a git svn repo

    * ``git svn init --stdlayout --no-metadata <SVN-URL>``

* Modify git config for SVN repo settings

    * ``git config --edit``

.. code-block:: none

     1 [core]
     2         repositoryformatversion = 0
     3         filemode = true
     4         bare = false
     5         logallrefupdates = true
     6 [remote "origin"]
     7         fetch = +refs/heads/*:refs/remotes/origin/*
     8         url = https://natalieawh@github.com/natalieawh/AtompawProject.git
     9 [branch "master"]
    10         remote = origin
    11         merge = refs/heads/master
    12 [svn-remote "svn"]
    13         noMetadata = 1
    14         url = <SVN-URL>
    15         fetch = trunk/<branch to convert>:refs/remotes/trunk/origin
    16         branches = branches/*/<branch to convert>:refs/remotes/origin/*
    17         tags = tags/*/<branch to convert>:refs/remotes/tags/origin/*

* **NOTE** Git 1.7 does not properly initial svn repo, "origin" must be added to
  "fetch," "branches" and "tags"

Note that the "origin" is critical.

* After saving this file, then retrieve SVN data

    * git svn fetch

* After several minutes, there is a stream of file names and the files appear in
  the repository.
* If multiple branches were retrieved, run bash command:

.. code-block:: none

    #!/bin/bash
    for branch in `git branch -r |grep "branches/" |sed 's/ branches\///'` ; do
        git branch $branch refs/remotes/branches/$branch
    done
    for tag in `git branch -r |grep "tags/" |sed 's/ tags\///'` ; do
        git tag -a -m"Converting SVN tags" $tag refs/remotes/tags/$tag
    done

* Push data to git

    * ``git push --all origin``
    * ``get push --tags origin``

* See also: https://www.atlassian.com/git/tutorials/migrating-overview

.. _`online gprof manual`: http://sourceware.org/binutils/docs-2.20/gprof/index.html
.. _`Profiling`: http://en.wikipedia.org/wiki/Profiling_(computer_programming)
.. _`HPCToolkit`: http://hpctoolkit.org
.. _`GprofQuickStart`: http://vmlinux.org/foswiki/bin/view/Main/GprofQuickStart
.. _`User guide`: https://guides.github.com/activities/hello-world/
.. _`User tutorial`: https://try.github.io
.. _`online tutorial`: https://www.atlassian.com/git/tutorials/svn-to-git-prepping-your-team-migration
