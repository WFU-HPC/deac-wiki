# Cluster Architectural Features

![UCS_B200_Chassis.jpg](UCS_B200_Chassis.jpg "UCS_B200_Chassis.jpg")

## Head Nodes

  - Users connect to and interact with the cluster via **head nodes**.

:\* These systems have the exact same software installations as the
cluster **compute nodes** plus some additional interactive tools for end
user environments.

## Compute Nodes

  - Constructed of Cisco UCS Hardware, the compute nodes (where all the
    job processing takes place) are grouped by into different categories
    by type.
  - 'Cisco UCS' nodes are grouped and can be designated by their fabric
    connection (backend switch) listed below.

:\* All UCS blades are connected through a singular tengig fabric.

  - Nodes can also be grouped by their chassis designation,
    *ucs\#-\#\#*, denoting sets of 8 corresponding compute nodes
    contained within the same physical chassis..
  - Parallel processing jobs are strongly encouraged to request that all
    nodes for a job belong to a single category or processor type.

:\* See [SLURM:Quick Start Guide](SLURM:Quick_Start_Guide "wikilink")
and [SLURM:Job Script Templates](SLURM:Job_Script_Templates "wikilink")
for examples of how to do this.

## SLURM Node Features

  - All compute nodes have assigned features within SLURM. These
    features can be specified as constraints to limit node selection for
    jobs. They are:

:; head : These nodes are used to submit jobs to SLURM, and are not
assigned to any partition

:; gpu : These nodes have GPU's installed and available

:; ucs\#-XX : These nodes belong to UCS-2 or UCS-3 Chassis XX, e.g.
ucs3-1, ucs2-14, etc. are node properties

:; scr50gb : These nodes have 40GB of local scratch disk space to use
for jobs

:; scr250gb : These nodes have 250GB of local scratch disk space to use
for jobs

:; scr425gb : These nodes have 400GB of local scratch disk space to use
for jobs

:; haswell: These nodes have [Intel's Xeon E5
Haswell](Information:Intel_chip_architecture#Architectures "wikilink")
based processors (32-core UCS nodes)

:; broadwell: These nodes have [Intel's Xeon E5
Broadwell](Information:Intel_chip_architecture#Architectures "wikilink")
based processors (44-core UCS nodes)

:; skylake : These nodes have [Intel's Xeon E5
Skylake](Information:Intel_chip_architecture#Architectures "wikilink")
based processors (44-core UCS nodes)

  - A complete list of a nodes attributes can be found with the
    [scontrol command listed
    here](SLURM:Quick_Start_Guide#Node_information "wikilink")

# Physical Hardware Specifications

## Aggregate Information

  -
    **Nodes** or **Blades** : 95 nodes
    **Processors** : 3892 cores
    **GPU cores**: 14,336 cores
    **Memory** : 19.31TB
    **Storage** : 197.86TB

## Compute Nodes

**93 - Cisco B-series Blades - 3,892 cores, 19.31TB total**:

  -

      -
        24 Haswell Blades with 32 cores -- 128GB RAM
        43 Broadwell Blades with 44 cores -- 256GB RAM
        26 Skylake Blades with 44 cores -- 188GB RAM

## GPU Nodes

For in-depth GPU information, see
[Information:GPU_Computing](Information:GPU_Computing "wikilink")

**2 - UCS C240 Nodes (44 cores each) - 88 cores total**:

  -

      -
        2 GPU cards per node
        256GB RAM per node
        All are NVIDIA Tesla **P100**
        3,584 CUDA cores per Tesla
        14,336 CUDA cores total\!

COMING SOON: **1 - UCS C480 Nodes - 88 cores total**:

  -

      -
        6 GPU cards per node
        512 GB RAM per node
        All are NVIDIA Tesla **V100**
        5,120 CUDA cores per Tesla
        30,720 CUDA cores total\!

**Total GPU cores - 47,056\!**

## Storage

![Fas8040.jpg‎](Fas8040.jpg‎ "Fas8040.jpg‎")

  - **NetApp FAS8040 Storage Array** (177.86TB shared via NFS)
    **[Technical
    Specs](http://www.netapp.com/us/products/storage-systems/fas8000/fas8000-tech-specs.aspx)**
    **[Hardware Datasheet](:File:FAS8000-datasheet.pdf‎ "wikilink")**
    **[NetApp YouTube
    Channel](https://www.youtube.com/channel/UCraITOUxo4l3oYQBH8fofyw)**

<!-- end list -->

  - 24 - 800GB SSD (flash pool for fast read/write)
  - 120 - 2TB SATA 7.2K

<!-- end list -->

  - **Amazon Glacier Cloud Storage** (unlimited)

<!-- end list -->

  - Unlimited cloud storage with variable data expiration.
  - *Host* of cluster archive storage

# References

<references/>

[Category:Cluster](Category:Cluster "wikilink")
[Category:SLURM](Category:SLURM "wikilink")
[Category:Hardware](Category:Hardware "wikilink")
