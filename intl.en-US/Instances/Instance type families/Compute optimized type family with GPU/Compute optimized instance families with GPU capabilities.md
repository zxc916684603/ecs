# Compute optimized instance families with GPU capabilities {#concept_fgq_sdz_wgb .concept}

This topic describes the vgn5i, gn6i, gn6v, gn5, gn5i, and gn4 compute optimized instance families with GPU capabilities and lists their instance types.

## vgn5i, lightweight compute optimized instance family with GPU capabilities {#section_lip_fsm_g9e .section}

Features

-   I/O optimized
-   Supports standard SSDs and ultra disks
-   Uses NVIDIA P4 GPU computing accelerators
-   Contains virtual GPUs \(vGPUs\), which are the result of GPU virtualization with mediated pass-through
    -   Supports the 1/8, 1/4, 1/2, and 1/1 computing capacity of NVIDIA® Tesla® P4 GPUs
    -   Supports 1, 2, 4, and 8 GB of GPU memory
-   CPU-to-memory ratio of 1:3
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   AI \(deep learning and machine learning\) inference for the elastic deployment of Internet services
    -   Educational environment of deep learning
    -   Modeling experiment environment of deep learning

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|
|:------------|:----|:-------------|:--------------------|:--|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---|
|ecs.vgn5i-m1.large|2|6|N/A|P4\*1/8|1|1|300|Yes|2|2|
|ecs.vgn5i-m2.xlarge|4|12|N/A|P4\*1/4|2|2|500|Yes|2|3|
|ecs.vgn5i-m4.2xlarge|8|24|N/A|P4 \* 1/2|4|3|800|Yes|2|4|
|ecs.vgn5i-m8.4xlarge|16|48|N/A|P4\*1|8|5|1,000|Yes|4|5|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

## gn6i, compute optimized instance family with GPU capabilities {#section_e88_tau_vwf .section}

Features

-   I/O optimized
-   CPU-to-memory ratio of 1:4
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors
-   Supports standard SSDs, ultra disks, and enhanced SSDs that deliver millions of IOPS
-   Achieves better performance with the new-generation X-Dragon compute architecture
-   Uses NVIDIA T4 GPU computing accelerators
    -   Powered by the new NVIDIA Turing architecture
    -   Up to 320 Turing Tensor Cores
    -   Up to 2,560 CUDA Cores
    -   Mixed-precision Tensor Cores support 65 FP16 TFLOPS, 130 INT8 TOPS, and 260 INT4 TOPS
    -   16 GB memory capacity \(320 GB/s bandwidth\)
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   AI \(deep learning and machine learning\) inference for computer vision, voice recognition, speech synthesis, natural language processing, machine translation, and reference systems
    -   Real-time rendering for cloud gaming
    -   Real-time rendering for AR and VR applications
    -   Reload graphics computing or Graphics Workstation
    -   GPU-accelerated databases
    -   High-performance computing

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|
|:------------|:----|:-------------|:--------------------|:--|:----------------|--------------------|:------------------------------|:-----------|:---------|:---|
|ecs.gn6i-c4g1.xlarge|4|15|N/A|T4\*1|16|4|500|Yes|2|2|
|ecs.gn6i-c8g1.2xlarge|8|31|N/A|T4\*1|16|5|800|Yes|2|2|
|ecs.gn6i-c16g1.4xlarge|16|62|N/A|T4\*1|16|6|1,000|Yes|4|3|
|ecs.gn6i-c24g1.6xlarge|24|93|N/A|T4\*1|16|7.5|1,200|Yes|6|4|
|ecs.gn6i-c24g1.12xlarge|48|186|N/A|T4\*2|32|15|2,400|Yes|12|6|
|ecs.gn6i-c24g1.24xlarge|96|372|N/A|T4\*4|64|30|4,800|Yes|24|8|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

## gn6v, compute optimized instance family with GPU capabilities {#section_698_e4v_7rh .section}

Features

-   I/O optimized
-   Supports enhanced SSDs, standard SSDs, and ultra disks.
-   Uses NVIDIA V100 GPU processors
-   CPU-to-memory ratio of 1:4
-   Equipped with 2.5 GHz Intel ® Xeon ® Platinum 8163 \(Skylake\) processors
-   Uses NVIDIA V100 GPU computing accelerators \(SXM2-based\)
    -   Powered by the innovative NVIDIA Volta architecture
    -   16 GB HBM2 GPU memory
    -   5,120 CUDA Cores
    -   640 Tensor Cores
    -   Memory bandwidth of 900 GB/s
    -   Supports up to six NVLink connections for a total bandwidth of 300 GB/s with 25 GB/s each
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   Deep learning, image classification, autonomous vehicles, voice recognition, and other AI applications
    -   Scientific computing applications, such as fluid dynamics, finance, molecular dynamics, and environmental analysis

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|Private IP address of a single ENI|
|:------------|:----|:-------------|:--------------------|:--|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---|----------------------------------|
|ecs.gn6v-c8g1.2xlarge|8|32.0|N/A|1 \* NVIDIA V100|1 \* 16|2.5|800|Yes|4|4|10|
|ecs.gn6v-c8g1.8xlarge|32|128.0|N/A|4 \* NVIDIA V100|4 \* 16|10.0|2,000|Yes|8|8|20|
|ecs.gn6v-c8g1.16xlarge|64|256.0|N/A|8 \* NVIDIA V100|8 \* 16|20.0|2,500|Yes|16|8|20|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

## gn5, compute optimized instance family with GPU capabilities {#section_8ir_i5x_nvl .section}

Features

-   I/O optimized
-   Supports standard SSDs and ultra disks
-   Uses NVIDIA P100 GPU processors
-   Multiple CPU-to-memory ratios
-   High-performance local NVMe SSDs
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing applications, such as fluid dynamics, finance, genomics, and environmental analysis
    -   High-performance computing, rendering, multimedia encoding and decoding, and other server-side GPU compute workloads

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|Private IP address of a single ENI|
|:------------|:----|:-------------|:--------------------|:--|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---|----------------------------------|
|ecs.gn5-c4g1.xlarge|4|30.0|440|1 \* NVIDIA P100|1 \* 16|3.0|300|No|1|3|10|
|ecs.gn5-c8g1.2xlarge|8|60.0|440|1 \* NVIDIA P100|1 \* 16|3.0|400|No|1|4|10|
|ecs.gn5-c4g1.2xlarge|8|60.0|880|2 \* NVIDIA P100|2 \* 16|5.0|1,000|No|2|4|10|
|ecs.gn5-c8g1.4xlarge|16|120.0|880|2 \* NVIDIA P100|2 \* 16|5.0|1,000|No|4|8|20|
|ecs.gn5-c28g1.7xlarge|28|112.0|440|1 \* NVIDIA P100|1 \* 16|5.0|1,000|No|8|8|20|
|ecs.gn5-c8g1.8xlarge|32|240.0|1,760|4 \* NVIDIA P100|4 \* 16|10.0|2,000|No|8|8|20|
|ecs.gn5-c28g1.14xlarge|56|224.0|880|2 \* NVIDIA P100|2 \* 16|10.0|2,000|No|14|8|20|
|ecs.gn5-c8g1.14xlarge|54|480.0|3,520|8 \* NVIDIA P100|8 \* 16|25.0|4,000|No|14|8|20|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

## gn5i, compute optimized instance family with GPU capabilities {#section_ye9_eyj_ek2 .section}

Features

-   I/O optimized
-   Supports standard SSDs and ultra disks
-   Uses NVIDIA P4 GPU processors
-   CPU-to-memory ratio of 1:4
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   Deep learning inference
    -   Multimedia encoding and decoding, and other server-side GPU compute workloads

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|Private IP address of a single ENI|
|:------------|:----|:-------------|:--------------------|:--|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---|----------------------------------|
|ecs.gn5i-c2g1.large|2|8.0|N/A|1 \* NVIDIA P4|1 \* 8|1.0|100|Yes|2|2|6|
|ecs.gn5i-c4g1.xlarge|4|16.0|N/A|1 \* NVIDIA P4|1 \* 8|1.5|200|Yes|2|3|10|
|ecs.gn5i-c8g1.2xlarge|8|32.0|N/A|1 \* NVIDIA P4|1 \* 8|2.0|400|Yes|4|4|10|
|ecs.gn5i-c16g1.4xlarge|16|64.0|N/A|1 \* NVIDIA P4|1 \* 8|3.0|800|Yes|4|8|20|
|ecs.gn5i-c16g1.8xlarge|32|128.0|N/A|2 \* NVIDIA P4|2 \* 8|6.0|1,200|Yes|8|8|20|
|ecs.gn5i-c28g1.14xlarge|56|224.0|N/A|2 \* NVIDIA P4|2 \* 8|10.0|2,000|Yes|14|8|20|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

## gn4, compute optimized family with GPU capabilities {#section_u3g_2nm_wr4 .section}

Features

-   I/O optimized
-   Supports standard SSDs and ultra disks
-   Uses NVIDIA M40 GPU processors
-   Multiple CPU-to-memory ratios
-   Equipped with 2.5 GHz Intel ® Xeon ® E5-2682 v4 \(Broadwell\) processors
-   Provides strong network performance with large computing capacity
-   Suitable for the following scenarios:
    -   Deep learning
    -   Scientific computing applications, such as fluid dynamics, finance, genomics, and environmental analysis
    -   High-performance computing, rendering, multimedia encoding and decoding, and other server-side GPU compute workloads

Instance types

|Instance type|vCPUs|Memory \(GiB\)|Local storage \(GiB\)|GPU|GPU memory \(GB\)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Kpps\)|IPv6 support|NIC queues|ENIs|Private IP address of a single ENI|
|:------------|:----|:-------------|:--------------------|:--|:----------------|:-------------------|:------------------------------|:-----------|:---------|:---|----------------------------------|
|ecs.gn4-c4g1.xlarge|4|30.0|N/A|1 \* NVIDIA M40|1 \* 12|3.0|300|No|1|3|10|
|ecs.gn4-c8g1.2xlarge|8|30.0|N/A|1 \* NVIDIA M40|1 \* 12|3.0|400|No|1|4|10|
|ecs.gn4.8xlarge|32|48.0|N/A|1 \* NVIDIA M40|1 \* 12|6.0|800|No|3|8|20|
|ecs.gn4-c4g1.2xlarge|8|60.0|N/A|2 \* NVIDIA M40|2 \* 12|5.0|500|No|1|4|10|
|ecs.gn4-c8g1.4xlarge|16|60.0|N/A|2 \* NVIDIA M40|2 \* 12|5.0|500|No|1|8|20|
|ecs.gn4.14xlarge|56|96.0|N/A|2 \* NVIDIA M40|2 \* 12|10.0|1,200|No|4|8|20|

**Note:** 

-   You can go to the [ECS Instance Types Available for Each Region page](https://ecs-buy4service.aliyun.com/instanceTypes/#/instanceTypeByRegion) to view the instance types available in each region.
-   For more information about these specifications, see [Instance specification metrics](reseller.en-US/Instances/Instance families.md#section_e9r_xkf_z15).

