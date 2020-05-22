# Overview

  - CUDA Toolkit Website\[1\]
  - Tesla Based Products\[2\]
  - Tesla Software Development Tools\[3\]

# Specifics

Use module:

`    $ module load cuda/9`

  - CUDA Installation Directory : /usr/local/cuda (for latest)
    CUDA Driver Version / Runtime Version : 9.2 / 9.1
    CUDA Capability Major/Minor version number: 6.0

# Job Submission

Support for GPU job submission is enabled the GRES (generic resource)
configuration within SLURM.\[4\]

See
[SLURM:Job_Script_Templates\#Job_Script_for_GPU](SLURM:Job_Script_Templates#Job_Script_for_GPU "wikilink")
for how to request GPU resources.

# References

<references/>

# Device Information

## Tesla P100 GPU Nodes

From a1a-u3-gpu-0\[1,2\]-p100 device:

>
>
> ```
>
> [ root@a1a-u3-gpu-01 ~]# /usr/local/cuda/samples/bin/x86_64/linux/release/deviceQuery
> /usr/local/cuda/samples/bin/x86_64/linux/release/deviceQuery Starting...
>
>  CUDA Device Query (Runtime API) version (CUDART static linking)
>
> Detected 2 CUDA Capable device(s)
>
> Device 0: "Tesla P100-PCIE-16GB"
>   CUDA Driver Version / Runtime Version          9.2 / 9.2
>   CUDA Capability Major/Minor version number:    6.0
>   Total amount of global memory:                 16281 MBytes (17071734784 bytes)
>   (56) Multiprocessors, ( 64) CUDA Cores/MP:     3584 CUDA Cores
>   GPU Max Clock rate:                            1329 MHz (1.33 GHz)
>   Memory Clock rate:                             715 Mhz
>   Memory Bus Width:                              4096-bit
>   L2 Cache Size:                                 4194304 bytes
>   Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
>   Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
>   Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
>   Total amount of constant memory:               65536 bytes
>   Total amount of shared memory per block:       49152 bytes
>   Total number of registers available per block: 65536
>   Warp size:                                     32
>   Maximum number of threads per multiprocessor:  2048
>   Maximum number of threads per block:           1024
>   Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
>   Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
>   Maximum memory pitch:                          2147483647 bytes
>   Texture alignment:                             512 bytes
>   Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
>   Run time limit on kernels:                     No
>   Integrated GPU sharing Host Memory:            No
>   Support host page-locked memory mapping:       Yes
>   Alignment requirement for Surfaces:            Yes
>   Device has ECC support:                        Enabled
>   Device supports Unified Addressing (UVA):      Yes
>   Device supports Compute Preemption:            Yes
>   Supports Cooperative Kernel Launch:            Yes
>   Supports MultiDevice Co-op Kernel Launch:      Yes
>   Device PCI Domain ID / Bus ID / location ID:   0 / 9 / 0
>   Compute Mode:
>      < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
>
> Device 1: "Tesla P100-PCIE-16GB"
>   CUDA Driver Version / Runtime Version          9.2 / 9.2
>   CUDA Capability Major/Minor version number:    6.0
>   Total amount of global memory:                 16281 MBytes (17071734784 bytes)
>   (56) Multiprocessors, ( 64) CUDA Cores/MP:     3584 CUDA Cores
>   GPU Max Clock rate:                            1329 MHz (1.33 GHz)
>   Memory Clock rate:                             715 Mhz
>   Memory Bus Width:                              4096-bit
>   L2 Cache Size:                                 4194304 bytes
>   Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
>   Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
>   Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
>   Total amount of constant memory:               65536 bytes
>   Total amount of shared memory per block:       49152 bytes
>   Total number of registers available per block: 65536
>   Warp size:                                     32
>   Maximum number of threads per multiprocessor:  2048
>   Maximum number of threads per block:           1024
>   Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
>   Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
>   Maximum memory pitch:                          2147483647 bytes
>   Texture alignment:                             512 bytes
>   Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
>   Run time limit on kernels:                     No
>   Integrated GPU sharing Host Memory:            No
>   Support host page-locked memory mapping:       Yes
>   Alignment requirement for Surfaces:            Yes
>   Device has ECC support:                        Enabled
>   Device supports Unified Addressing (UVA):      Yes
>   Device supports Compute Preemption:            Yes
>   Supports Cooperative Kernel Launch:            Yes
>   Supports MultiDevice Co-op Kernel Launch:      Yes
>   Device PCI Domain ID / Bus ID / location ID:   0 / 132 / 0
>   Compute Mode:
>      < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >
> > Peer access from Tesla P100-PCIE-16GB (GPU0) -> Tesla P100-PCIE-16GB (GPU1) : No
> > Peer access from Tesla P100-PCIE-16GB (GPU1) -> Tesla P100-PCIE-16GB (GPU0) : No
>
> deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 9.2, CUDA Runtime Version = 9.2, NumDevs = 2
> Result = PASS
> ```

[Category:GPU](Category:GPU "wikilink")
[Category:Hardware](Category:Hardware "wikilink")

1.  <https://developer.nvidia.com/cuda-downloads>
2.  <http://www.nvidia.com/object/tesla-servers.html>
3.  <http://www.nvidia.com/object/tesla_software.html>
4.  <https://slurm.schedmd.com/gres.html>
