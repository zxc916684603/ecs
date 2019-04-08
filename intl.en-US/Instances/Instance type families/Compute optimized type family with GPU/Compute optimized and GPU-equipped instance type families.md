# Compute optimized and GPU-equipped instance type families {#concept_fgq_sdz_wgb .concept}

This topic describes specific compute optimized instance type families with GPUs, and lists the specific instance types within each of the instance type families. Specifically, the instance type families to be described are as follows: gn6v, gn5, gn5i, and gn4.

## gn6v, compute optimized type family with GPUs {#section_mgy_332_xgb .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Disks
-   Uses NVIDIA V100 GPU processors
-   Equipped with a vCPU to memory ratio of 1:4
-   Equipped with 2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Supports strong network performance through sufficient computing capacity
-   Suitable for the following scenarios:
    -   Deep learning, autonomous vehicles, voice recognition, and other AI applications
    -   Scientific computing, computational finance, genomics, and environmental analysis

**Instance types**

|Instance types|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)[\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|Packet forwarding rate \(Thousand pps\)[\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|NIC queues[\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|ENIs[\*\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|
|:-------------|:---|:-------------|:-----------------------------------------|:--|:----------------|:--------------------------------------------|:-----------------------------------------------------------------|:--------------------------------------|:----------------------------------|
|ecs.gn6v-c8g1.2xlarge|8|32.0|N/A|1 \* NVIDIA V100|1 \* 16|2.5|800|4|4|
|ecs.gn6v-c8g1.8xlarge|32|128.0|N/A|4 \* NVIDIA V100|4 \* 16|10.0|2,000|8|8|
|ecs.gn6v-c8g1.16xlarge|64|256.0|N/A|8 \* NVIDIA V100|8 \* 16|20.0|2,500|16|8|

**说明：** For more information, see [Create a compute optimized instance with GPUs](../../../../../reseller.en-US/Instances/Instance type families/Compute optimized type family with GPU/Create a compute optimized instance with GPUs.md#).

See [other instance type families](reseller.en-US/Instances/Instance type families/Instance type families.md#).

## gn5, compute optimized type family with GPU {#section_qtz_j32_xgb .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Disks
-   Uses NVIDIA P100 GPU processors
-   No fixed ratio of vCPU to memory
-   High-performance local NVMe SSD disks
-   Equipped with 2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Supports strong network performance through sufficient computing capacity
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing, such as computational fluid dynamics, computational finance, genomics, and environmental analysis
    -   High-performance computing, rendering, multi-media coding and decoding, and other server-side GPU compute workloads

**Instance types**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)[\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#) |Packet forwarding rate \(Thousand pps\)[\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|NIC queues[\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|ENIs[\*\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|
|:-------------|:---|:--------------|:-----------------------------------------|:--|:----------------|:---------------------------------------------|:-----------------------------------------------------------------|:--------------------------------------|:----------------------------------|
|ecs.gn5-c4g1.xlarge|4|30.0|440|1 \* NVIDIA P100|1 \* 16|3.0|300|1|3|
|ecs.gn5-c8g1.2xlarge|8|60.0|440|1 \* NVIDIA P100|1 \* 16|3.0|400|1|4|
|ecs.gn5-c4g1.2xlarge|8|60.0|880|2 \* NVIDIA P100|2 \* 16|5.0|1,000|2|4|
|ecs.gn5-c8g1.4xlarge|16|120.0|880|2 \* NVIDIA P100|2 \* 16|5.0|1,000|4|8|
|ecs.gn5-c28g1.7xlarge|28|112.0|440|1 \* NVIDIA P100|1 \* 16|5.0|1,000|8|8|
|ecs.gn5-c8g1.8xlarge|32|240.0|1760|4 \* NVIDIA P100|4 \* 16|10.0|2,000|8|8|
|ecs.gn5-c28g1.14xlarge|56|224.0|880|2 \* NVIDIA P100|2 \* 16|10.0|2,000|14|8|
|ecs.gn5-c8g1.14xlarge|54|480.0|3520|8 \* NVIDIA P100|8 \* 16|25.0|4,000|14|8|

**说明：** For more information, see [Create a compute optimized instance with GPUs](../../../../../reseller.en-US/Instances/Instance type families/Compute optimized type family with GPU/Create a compute optimized instance with GPUs.md#).

See [other instance type families](reseller.en-US/Instances/Instance type families/Instance type families.md#).

## gn5i, compute optimized type family with GPU {#section_u3b_l32_xgb .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Disks
-   Uses NVIDIA P4 GPU processors
-   Equipped with a vCPU to memory ratio of 1:4
-   Equipped with 2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Supports strong network performance through sufficient computing capacity
-   Suitable for the following scenarios:
    -   Deep learning
    -   Multi-media coding and decoding, and other server-side GPU compute workloads

**Instance types**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)[\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#) |Packet forwarding rate \(Thousand pps\)[\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|NIC queues[\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|ENIs[\*\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|
|:-------------|:---|:--------------|:-----------------------------------------|:--|:----------------|:---------------------------------------------|:-----------------------------------------------------------------|:--------------------------------------|:----------------------------------|
|ecs.gn5i-c2g1.large|2|8.0|N/A|1 \* NVIDIA P4|1 \* 8|1.0|100|2|2|
|ecs.gn5i-c4g1.xlarge|4|16.0|N/A|1 \* NVIDIA P4|1 \* 8|1.5|200|2|3|
|ecs.gn5i-c8g1.2xlarge|8|32.0|N/A|1 \* NVIDIA P4|1 \* 8|2.0|400|4|4|
|ecs.gn5i-c16g1.4xlarge|16|64.0|N/A|1 \* NVIDIA P4|1 \* 8|3.0|800|4|8|
|ecs.gn5i-c16g1.8xlarge|32|128.0|N/A|2 \* NVIDIA P4|2 \* 8|6.0|1,200|8|8|
|ecs.gn5i-c28g1.14xlarge|56|224.0|N/A|2 \* NVIDIA P4|2 \* 8|10.0|2,000|14|8|

**说明：** For more information, see [Create a compute optimized instance with GPUs](../../../../../reseller.en-US/Instances/Instance type families/Compute optimized type family with GPU/Create a compute optimized instance with GPUs.md#).

See [other instance type families](reseller.en-US/Instances/Instance type families/Instance type families.md#).

## gn4, compute optimized type family with GPU {#section_cts_l32_xgb .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Disks
-   Uses NVIDIA M40 GPU processors
-   No fixed ratio of CPU to memory
-   Equipped with 2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Supports strong network performance through sufficient computing capacity
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing, such as computational fluid dynamics, computational finance, genomics, and environmental analysis
    -   High-performance computing, rendering, multi-media coding and decoding, and other server-side GPU compute workloads

**Instance types**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)[\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#) |Packet forwarding rate \(Thousand pps\)[\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|NIC queues[\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|ENIs[\*\*\*\*\*](reseller.en-US/Instances/Instance type families/Instance type families.md#)|
|:-------------|:---|:--------------|:-----------------------------------------|:--|:----------------|:---------------------------------------------|:-----------------------------------------------------------------|:--------------------------------------|:----------------------------------|
|ecs.gn4-c4g1.xlarge|4|30.0|N/A|1 \* NVIDIA M40|1 \* 12|3.0|300|1|3|
|ecs.gn4-c8g1.2xlarge|8|30.0|N/A|1 \* NVIDIA M40|1 \* 12|3.0|400|1|4|
|ecs.gn4.8xlarge|32|48.0|N/A|1 \* NVIDIA M40|1 \* 12|6.0|800|3|8|
|ecs.gn4-c4g1.2xlarge|8|60.0|N/A|2 \* NVIDIA M40|2 \* 12|5.0|500|1|4|
|ecs.gn4-c8g1.4xlarge|16|60.0|N/A|2 \* NVIDIA M40|2 \* 12|5.0|500|1|8|
|ecs.gn4.14xlarge|56|96.0|N/A|2 \* NVIDIA M40|2 \* 12|10.0|1,200|4|8|

**说明：** For more information, see [Create a compute optimized instance with GPUs](../../../../../reseller.en-US/Instances/Instance type families/Compute optimized type family with GPU/Create a compute optimized instance with GPUs.md#).

See [other instance type families](reseller.en-US/Instances/Instance type families/Instance type families.md#).

