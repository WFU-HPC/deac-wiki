# Overview

Typically when you access a cluster system you are accessing a head
node, that acts as a gateway to cluster resources. A head node is setup
to be submit jobs to the cluster's scheduler. In general, when "logging
in to the cluster" is mentioned, the act of logging into a head node is
how you do it.

A head node is often nothing more than a system configured to act as the
midway point between cluster resources and everything else. When you are
on a head node, you should not actually running or working on cluster
compute resources. Configuration of the headnode is very similar to
available compute nodes, in that all required software and data paths
should be present. This allows users to verify job functionality before
fully submitting them. This simplifies access, usage, and efficiency by
having all interactions filtered and managed through a few designated
points. In theory, users should never need to access any of the
individual compute nodes directly, instead relying on the head node and
the tools it provides to submit jobs to the cluster, monitor them, and
view and retrieve their results.

Ideally you do not want to run computational programs on the head node
itself. Meaning specifically, any programs you want to run on the
cluster should not be run on the head node, instead they should be run
and tested on the cluster itself using the scheduling system tools on
the head node. You should restrict your usage of the head node to
programs that let you build and prepare your cluster programs and manage
and view your data.

# DEAC Headnodes

**gemini.deac.wfu.edu**
**pegasus.deac.wfu.edu**

The DEAC cluster has TWO headnodes. These nodes are virtual machines (to
allow better redundancy and higher uptime), with 12 cores and 128GB of
memory each.

# Access

To login to the DEAC cluster headnodes, users must use the SSH protocol.
Login can only be achieved after a
\[<https://is.wfu.edu/deac/user-support/account-request/>| cluster
account request\] has been submitted. Do NOT use your Desktop or Laptop
account/password to access these nodes\!

*Login to the DEAC headnodes is restricted to Wake Forest Networks
only*\! This is a security precaution to prohibit unauthorized access
and bot login attempts. If any user is attempting to login via SSH off
campus, they must have an \[<https://is.wfu.edu/services/vpn/>|
established VPN connection\] to vpn.wfu.edu\! To make this VPN
connection, one SHOULD use their Desktop/Laptop account/password. Once
the VPN connection is made, SSH to the DEAC headnodes and user your
cluster account/password as you normally would\!

# External Collaborators

If you wish to collaborate with non-WFU personnel, please have them
email deac-help@wfu.edu and we will create a guest account for them to
be able to VPN in. More detailed info to come
soon.

[Category:New_User_Information](Category:New_User_Information "wikilink")
[Category:Cluster](Category:Cluster "wikilink")
