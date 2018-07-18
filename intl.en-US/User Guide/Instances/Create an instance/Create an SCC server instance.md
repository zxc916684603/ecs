# Create an SCC server instance {#concept_vrp_mr1_ydb .concept}

Super Computing Clusters \(SCC\) are currently available by invitation. You must [apply](https://page-intl.aliyun.com/form/scc_internet/index.htm)to use them.

## About Super Computing Clusters \(SCC\)  {#section_g2m_pr1_ydb .section}

SCC are based on ECS Bare Metal \(EBM\) Instances. With the help of the high-speed interconnectivity of RDMA \(Remote Direct Memory Access\) technology,  SCC greatly improve network performance and increase the acceleration ratio of large-scale clusters.  Therefore, SCC have all the advantages of EBM Instances and they can provide high-quality network performance featuring high bandwidth and low latency. For more information, see [ECS Bare Metal Instance and Super Computing Clusters](../../../../intl.en-US/Product Introduction/Instance/ECS Bare Metal Instance and Super Computing Clusters.md#).

Refer to the [Super Computing Cluster \(SCC\) instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#sccg5) for detailed instance specification information.

## Creating an instance {#section_h2m_pr1_ydb .section}

You can refer to the description of [Create an ECS instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#) to create an SCC server instance. You must consider the following when creating an SCC instance:

-   **Region**: Currently, only **China East 2 \(Shanghai\)**, **Zone D** provides SCC instances.
-   **Network**: Only VPC supports SCC.
-   **Instance type**: Currently, only the scch5 type family is available. For more information about instance types, see Instance type families.
-   **Image**: When your account is authorized to create an SCC instance, Alibaba Cloud ECS shares some images with you. Only those images are valid. Therefore, click **Shared Image** and select the image.  Only CentOS 7.4 is supported.
-   **Storage**: SCC support up to 16 data disks. You can add a data disk here, or you can [add a disk](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#) after the instance has been created, and [mount the data disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#). 

