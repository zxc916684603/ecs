# Limits {#concept_gvb_h1w_tdb .concept}

This topic describes service limits of ECS and how to request exceptions to the limits.

## Overview {#section_nxc_2zs_2gb .section}

ECS has the following service limits:

-   ECS does not allow you to install virtualization software, such as VMware Workstation, or use it for re-virtualization. Only [ECS Bare Metal Instances](reseller.en-US/Instances/Instance type families/ECS bare metal instance type family/What is an ECS Bare Metal Instance?.md#) and [Super Computing Clusters](../../../../reseller.en-US/Instances/Instance type families/Super Computing Cluster instance type family/What is a Super Computing Cluster?.md#) support re-virtualization.
-   ECS does not support sound card applications.
-   External hardware devices, such as hardware dongles, USB flash drives, external hard disks, and hardware tokens, cannot be attached. Software verification methods such as two-factor authentication and dynamic passwords can be used.
-   ECS does not support IP address translation services such as SNAT. Instead, it achieves this function by using VPNs and proxies.
-   ECS does not support multicast protocols. We recommend that you use unicast instead.
-   Log Service does not support 32-bit Linux ECS instances. For information about regions that support Log Service, see [Service endpoint](../../../../reseller.en-US/API Reference/Service endpoint.md#). For information about operating systems that support Log Service, see the [Overview](../../../../reseller.en-US/Data Collection/Logtail collection/Overview/Overview.md#) section about Logtail collection.

## View quotas {#section_thb_aai_kpr .section}

On the Overview page of the ECS console, click **Privileges & Quotas** and select a region to view the resource quotas in that region. If the quota of a resource cannot meet your needs, submit a ticket to request an increase for the quota. For more information, see [Manage privileges and quotas](../../../../reseller.en-US/Tags & Resource Management /Manage privileges and quotas.md#). You can also view resource quotas by calling an API operation. For more information, see [DescribeAccountAttributes](../../../../reseller.en-US/API Reference/Others/DescribeAccountAttributes.md#).

## Instance limits {#section_tbg_zdx_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Permissions to create instances|To create ECS instances in any Mainland China regions, you must first complete real-name authentication.|No exceptions|
|Instance types for which you can create pay-as-you-go instances|Instance types with less than 16 vCPUs.|Submit a ticket|
|Total number of vCPUs of pay-as-you-go instances in each region for an account|50 vCPUs.|Submit a ticket|
|Total number of vCPUs of preemptible instances in each region for an account|0 vCPUs. You can submit a ticket to request the quota of 50 vCPUs.|Submit a ticket|
|Total number of launch templates in each region for an account|30.|No exceptions|
|Total number of versions of a launch template|30.|No exceptions|
|Switch from pay-as-you-go to subscription|Not supported by the following instance types \(families\): t1, s1, s2, s3, c1, c2, m1, m2, n1, n2, and e3.|No exceptions|
|Switch from subscription to pay-as-you-go| -   Whether this feature is supported depends on your ECS instance resource usage.
-   5,000 vCPU hours each month.
-   A maximum monthly refund limit is set. For more information about the refund limit, see the Switch to Pay-As-You-Go page.

 |No exceptions|

## Block Storage limits {#section_xlb_32x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Permissions to create pay-as-you-go disks|Complete [real-name authentication](https://www.alibabacloud.com/help/doc-detail/52595.htm) before creating disks in any Mainland China regions.|No exceptions|
|Total number of all pay-as-you-go disks in all regions for an account|Number of pay-as-you-go instances in all regions for an account × 5. Each account can create at least 10 pay-as-you-go disks.|Submit a ticket|
|Total number of system disks for each instance|1.|No exceptions|
|Maximum number of data disks for an instance|16 \(including disks and Shared Block Storage devices\).|No exceptions|
|Number of instances to which a Shared Block Storage device can be attached|8.|No exceptions|
|Total number of Shared Block Storage devices in all regions for an account|10.|Submit a ticket|
|Capacity of a basic disk|5 GiB to 2,000 GiB.|No exceptions|
|Capacity of an SSD|20 GiB to 32,768 GiB.|No exceptions|
|Capacity of an ultra disk|20 GiB to 32,768 GiB.|No exceptions|
|Capacity of a local SSD|5 GiB to 800 GiB.|No exceptions|
|Total capacity of all local SSDs for an instance|1,024 GiB.|No exceptions|
|Capacity of a local NVMe SSD|1,456 GiB.|No exceptions|
|Total capacity of all local NVMe SSDs for an instance|2,912 GiB.|No exceptions|
|Capacity of a local SATA HDD|5,500 GiB.|No exceptions|
|Total capacity of all local SATA HDDs for an instance|154,000 GiB.|No exceptions|
|Capacity of an SSD Shared Block Storage device|32,768 GiB.|No exceptions|
|Total capacity of all SSD Shared Block Storage devices for an instance|128 TiB.|No exceptions|
|Capacity of an ultra Shared Block Storage device|32,768 GiB.|No exceptions|
|Total capacity of all ultra Shared Block Storage devices for an instance|128 TiB.|No exceptions|
|Capacity of an enhanced SSD|32,768 GiB.|No exceptions|
|Capacity of a system disk| -   Windows: 40 GiB to 500 GiB.
-   Linux \(excluding CoreOS\) and FreeBSD: 20 GiB to 500 GiB.
-   CoreOS: 30 GiB to 500 GiB.

 |No exceptions|
|Capacity of a data disk| -   Basic disk: 5 GiB to 2,000 GiB.
-   SSD, ultra disk, SSD Shared Block Storage device, or ultra Shared Block Storage device: 20 GiB to 32,768 GiB.
-   Local disk: dependent on specific disks.

 |No exceptions|
|Attach new local disks to instances that have local disks|Not supported.|No exceptions|
|Change the specifications of instances that have local disks|Only bandwidth can be changed.|No exceptions|
|System disk mount points|/dev/xvda.|No exceptions|
|Data disk mount points|/dev/xvd\[b-z\].|No exceptions|

**Note:** Block storage capacity is measured in binary units. 1 KiB equals 1,024 Bytes. 1 GiB equals 1,024 MiB.

## Snapshot limits {#section_bxk_n2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Number of snapshots that can be created for each disk and Shared Block Storage device|64|No exceptions|
|Number of automatic snapshot policies that can be created in a region for an account|100|No exceptions|

## Image limits {#section_jnw_r2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of custom images in each region for an account|100.|Submit a ticket|
|Maximum number of users with whom an image can be shared|50.|Submit a ticket|
|Images supported by instance types|Instance types that have 4 GiB or more memory do not support 32-bit images.|No exceptions|

## SSH key pair limits {#section_dxw_s2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of SSH key pairs in each region for an account|500|No exceptions|
|Instance types supporting SSH key pairs|All instance types except non-I/O optimized instance types in Generation I|No exceptions|
|Images supporting SSH key pairs|Linux images only|No exceptions|

## Public bandwidth limits {#section_og5_t2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Maximum inbound public bandwidth|200 Mbit/s.|No exceptions|
|Maximum outbound public bandwidth| -   Subscription: up to 200 Mbit/s.
-   Pay-as-you-go: up to 100 Mbit/s.

 |No exceptions|
|Change the assigned public IP address for an instance|Public IP addresses can be changed within six hours after the instance is created, and can be changed a maximum of three times.|No exceptions|

## Security group limits {#section_mzr_52x_wdb .section}

|Item|Limit on basic security groups|Limit on advanced security groups|
|----|------------------------------|---------------------------------|
|Total number of security groups in each region for an account|100.|Same as that on basic security groups.|
|Number of classic network-type ECS instances that can be added to a classic network-type security group|1,000.[\*](#)|Classic network is not supported.|
|Number of VPC-type ECS instances that can be added to a VPC-type security group|Depends on the [number of private IP addresses in a VPC-type security group](#).|No limit.|
|Number of security groups that can contain the same ECS instance|5. You can submit a ticket to raise the limit to 10 or 16 security groups.

 |Same as that on basic security groups.|
|Number of security groups that can contain the same ENI of an ECS instance|
|Maximum number of rules \(both inbound and outbound\) in a security group|100.[\*\*\*](#)|Same as that on basic security groups.|
|Maximum number of rules \(both inbound and outbound\) in all security groups that contain the same ENI|500.|Same as that on basic security groups.|
|Number of private IP addresses in a VPC-type security group|2,000.[\*\*](#)|No limit.|
|Number of ENIs in a VPC-type security group|Depends on the [maximum number of rules in a security group](#).|50,000.|
|Public network access port|The default STMP port for outbound traffic is port 25, which is disabled by default. It cannot be enabled by security group rules.|Same as that on basic security groups.|

\* If more than 1,000 classic network-type instances need access to each other, you can distribute them across multiple security groups and authorize mutual access.

\*\* If you require mutual access among more than 2,000 private IP addresses, you can distribute them across multiple security groups and authorize mutual access.

\*\*\* If you increase the number of security groups that can contain the same ECS instance, the maximum number of rules in a security group will decrease. The product of the number of security groups that can contain the same ECS instance and the maximum number of rules \(both inbound and outbound\) in a security group must be less than or equal to 500. For example, 5 × 100 = 500, 10 × 50 = 500, and 16 × 30 < 500.

## Deployment set limits {#section_wcf_hbs_2fb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of deployment sets in each region for an account|2.|No exceptions|
|Total number of instances that can be included in a deployment set|Seven instances are allowed in a zone. The maximum number of instances allowed in a region is 7 × number of zones.|No exceptions|
|Instance types that can be created in a deployment set|c5, g5, hfc5, hfg5, r5, se1ne, sn1ne, and sn2ne.|No exceptions|

## Cloud Assistant limits {#section_qkq_mzs_2gb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of Cloud Assistant commands in each region for an account|100|Submit a ticket|
|Total number of Cloud Assistant commands that can be used by an account each day in a region|5,000|Submit a ticket|

## ENI limits {#section_gfq_v2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of ENIs in each region for an account|100|Submit a ticket|

## Tag limits {#section_npm_w2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of tags that can be bound to an instance|20|No exceptions|

## API limits {#section_glg_x2x_wdb .section}

|Item|Limit|Request an exception to a limit|
|:---|:----|:------------------------------|
|Total number of CreateInstance calls|200 calls per minute|Submit a ticket|

**Note:** For more information about the VPC limits, see [Limits](../../../../reseller.en-US/Product Introduction/Limits.md#).

