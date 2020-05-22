# Background

By and large, the most difficult issue to effectively manage with a
large research group (that is, greater than 1 person\!) is the data
created on the cluster by everyone in that research group. Subtle issues
related to disk storage and data ownership can make results someone you
supervise has generated be completely inaccessible to you\! Some
effective research group policies regarding how your users function can
help reduce the stress and frustration of having all the results but not
being able to view them. This article covers some background information
and strategies to help you develop those policies in your group.

## Account Convention

Accounts on the cluster are created such that each user has their own
primary group. This is the default convention followed by Red Hat and
adopted by the WFU DEAC cluster. This convention means that, when a user
creates a file or directory, it will be typically be owned and grouped
using that user's primary memberships.

:\* The caveat to this convention involves files created in a job
submitted to the cluster. Cluster jobs run as the user submitted (as you
would expect) and as the fairshare group under which the job was
submitted (not expected). So, for user BOB submitting a job under the
generalGrp fairshare group, all files created by the job will be
'BOB.generalGrp'.

## Group Convention

All users are assigned to multiple groups. These groups include the
"fairshare" group (under which your priorities are determined by the
cluster scheduler), your primary research group (which could also be the
fairshare group), your primary department, a general research
collaboration group, etc. Any user can change the group membership of a
file or directory that of which they are a member (and have permission)
to any other group to which they belong.

## Group Sticky Bit

UNIX/Linux has this concept of a "group sticky bit" that can be set on a
directory. By setting the bit, you are making the group membership of
that directory "sticky", that is you declare that all new files and
directories created in that directory will have the same group
membership of the parent. A common misunderstanding of the sticky bit is
that it changes existing files and directories, which is does not\! Only
newly created
files/directories.

`   This sticky bit overrides any default behavior that is in effect for `
`   file or directory creation, even the SLURM job group membership behavior!`

# Maintaining Group Ownership

The general idea is simple. Create a primary level directory with the
correct group membership and sticky bit set so that all directories and
files underneath now belong to the group. Below the desired directory,
run the following commands:

` $ chgrp researchGrp /deac/researchGrp`
` $ chmod 2770 /deac/researchGrp`

The remaining steps involved require a group policy set up by the
research group. This policy must include two key features:

1.  All users must create their data files in that directory tree. You
    may want to have someone do a quarterly audit of the directory to
    ensure all the contents still have the correct group memberships.
2.  All users must have a specific 'umask' in the login configuration
    files (.bashrc or .tcshrc) such that the group permissions have at
    least read access and maybe even write access ('umask 027' or 'umask
    007', respectively)

# Restricting Access

You want everyone in your group to be able to read and write to the
directory but no one else. For convenience, you'd like the filesystem
and/or users to automatically ensure these permissions in order to avoid
that last minute deadline hitting and you can't read the one file that
you need.

First let's ensure your researchGrp directory is group writeable:

` $ chgrp research /deac/reserachGrp`
` $ chmod g+w /deac/researchGrp`

## Group access only

Remove all access to non-group members:

` $ chmod o-wrx /deac/researchGrp`

## World readable

Assuming you have run the "Group access only" command... If you want
non-group members to have read only access, but not edit privileges:

` $ chmod o+r /deac/researchGrp`

[Category:New User
Information](Category:New_User_Information "wikilink")
