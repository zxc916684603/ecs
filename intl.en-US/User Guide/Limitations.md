# Limitations {#concept_gvb_h1w_tdb .concept}

When using ECS, consider the following:

-   ECS does not support virtual application installation or revirtualization such as installing VMware. Currently, only [ECS Bare Metal Instance and Super Computing Clusters](../../../../intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#) supports revirtualization.
-   Does not support sound card application.
-   It is not supported to mount external hardware devices directly \(such as hardware dongle, U disk, external hard disk, and bank U key\). You can try a software dongle or two-step verification with dynamic passwords.
-   ECS does not support IP packet address translation services such as SNAT. You can achieve this by using a VPN or proxy.
-   ECS does not support multicast protocols. If multicasting services are required, we recommend that you use point-to-point unicast instead.
-   Currently, Log Service does not support 32-bit Linux ECS instances. To learn about the regions that support Log Service, see [Service endpoint](https://www.alibabacloud.com/help/doc-detail/29008.htm). See [Overview](../../../../intl.en-US/User Guide/Logtail collection/Overview.md#) to learn about the server operating systems that support Log Service.

Besides the preceding limitations, the additional limitations of ECS are described in the following table.

## ECS instances {#section_tbg_zdx_wdb .section}

|Item|limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Permission to create instances|Complete real-name registration before creating ECS instances in the mainland China regions|Not supported|
|Instance types for which you can create Pay-As-You-Go instances|Instance types with less than 16 vCPUs|Open a ticket|
|Default quota of Pay-As-You-Go instances in each region for one account|50 vCPUs \(increases with membership levels\)|Open a ticket|
|Default quota of preemptible instances in each region for one account|You need to open a ticket to request the permission. Up to 50 vCPUs are allowed once the permission is granted. The quota increases with membership levels.|Open a ticket|
|Default quota of launch templates in each region for one account|30|Not supported|
|Default quota of versions of one launch template|30|Not supported|
|Switch from Pay-As-You-Go to Subscription|The following instance types \(families\) are not supported: t1, s1, s2, s3, c1, c2, m1, m2, n1, n2, e3|Not supported|

## Block storage {#section_xlb_32x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Create Pay-As-You-Go cloud disks|Complete [real-name registration](https://www.alibabacloud.com/help/doc-detail/52595.htm) before creating cloud disks in the mainland China regions|Not supported|
|Default quota of Pay-As-You-Go cloud disks in all regions for one account|Number of Pay-As-You-Go instances in all regions under the user account x 5|Open a ticket|
|Quota of system disks for one instance|1|Not supported|
|Quota of data disks for one instance|16 \(including cloud disks and Shared Block Storage\) |Not supported|
|Quota of instances to which one shared block storage can be attached|8|Not supported|
|Quota of shared block storage in all regions for one account |10|Open a ticket|
|Capacity of one Basic Cloud Disk|5 GiB ~ 2,000 GiB|Not supported|
|Capacity of one SSD Cloud Disk|20 GiB ~ 32,768 GiB|Not supported|
|Capacity of one Ultra Cloud disk |20 GiB ~ 32,768 GiB|Not supported|
|Capacity of one local SSD disk|5 GiB ~ 800 GiB|Not supported|
|Capacity of local SSD disks for one instance|1,024 GiB|Not supported|
|Capacity of one local NVMe SSD disk|1,456 GiB|Not supported|
|Capacity of local NVMe SSD disks for one instance|2,912 GiB|Not supported|
|Capacity of one local SATA HDD disk|5,500 GiB|Not supported|
|Capacity of local SATA HDD disks for one instance|154,000 GiB|Not supported|
|Capacity of one SSD Shared Block Storage|32,768 GiB|Not supported|
|Capacity of SSD Shared Block Storage for one instance|128 TiB|Not supported|
|Capacity of one Ultra Shared Block Storage|32,768 GiB|Not supported|
|Capacity of Ultra Shared Block Storage for one instance|128 TiB|Not supported|
|Capacity of one ESSD disk|32,768 GiB|Not supported|
|Capacity of one system disk| -   Windows: 40 GiB−500 GiB
-   Linux \(excluding CoreOS\) and FreeBSD: 20 GiB−500 GiB
-   CoreOS: 30 GiB−500 GiB

 |Not supported|
|Capacity of one data disk| -   Basic Cloud Disk: 5 GiB−2,000 GiB
-   SSD Cloud Disk/Ultra Cloud Disk/SSD Shared Block Storage/Ultra Shared Block Storage: 20 GiB−32,768 GiB
-   Local disk: The capacity depends on specific disks

 |Not supported|
|Attach a new local disk to an instance with local disks|Not supported|Not supported|
|Change configuration of an instance with local disks|Only bandwidth changes allowed|Not supported|
|System disk mount points|/dev/xvda|Not supported|
|Data disk mount points|/dev/xvd\[b-z\]|Not supported|

## Snapshots {#section_bxk_n2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of snapshots|Number of elastic block storage devices x 64|Not supported|

## Images {#section_jnw_r2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of custom images in all regions for one account|100 \(increases with membership levels\)|Submit a ticket|
|Maximum number of users with whom a single image can be shared|50|Submit a ticket|
|Usage of images on instance types|32-bit images are not supported on an instance with 4 GiB or more RAM.|Not supported|

## Key pairs {#section_dxw_s2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of key pairs in all regions for one account|500|Not supported|
|Instance types supporting key pairs|All instance types, except those non-I/O optimized instance types in Generation I|Not supported|
|Images supporting key pairs|Linux images only|Not supported|

## Internet bandwidth {#section_og5_t2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Maximum inbound Internet bandwidth|200 Mbit/s|Not supported|
|Maximum outbound Internet bandwidth|100 Mbit/s|Open a ticket to increase the limit to 200 Mbit/s|
|Change the assigned public IP address for one instance|The instance has existed for less than six hours. You can change the public IP address of an instance three times.|Not supported.|

## Security group {#section_mzr_52x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of instances/IP for one security group| -   Security groups for classic network instances: 1,000 classic network instances
-   Security groups for VPC instances: 2,000 private IP \(shared by primary and secondary network cards\)

 |Not supported|
|Quota of authorization rules for one security group|100|Not supported|
|Quota of security groups in a region for an account| 100 \(increases with membership levels\)

 |Open a ticket|
|Quota of security groups to which each elastic network interface belongs for one instance|5|Open a ticket|
|Port|For the outbound Internet traffic, the default STMP port is 25, which is disabled by default and cannot be enabled through security group rules.|Open a ticket to enable it. For more information, see [Request for enabling TCP port 25.](https://www.alibabacloud.com/help/doc-detail/56130.htm)|

## ENI {#section_gfq_v2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of ENIs in one region for one account| 100 \(increases with membership levels\)

 |Open a ticket|

## Label {#section_npm_w2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of tags that can be bound to one instance|20|Not supported|

## API {#section_glg_x2x_wdb .section}

|Item|Limitation|How to break the limitation|
|:---|:---------|:--------------------------|
|Quota of CreateInstance calls|At most 200 times per minute|Open a ticket|

**Note:** For more information about limitations of VPC products, see [Limits](../../../../intl.en-US/Product Introduction/Limits.md#).

