# ECS Bare Metal Instance and Super Computing Clusters {#concept_lnh_hv2_5db .concept}

ECS Bare Metal \(EBM\) Instance is a new type of computing product that features both elasticity of virtual machines and performance and characteristics of physical machines. As a product completely and independently developed by Alibaba Cloud, EBM Instances are based on the next-generation virtualization technology. Compared with the previous generation of virtualization technology, the next-generation virtualization technology with an innovative approach, not only supports the common virtual cloud server but also completely supports the nested virtualization technology. It retains the resource elasticity of common cloud servers and adopts nested virtualization technology such that it keeps the user experience of physical machines intact.

Super Computing Clusters \(SCC\) are based on EBM Instances. With the help of the high-speed interconnectivity of RDMA \(Remote Direct Memory Access\) technology, SCC greatly improve network performance and increase the acceleration ratio of large-scale clusters. Therefore, SCC have all the advantages of EBM Instances and offer high-quality network performance featuring high bandwidth and low latency.

## Advantages {#section_onk_y55_ydb .section}

**EBM Instances**

EBM Instances realize the value of customers by way of technological innovation. Specifically, EBM Instances have the following advantages:

-   **Exclusive computing resources**

    As a cloud-based elastic computing product, the EBM Instances outshine the performance and isolation of contemporary physical machine and enables exclusive computing resources without virtualization performance overheads and feature loss. EBM Instances support 8, 16, 32, and 96 CPU cores and ultrahigh frequency. Considering an EBM Instance with 8 cores as an example, it supports an ultrahigh frequency of up to 3.7 to 4.1 GHz, providing better performance and responsiveness for gaming and financial industries than similar products.

-   **Encrypted compute**

    For security, the EBM Instances use a chip-level trusted execution environment \(Intel® SGX\) in addition to the physical server isolation. This allows to compute only the encrypted data in a safe and trusted environment, and provides improved security for the customer data on the cloud. This chip-level hardware security protection provides a safe box for the data of cloud users and allows users to control all the data encryption and key protection procedures.

-   **Any Stack on Alibaba Cloud**

    An EBM Instance combines the performance strengths and complete features of physical machines and [the ease-of-use and cost-effectiveness of cloud servers](intl.en-US/Product Introduction/Benefits of ECS.md#). It can effectively meet your demands for high-performance computing and help you build new hybrid clouds. Thanks to the flexibility, elasticity, and all the other strengths it inherits from both virtual and physical machines, it is powered with re-virtualization ability. As a result, offline private clouds can be seamlessly migrated to Alibaba Cloud without any issues regarding performance overhead that may arise because of nested virtualization. This facilitates a new approach for you to move businesses onto the cloud.

-   **Heterogeneous instruction set processor support**

    The virtualization 2.0 technology used by EBM Instances is completely developed by Alibaba Cloud. It can zero-cost support ARM and other instruction set processors.


**SCC**

Alibaba Cloud also released Super Computing Clusters based on the EBM Instance to meet the demands for high performance computing, artificial intelligence, machine learning, scientific or engineering computing, data analysis, audio and video processing, and so on. In the cluster, nodes are connected by Remote Direct Memory Access \(RDMA\) networks featuring high bandwidth and low latency, guaranteeing the high parallel efficiency posed by applications that need high-performance computing. Meanwhile, the RoCE \(RDMA over Convergent Ethernet\) may rival an Infiniband network in terms of connection speed, and supports more extensive Ethernet-based applications. The combination of the SCC built on the EBM Instance and other Alibaba Cloud computing products such as the ECS and GPU servers provides [the Alibaba Cloud elastic high-performance computing \(E-HPC\) platform](https://www.alibabacloud.com/help/product/57664.htm) with ultimate high performance parallel computing resources, which makes supercomputing on the cloud a reality.

## Features {#section_efq_x55_ydb .section}

EBM Instances and SCC have the following features:

-   CPU specifications:

    -   EBM Instances: Supports 8 cores, 16 cores, 32 cores, and 96 cores, and supports high clock speed.
    -   SCC: Supports 64 cores and 96 cores, and provide support for high clock speed.
-   Memory specifications:

    -   EBM Instances: Supports 32 GiB to 768 GiB memory. To provide better computing performance, the ratio of CPU to memory is 1:2 or 1:4.
    -   SCC: The ratio of CPU to memory is 1:3 or 1:4.
-   Storage configuration: supports boot from Virtual Machine images and clouds for second-level delivery.

-   Network configurations:

    -   Supports Virtual Private Cloud \(VPC\) networks, maintaining interoperability with ECS, GPU cloud servers, and other cloud products. Delivers performance and stability comparable to physical machine networks.
    -   \(Only for SCC\) Supports RDMA communication through high-speed RoCE networks.
-   Images: Supports images of Alibaba Cloud ECS.

-   Security settings: Maintains the same security policies and flexibility as existing cloud server ECS instances.


The following table compares EBM Instance or SCC, physical servers, and virtual servers. Here, Y indicates “Support”, N indicates “Not Support”, and N/A indicates no data available or not applicable.

|Features|Features|EBM Instances/SCC|Physical servers|Virtual servers|
|:-------|:-------|:----------------|:---------------|:--------------|
|Automated O&M|Delivery in minutes|Y|N|Y|
|Computing|Zero performance loss|Y|Y|N|
|Zero feature loss|Y|Y|N|
|Zero resource competition|Y|Y|N|
|Storage| Fully compatible with ECS cloud disks|Y|N|Y|
|Start from cloud disks \(system disks\)|Y|N|Y|
|System disk can be quickly reset|Y|N|Y|
|Uses ECS images|Y|N|Y|
|Supports cold migration between physical and virtual servers|Y|N|Y|
|Requires no installation of operating system|Y|N|Y|
|Discards local RAID, and provides stronger protection of data on cloud disks|Y|N|Y|
|Network|Fully compatible with the ECS VPC networks|Y|N|Y|
|Fully compatible with the ECS classic networks|Y|N|Y|
|Free of bottlenecks for communications between physical and virtual server clusters in the VPC|Y|N|Y|
|Management|Fully compatible with the existing ECS management system|Y|N|Y|
|Consistent user experience on VNC and other features with that of virtual servers|Y|N|Y|
|Guaranteed OOB network security|Y|N|N/A|

## Instance type families {#section_ufq_x55_ydb .section}

The type families of EBM Instances include:

-   General purpose EBM Instance type families, including ebmg5 and ebmg4
-   High frequency EBM Instance type families, including ebmhfg5 and ebmhfg4
-   Compute EBM Instance type families, including ebmc4

The type families of SCC include scch5 and sccg5.

For specific information about type families, see [EBM Instance type families](intl.en-US/Product Introduction/Instance type families.md#ebmg5) and [SCC Instance type families](intl.en-US/Product Introduction/Instance type families.md#sccg5).

## Billing methods {#section_wfq_x55_ydb .section}

Currently, EBM Instances and SCC instances are billed on a monthly or yearly basis only. For more information about billing methods, see [Billing method comparison](../intl.en-US/Pricing/Billing method comparison.md#).

## Related operations {#section_xfq_x55_ydb .section}

You can [Create an EBM instance](../intl.en-US/User Guide/Instances/Create an instance/Create an EBM instance.md#) or [Create an SCC server instance](../intl.en-US/User Guide/Instances/Create an instance/Create an SCC server instance.md#).

For more information, see [FAQs about EBM Instances](https://www.alibabacloud.com/help/faq-detail/66558.htm).

