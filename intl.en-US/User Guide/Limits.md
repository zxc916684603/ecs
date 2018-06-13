# Limits {#concept_gvb_h1w_tdb .concept}

When using ECS, consider the following:

-   ECS does not support virtual application installation or subsequent virtualization such as when using VMware.  Currently, only [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9553.md\#](../../../../intl.en-US/Product Introduction/Instance/ECS Bare Metal Instance and Super Computing Clusters.md#) supports virtualization.
-   ECS does not support sound card applications. 
-   ECS does not support the installation of external hardware devices such as hardware dongles, USB drives, external hard drives, and  the USB security keys issued by banks.
-   ECS does not support SNAT and other IP packet address translation services.  You can achieve this by using an external VPN or proxy.
-   ECS does not support multicast protocol.  If multicasting services are required, we recommend that you use unicast point-to-point method.
-   Currently, Log Service does not support 32-bit Linux ECS instance. To know the regions that support Log Service, see [Service endpoint](https://www.alibabacloud.com/help/doc-detail/29008.htm). See [../../../../dita-oss-bucket/SP\_7/DNSLS11850791/EN-US\_TP\_13054.md\#](../../../../intl.en-US/User Guide/Logtail collection/Overview.md#) to know the server operating systems that support Log Service.

Besides the preceding limit, the additional limits of ECS are mentioned in the following table.

## ECS instances {#section_tbg_zdx_wdb .section}

|Item|Limit |Supply for higher configuration or unlock configuration rights|
|:---|:-----|:-------------------------------------------------------------|
|Permission to create instances |Complete real-name registration to create ECS instances in the mainland China regions |Not supported|
|Default quota of Pay-As-You-Go ECS instances \(including spot instances\) in all regions for one account |10|Open a ticket|
|Launch templates in each region for one account |30|Not supported|
|Versions of one launch template |30|Not supported|
|Conversion of the billing method from Pay-As-You-Go to Subscription |Not supported in the following instance types or type families:-   Generation II: n1, ne2, and e3
-   All instance types of Generation I

|Not supported|
|Default available instance types for creating Pay-As-You-Go ECS instances \(New generation\) |ecs.t1.small \(1 vCPU core, 1 GiB\) |Open a ticket|
|ecs.s1.small \(1 vCPU core, 2 GiB\)|
|ecs.s1.medium \(1 vCPU core, 4 GiB\)|
|ecs.s2.small \(2 vCPU core, 2 GiB\)|
|ecs.s2.large \(2 vCPU core, 4 GiB\)|
|ecs.s2.xlarge \(2 vCPU core, 8 GiB\)|
|ecs.s3.medium \(4 vCPU core, 4 GiB\)|
|ecs.s3.large \(4 vCPU core, 8 GiB\)|
|ecs.m1.medium \(4 vCPU core, 16 GiB\)|
|Default available instance types for creating Pay-As-You-Go ECS instances \(Previous generation\) |ecs.n1.tiny \(1 vCPU core, 1 GiB\)|Open a ticket|
|ecs.n1.small \(1 vCPU core, 2 GiB\)|
|ecs.n1.medium \(2 vCPU core, 4 GiB\)|
|ecs.n1.large \(4 vCPU core, 8 GiB\)|
|ecs.n2.small \(1 vCPU core, 4 GiB\)|
|ecs.n2.medium \(4 vCPU core, 8 GiB\)|
|ecs.n2.large \(4 vCPU core, 16 GiB\)|
|ecs.e3.small \(1 vCPU core, 8 GiB\)|
|ecs.e3.medium \(2 vCPU core, 16 GiB\)|

## Block storage {#section_xlb_32x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Permission to create Pay-As-You-Go cloud disks |Complete [real-name registration](https://www.alibabacloud.com/help/zh/doc-detail/52595.htm) to create ECS instances in the mainland China regions |Not supported|
|Quota of Pay-As-You-Go cloud disks in all regions for one account |Five times of the number of Pay-As-You-Go instances in all regions under one account |Open a ticket|
|Quota of system disks for one ECS instance |1|Not supported|
|Quota of data disks for one ECS instance |16 \(including cloud disks and Shared Block Storage\) |Not supported|
|Multi-node attachment of shared block storage |16 instances. Four instances supported during public beta. |Not supported|
|Quota of shared block storage in all regions for one account |10|Open a ticket|
|Capacity of one Basic Cloud Disk |5 GiB ~ 2000 GiB|Not supported|
|Capacity of one SSD Cloud Disk |20 GiB ~ 32768 GiB|Not supported|
|Capacity of one Ultra Cloud disk |20 GiB ~ 32768 GiB|Not supported|
|Capacity of one ephemeral SSD disk |5 GiB ~ 800 GiB|Not supported|
|Capacity of ephemeral SSD disks on one ECS instance |1024 GiB|Not supported|
|Capacity of one NVMe SSD local disk |1456 GiB|Not supported|
|Capacity of NVMe SSD local disks on one ECS instance |2912 GiB|Not supported|
|Capacity of one SATA HDD local disk |5500 GiB|Not supported|
|Capacity of SATA HDD local disks on one ECS instance |154000 GiB|Not supported|
|Capacity of one SSD Shared Block Storage device |32768 GiB|Not supported|
|Capacity of SSD Shared Block Storage devices on one ECS instance |128 TiB|Not supported|
|Capacity of one Ultra Shared Block Storage device |32768 GiB|Not supported|
|Capacity of Ultra Shared Block Storage devices on one ECS instance |128 TiB|Not supported|
|Size limit of one system disk |Windows: 40 GiB − 500 GiB Linux \(excluding CoreOS\)+ FreeBSD: 20 GiB − 500 GiB CoreOS: 30 GiB − 500 GiB |Not supported|
|Size limit of one data disk |Basic Cloud Disk: 5 GiB − 2,000 GiB SSD Cloud Disk/Ultra Cloud Disk/SSD Shared Block Storage/Ultra Shared Block Storage: 20 GiB − 32,768 GiB Local disk: See Local disks|Not supported|
|Attaching an independent local disk to an ECS instance with local disks |Not supported |Not supported |
|Configuration changes of an ECS instance with local disks |Only changes to public network bandwidth are permitted |Not supported |
|Mount point for system disks |/dev/xvda|Not supported|
|Mount points for data disks |/dev/xvd\[b-z\]|Not supported|

## Snapshots {#section_bxk_n2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of snapshots |Number of elastic block storage devices \* 64 |Not supported|

## Images {#section_jnw_r2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of custom images in all regions for one account |100|Open a ticket|
|Quota of accounts to share one custom image |100|Open a ticket|
|Requirements of images for instance types |32-bit images are not supported on an instance with 4 GiB or more RAM. |Not supported|

## Key pairs {#section_dxw_s2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of key pairs in all regions for one account |500|Not supported|
|Instance types supporting key pairs |All instance types, except those non-I/O optimized instance types in Generation I |Not supported|
|Images supporting key pairs |Linux images only |Not supported|

## Security groups {#section_mzr_52x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of ECS instances for one security group |1000|Not supported|
|Quota of rules for one security groups |100|Not supported|
|Quota of security groups in all regions for one account | 100

 |Open a ticket|
|Quota of security groups for one ECS instances |5|Not supported|
|Port|Access to TCP Port 25, which is the default port for the STMP service, is denied. It cannot be allowed by adding a security group rule. |Open a ticket. For more information, see [Apply to open TCP port 25](https://www.alibabacloud.com/help/doc-detail/56130.htm)|

## ENI {#section_gfq_v2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of ENI in one region for one account | 100

 |Open a ticket|

## Tags {#section_npm_w2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Quota of tags for one ECS instance |10|Not supported|

## API {#section_glg_x2x_wdb .section}

|Item|Limit|Supply for higher configuration or unlock configuration rights|
|:---|:----|:-------------------------------------------------------------|
|Invocation quota of CreateInstance |At most 200 times per minute |Open a ticket|

**Note:** For more information about the limits for VPC, see [../../../../dita-oss-bucket/SP\_22/DNVPC11824082/EN-US\_TP\_2432.md\#](../../../../intl.en-US/VPC product introduction/Limits.md#).

