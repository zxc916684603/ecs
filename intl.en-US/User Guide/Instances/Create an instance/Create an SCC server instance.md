# Create an SCC server instance {#concept_vrp_mr1_ydb .concept}

An SCC is based on ECS Bare Metal \(EBM\) Instance. With the help of the high-speed interconnectivity of RDMA \(Remote Direct Memory Access\) technology, SCC greatly improves network performance and increases the acceleration ratio of large-scale clusters. Therefore, SCC has all the advantages of EBM Instances, and provides high-quality network performance featuring high bandwidth and low latency. For more information, see [ECS Bare Metal Instance and Super Computing Clusters](../../../../intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

This article describes some consideration when you create an SCC instance. For more information about creating an SCC instance, see [create an ECS instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).

You must consider the following when creating an SCC instance:

-   **Region**: Currently, only **Zone D** and **Zone B** of **China East 2 \(Shanghai\)** provide SCC instances.
-   **Instance Type**: The scch5 and sccg5 type families are available. For more information about instance types, see [instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#scch5).
-   **Image**: Select **Public Image**. Currently, only custom Linux CentOS 7.5 is supported.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9637/15362264055118_en-US.png)

-   **Storage**: SCC support up to 16 data disks. You can add a data disk during instance creation, or you can [add a disk](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#) after the instance is created, and then [mount the data disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#). 
-   **Network**: Only VPC is supported.

