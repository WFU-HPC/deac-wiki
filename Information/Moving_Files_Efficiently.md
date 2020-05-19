Disk space is the most overlooked resource until it gets fully utilized.
Users are encouraged to periodically review their usage on the various
filesystems and relocate or back up/remove files that are infrequently
used or no longer needed on the cluster. Aside from space consumption,
Disk IO (Input/Output) plays a large role in High Performance Computing.
The more IO generated, the slower performance can be.

This document will instruct users on how to copy files efficiently
within the cluster or external to the cluster using a command called
**rsync**.

## Requirements

  - rsync : A syncronization program that looks for differences between
    the source and destination files/directories in order to synchronize
    the two locations as specified.
    SSH : If the syncronization of files/directories occurs between two
    different servers, you will need to use SSH to perform the file
    transfers (FTP and RCP are not permitted).

## Examples

### Assumptions

  - *srcdir* : Directory that contains the files to be moved.
    *destdir* : Directory where you would like to move the contents of
    ***srcdir*** files.
    *remhost* : Remote host (outside of cluster) where you would like to
    move the
directory/files.

### Copying files from researchGrp directory to Archive

`   rsync -av /deac/generalGrp/users/carsloas/srcdir /archive1/generalGrp/users/carlsoas/destdir/`

### Copying files to ***remhost***

`   export RSYNC_RSH=/usr/bin/ssh  ###  For bash.  Use "setenv RSYNC_RSH /usr/bin/ssh" for tcsh.`
`   rsync -av /deac/generalGrp/users/carlsoas/srcdir/ carlsoas@remhost:/home/carlsoas/cluster.archive/destdir/`

  - You will be prompted for a password for the user account on the
    ***remhost*** before the file transfer will begin.

## About rsync

### The Good

  - rsync could take a while before the actual transfer starts : If you
    are resuming an interrupted rsync or have a significant number of
    files to copy, **rsync** could take several minutes to determine the
    file list to transfer. This delay is even more likely for remote
    file transfers.

<!-- end list -->

  - rsync can pick up where it left off : If your file transfer was
    aborted for whatever reason (network problem, for example), you can
    re-issue the exact same command in the same directory and rsync will
    determine what is different and resume where it left off.

<!-- end list -->

  - rsync can be issued multiple times with the same arguments\! : As
    the previous comment stated, you can verify that all of your files
    are the same one last time before you remove them from the full
    filesystem.

### The Pitfalls

  - *Trailing slashes on the source specification DOES matter\!* : If
    the trailing slash is **omitted** from the file/directory source
    specification (***srcdir***), the directory (and all of its
    contents, preserving the directory structure) will get created in
    the destination (***destdir***) specified.

`   $ ls test1/*`
`   test1/testA  test1/testB  test1/testC`
`   $ rsync -av test1 test2`
`   building file list ... done`
`   created directory test2`
`   test1/`
`   test1/testA`
`   test1/testB`
`   test1/testC`
`   wrote 232 bytes  read 68 bytes  600.00 bytes/sec`
`   total size is 0  speedup is 0.00`
`   $ ls test2`
`   test1`
`   $ ls test2/test1/*`
`   test2/test1/testA  test2/test1/testB  test2/test1/testC`

Specifying the trailing slash means the all of the files and directories
in the source specification (***srcdir***) will get copied directly the
destination specified (***destdir***).

`   $ ls test1/*`
`   test1/testA  test1/testB  test1/testC`
`   $ rsync -av test1/ test3`
`   building file list ... done`
`   created directory test3`
`   test1/`
`   test1/testA`
`   test1/testB`
`   test1/testC`
`   wrote 232 bytes  read 68 bytes  600.00 bytes/sec`
`   total size is 0  speedup is 0.00`
`   $ ls test3/*`
`   test3/testA  test3/testB  test3/testC`

  - *rsync does not (\!) mirror two directory structures\!* : **rsync**
    merely synchronizes the source files with the destination files,
    creating them if they do not exist. **rsync** does not remove files
    (by default) from the destination that are no longer in the source.

<!-- end list -->

  - *rsync does not remove files from the source destination as it
    copies them\!* : This means that you have not actually freed up any
    space after running the rsync command\! In situations where disk
    space is critically low, it is ***STRONGLY*** suggested that you
    rsync smaller directory structures and remove them quickly to free
    up space in a more timely fashion to relieve the constraints.

<!-- end list -->

  - *rsync may not obey the destination directory's data management
    policies\!* : This simply means that when you use rsync to move
    data, your destination may require different read/write/execute and
    owner/group membership settings than the original directory. After
    the rsync, before sure to make the required changes to comply with
    that policy.

[Category:New User
Information](Category:New_User_Information "wikilink")---
title: Information:Moving Files Efficiently
permalink: /Information:Moving_Files_Efficiently/
---

