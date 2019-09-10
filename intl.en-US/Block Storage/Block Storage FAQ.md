# Block Storage FAQ {#concept_40551_zh .concept}

-   Enhanced SSD FAQ
    -   [What is an enhanced SSD?](#section_exq_8tt_oqw)
    -   [When are enhanced SSDs available for purchase?](#section_hhd_okp_zlj)
    -   [What are the differences between the enhanced SSDs offered during and after the public preview?](#section_cw3_bmw_boh)
    -   [What are the similarities and differences among enhanced SSDs, standard SSDs, and ultra disks?](#section_amv_05u_7k0)
    -   [How is the performance level of an enhanced SSD measured?](#section_tn9_l2d_g0h)
    -   [How do I test the performance of an enhanced SSD and obtain the one million IOPS result?](#section_guq_54c_14o)
    -   [What is the relationship between the storage performance of an enhanced SSD and storage performance of the instance to which the enhanced SSD is attached?](#section_l0c_cer_qu7)
    -   [In which regions and zones are enhanced SSDs available?](#section_yq8_9fo_zgu)
    -   [To which instance families can enhanced SSDs be attached?](#section_br8_0h3_7d6)
-   Common FAQ
    -   [What must I consider when I select zones to create disks and then attach the disks to ECS instances?](#section_nks_1y2_gcr)
    -   [What are the common operations that can be performed on a disk?](#section_xs4_pdh_fhb)
    -   [What is I/O optimization? Can I upgrade an existing ECS instance to an I/O optimized instance?](#section_zxg_r7a_vdt)
-   Performance test FAQ
    -   [What tools can I use to test the performance of Block Storage?](#section_vyv_qlf_4rg)
    -   [Why does my instance shut down when I use the FIO tool to test I/O performance?](#section_gdt_ekx_3rp)
-   Standard SSD FAQ
    -   [What is the I/O performance of a standard SSD?](#section_f2w_rch_fhb)
    -   [What scenarios are suitable for standard SSDs?](#section_sf1_sch_fhb)
    -   [Can I replace a basic disk with a standard SSD?](#section_z0c_kiu_c6o)
    -   [Can I upgrade a standard SSD after I purchase it?](#section_n5t_cdh_fhb)
    -   [An error is reported when I attempt to attach a standard SSD to my I/O optimized Linux instance. Why?](#section_md2_ddh_fhb)
    -   [For Linux instances, what must I be aware of before I add mount information for a basic disk or a standard SSD?](#section_vjf_tos_b2o)
-   Shared Block Storage FAQ
    -   [What is Shared Block Storage?](#section_zjn_40o_nlh)
    -   [When can I purchase Shared Block Storage?](#section_idn_dlp_fhb)
    -   [What scenarios are suitable for Shared Block Storage?](#section_xcn_dlp_fhb)
    -   [Can I attach a Shared Block Storage device to ECS instances in different regions?](#section_adn_dlp_fhb)
    -   [How many Shared Block Storage devices can be attached to one ECS instance?](#section_bdn_dlp_fhb)
    -   [What are the specifications and performance of Shared Block Storage?](#section_cdn_dlp_fhb)
    -   [How do I test the performance of Shared Block Storage?](#section_frj_h4p_fhb)
-   FAQ about attaching and detaching disks
    -   [What is a device name \(mount point\)?](#section_c9t_aqp_8au)
    -   [What is an independent disk?](#section_lth_2jp_fhb)
    -   [Can I attach one disk to multiple ECS instances?](#section_g5g_b2r_fhb)
    -   [Do I need to partition and format a pay-as-you-go disk after I purchase it and attach it to an ECS instance?](#section_gps_gpr_fhb)
    -   [Why am I unable to find the data disk that I purchased for a Linux instance?](#section_7hm_z6c_ttx)
    -   [How many disks can be attached to one ECS instance?](#section_hl8_hn5_p3n)
    -   [Why am I unable to find my ECS instance when I attempt to attach a disk to it?](#section_ewk_3gr_fhb)
    -   [Can I attach a disk to an ECS instance that is in a different zone from the disk?](#section_izt_uhb_fxk)
    -   [Will data in my data disk be lost when I detach the disk?](#section_xzy_pnk_by6)
    -   [Can I detach a system disk?](#section_2my_ijk_gy1)
-   Independent disk FAQ
    -   [How is an independent pay-as-you-go data disk billed?](#section_v4m_b2r_fhb)
    -   [A disk that I created separately was attached to my ECS instance. Why was the disk released with the instance?](#section_bjw_8f4_ju1)
    -   [Can I attach an independent pay-as-you-go data disk to a subscription ECS instance?](#section_xtp_b2r_fhb)
    -   [Can I detach a data disk from a subscription ECS instance?](#section_tsb_3gr_fhb)
    -   [I have upgraded or downgraded an instance during renewal. Can I switch a subscription disk to a pay-as-you-go disk in the instance within the instance renewal period?](#section_nql_jnr_fhb)
-   Disk snapshot FAQ
    -   [When I delete a disk, will its snapshots also be deleted?](#section_a41_mgr_fhb)
    -   [Why are some automatic snapshots on my disk missing?](#section_jvf_shr_fhb)
    -   [Can I use a snapshot to create an independent disk?](#section_tz3_jnr_fhb)
-   FAQ about reinitializing disks
    -   [What can I do if I cannot access the data in a Linux data disk because an error occurred while attaching the data disk?](#section_fz4_jnr_fhb)
    -   [Are my snapshots retained if I reinitialize a disk?](#section_mx6_x6w_wn8)
    -   [What can I do if the data disk of my ECS Linux instance cannot be found after I restart the instance or reinitialize the system disk?](#section_eja_zx1_w6o)
    -   [How do I re-mount data disks after I reinitialize the system disk of my ECS Linux instance?](#section_vaw_x75_0rr)
-   FAQ about resizing disks
    -   [Are my snapshots retained if I replace a system disk?](#section_2u6_pq5_q3f)
    -   [What must I be aware of before I replace a system disk?](#section_pc0_x40_gh9)
    -   [How do I resize a system disk?](#section_wdn_d4r_fhb)
    -   [Can I scale down a system disk after I scale it up?](#section_iiz_k8i_vkr)
    -   [What Block Storage devices can be resized when they are used as system disks, and do any regional limits apply to this operation?](#section_cbz_pdh_fhb)
    -   [Can the system disks of both subscription ECS instances and pay-as-you-go ECS instances be resized?](#section_tjd_xqr_fhb)
    -   [What is the storage capacity range of a system disk?](#section_nx3_xqr_fhb)
    -   [I changed the specifications of my ECS instance when renewing it. Can I specify a new system disk capacity when I replace the system disk?](#section_k1m_xqr_fhb)
    -   [How I can use a temporary pay-as-you-go disk created from a snapshot of a data disk to resize the data disk without data loss?](#section_idx_soz_yoe)
    -   [What can I do if the error message "Bad magic number in super-block while trying to open /dev/xvdb1" is returned when I resize a disk of an ECS Linux instance?](#section_td6_w72_q3x)
-   Partition FAQ
    -   [Can I partition a data disk for data storage?](#section_ppz_43v_fhb)
    -   [For a disk with multiple partitions, are snapshots created for the entire disk or only for a specific partition?](#section_q5b_p3v_fhb)
    -   [What must I be aware of before I re-partition a disk?](#section_nx1_3mv_fhb)
-   FAQ about rolling back disks
    -   [I rolled back a data disk by using a snapshot after I re-partitioned the disk. How many partitions are available in the disk?](#section_nyd_3mv_fhb)
    -   [An error message similar to the following is returned when I attempt to roll back a disk: "A disk can be rolled back only when the associated instance has been stopped and the disk has no snapshots being created. If the operating system of an ECS instance has been replaced, the snapshot taken before the replacement cannot be used to roll back the system disk." What can I do?](#section_psz_3vy_ghb)
-   Other FAQ
    -   [How do I copy data across instances?](#section_i3j_nrv_fhb)
    -   [How do I test the performance of an enhanced SSD?](#ESSDperfor)

## What is an enhanced SSD? {#section_exq_8tt_oqw .section}

An enhanced SSD is an ultra-high performance disk provided by Alibaba Cloud. Enhanced SSDs use 25 GE networks and the remote direct memory access \(RDMA\) technology to deliver up to 1 million random IOPS with low one-way latency. For more information, see [ESSD cloud disk](reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#).

## When are enhanced SSDs available for purchase? {#section_hhd_okp_zlj .section}

Enhanced SSDs are commercially available since the end of June 2019. You can log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) or call the [CreateDisk](../reseller.en-US/API Reference/Disk/CreateDisk.md#) operation to create enhanced SSDs.

## What are the differences between the enhanced SSDs offered during and after the public preview? {#section_cw3_bmw_boh .section}

Different specifications of enhanced SSDs are offered during and after the public preview. The commercially available specifications are described in the following table.

For ESSD cloud disks, larger capacity positively corresponds with higher data-processing performance. The capacity, IOPS, and throughput provided by ESSD cloud disks vary depending on their performance levels. The specific capacity and performance are detailed in the following table.

|Performance level|Capacity \(GiB\)|Maximum IOPS|Maximum throughput \(Mbit/s\)|
|-----------------|----------------|------------|-----------------------------|
|PL1|20-32,768|50,000|350|
|PL2|461-32,768|100,000|750|
|PL3|1,261-32,768|1,000,000|4,000|

## What are the similarities and differences among enhanced SSDs, standard SSDs, and ultra disks? {#section_amv_05u_7k0 .section}

-   Similarities: These three types of disks are all based on a distributed Block Storage architecture, provide high reliability and scalability, and support snapshots and data encryption.
-   Differences: SSDs have the best performance of the three types of disks. For more information, see [ESSD cloud disk](reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#) and [Block storage performance](reseller.en-US/Block Storage/Block storage performance.md#).

## How is the performance level of an enhanced SSD measured? {#section_tn9_l2d_g0h .section}

The performance level of an enhanced SSD is proportional to its capacity. An enhanced SSD that has a larger capacity delivers higher performance. Compared with standard SSDs, enhanced SSDs have much better performance. For more information, see [ESSD cloud disk](reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#).

## How do I test the performance of an enhanced SSD and obtain the one million IOPS result? {#section_guq_54c_14o .section}

We recommend that you use the FIO tool to test the performance of enhanced SSDs. For more information, see [How do I test the performance of an enhanced SSD?](#).

## What is the relationship between the storage performance of an enhanced SSD and storage performance of the instance to which the enhanced SSD is attached? {#section_l0c_cer_qu7 .section}

Part of instance-level storage performance is proportional to the specifications that instance types have. The higher specifications an instance type has, the higher IOPS and throughput it can deliver.

For example, you created an ECS instance of storage optimized instance family g5se and attached enhanced SSDs to the instance:

-   If the total storage performance of the enhanced SSDs does not exceed the maximum storage performance that the instance type can deliver, the total storage performance of the enhanced SSDs takes precedence.
-   If the total storage performance of the enhanced SSDs exceeds the maximum storage performance that the instance type can deliver, the maximum storage performance that the instance type can deliver takes precedence.

    For example, you created a 16-GiB instance of the ecs.g5se.xlarge type that can deliver up to 60,000 IOPS. If you attach an enhanced SSD to the instance and the enhanced SSD has a capacity of 2 TiB with a maximum IOPS of 101,800, the maximum IOPS of the instance is 60,000, instead of 101,800.


The following table describes the performance and specifications of the g5se instance family.

|Instance type|vCPUs|Memory \(GiB\)|IOPS \(thousand\)|Throughput \(Mbit/s\)|
|:------------|:----|:-------------|:----------------|:--------------------|
|ecs.g5se.large|2|8|30|118|
|ecs.g5se.xlarge|4|16|60|235|
|ecs.g5se.2xlarge|8|32|120|470|
|ecs.g5se.4xlarge|16|64|230|900|
|ecs.g5se.6xlarge|24|96|340|1,350|
|ecs.g5se.8xlarge|32|128|450|1,800|
|ecs.g5se.16xlarge|64|256|900|3,600|
|ecs.g5se.18xlarge|70|336|1,000|4,000|

## In which regions and zones are enhanced SSDs available? {#section_yq8_9fo_zgu .section}

Enhanced SSDs are available in the following regions and zones:

-   China Hangzhou Zone H, Zone I, and Zone G
-   China Shanghai Zone E, Zone F, and Zone G
-   China Beijing Zone H, Zone G, and Zone F
-   China Zhangjiakou Zone A and Zone B
-   China Shenzhen Zone E and Zone D
-   China Chengdu Zone A
-   China Hongkong Zone C
-   India Mumbai B
-   UK London Zone B
-   Australia Sydney Zone B

## To which instance families can enhanced SSDs be attached? {#section_br8_0h3_7d6 .section}

Enhanced SSDs can be attached to instances from the instance families that support 25 GE networks \(g6, g5, ic5, c6, c5, r6, r5, and g5se\), ECS Bare Metal Instance families \(ebmhfg5, ebmc4, ebmg5, ebmgn6v, ebmgn6i, ebmc5s, ebmg5s, ebmr5s, and sccgn6\), and enterprise-level heterogeneous computing instance families \(vgn5i, gn6i, gn6v, gn5, gn5i, gn4, ga1, f1, and f3\).

## What tools can I use to test the performance of Block Storage? {#section_vyv_qlf_4rg .section}

For details, see [Block storage performance](reseller.en-US/Block Storage/Block storage performance.md#).

## Why does my instance shut down when I use the FIO tool to test I/O performance? {#section_gdt_ekx_3rp .section}

You can use the FIO tool to test I/O performance by bare disk partition or file system. However, if you test bare disk partitions, the metadata of file systems in the bare disk partitions may be damaged, leaving you unable to access the files in the partitions. This then causes the instance to shut down. This problem does not occur when you use the FIO tool to test I/O performance by file system.

## What must I consider when I select zones to create disks and then attach the disks to ECS instances? {#section_nks_1y2_gcr .section}

A pay-as-you-go disk can only be attached to an ECS instance in the same zone.

-   For high-availability applications, we recommend that you create data disks and attach them to ECS instances in different zones.
-   For low-latency applications, we recommend that you create data disks and attach them to ECS instances in the same zone.

## What are the common operations that can be performed on a disk? {#section_xs4_pdh_fhb .section}

The following topics describe the common operations that you can perform on a disk:

-   [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#)
-   [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#)
-   [Format a data disk for a Windows instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#)
-   [Detach a cloud disk](reseller.en-US/Block Storage/Block storage/Detach a cloud disk.md#)
-   [Reinitialize a cloud disk](reseller.en-US/Block Storage/Block storage/Reinitialize a cloud disk/Reinitialize a cloud disk.md#)
-   [Replace the system disk \(non-public image\)](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk (non-public image).md#)
-   [Replace the system disk by using a public image](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk by using a public image.md#)
-   [Resize cloud disks online](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks online.md#)
-   [Resize cloud disks offline](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks offline.md#)
-   [Resize partitions and file systems of Linux data disks](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize partitions and file systems of Linux data disks.md#)
-   [Extend a Windows file system](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Extend a Windows file system.md#)

## What is I/O optimization? Can I upgrade an existing ECS instance to an I/O optimized instance? {#section_zxg_r7a_vdt .section}

I/O optimization provides better storage performance for instances and disks. For example, you can optimize the storage performance of a standard SSD by attaching it to an I/O optimized instance.

You can call the [../DNA0011860945/EN-US\_TP\_9879.md\#](../reseller.en-US/API Reference/Instances/ModifyInstanceSpec.md#) or [../DNA0011860945/EN-US\_TP\_9880.md\#](../reseller.en-US/API Reference/Instances/ModifyPrepayInstanceSpec.md#) operation to upgrade your non-I/O optimized instances to I/O optimized instances.

## What is the I/O performance of a standard SSD? {#section_f2w_rch_fhb .section}

For details, see [Block storage performance](reseller.en-US/Block Storage/Block storage performance.md#).

## What scenarios are suitable for standard SSDs? {#section_sf1_sch_fhb .section}

Standard SSDs offer high performance and high reliability. They are applicable to I/O-intensive applications, such as MySQL, SQL Server, Oracle, PostgreSQL, and other small and medium-sized relational databases. They are also applicable to small and medium-sized development and testing environments.

## Can I replace a basic disk with a standard SSD? {#section_z0c_kiu_c6o .section}

No, standard SSDs cannot be used to replace basic disks, because standard SSDs use all-SSD storage media.

## Can I upgrade a standard SSD after I purchase it? {#section_n5t_cdh_fhb .section}

Yes, you can upgrade and resize it. For more information, see [Overview](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Overview.md#).

## An error is reported when I attempt to attach a standard SSD to my I/O optimized Linux instance. Why? {#section_md2_ddh_fhb .section}

In the Linux operating system, the mount point for a standard SSD is /dev/vd\*, and the mount point for a basic disk is /dev/xvd\*. If you specify the mount point in the format of /dev/xvd\* in a command to mount a standard SSD, an error occurs. Specify the mount point in the format of /dev/vd\* in the command to mount the standard SSD.

## For Linux instances, what must I be aware of before I add mount information for a basic disk or a standard SSD? {#section_vjf_tos_b2o .section}

When you attach a data disk to a Linux instance, you need to format and partition the disk. During this process, note that /dev/xvdb1 is the mount point for a basic disk, and /dev/vdb1 is the mount point for a standard or enhanced SSD. If you add invalid information, you will fail to mount the disk by using the `mount -a` command. To avoid this problem, perform the following steps:

1.  Run the `fdisk -l` command to view the data disk information.
2.  Check whether the information added to `/etc/fstab` is valid.

    **Note:** Do not add duplicate mount information because this will cause a system startup failure.

3.  Run the vim command to modify the `/etc/fstab` file.
4.  Comment out or delete invalid information, and add valid mount information.
5.  Run the `mount -a` command to check whether the disk is mounted.

For more information, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#).

## What is Shared Block Storage? {#section_zjn_40o_nlh .section}

Shared Block Storage is a block-level data storage service that features high concurrency, high performance, and high reliability. It supports concurrent reads from and writes to multiple ECS instances. For more information, see [Shared Block Storage](reseller.en-US/Block Storage/Shared Block Storage.md#).

Each Shared Block Storage device can be attached to a maximum of eight ECS instances in the same zone and region at the same time. If you want to attach a Shared Block Storage device to more than eight ECS instances, submit a ticket to raise the limit.

## When can I purchase Shared Block Storage? {#section_idn_dlp_fhb .section}

Shared Block Storage is under public preview. During the public preview, Shared Block Storage is provided for free in all regions. After the public preview ends, Shared Block Storage supports both the subscription and pay-as-you-go billing methods.

## What scenarios are suitable for Shared Block Storage? {#section_xcn_dlp_fhb .section}

The high availability architecture of Shared Block Storage is suitable for enterprise-level applications. It provides shared access to block storage devices in a shared-everything architecture, such as the high availability server cluster architecture and Oracle Real Application Clusters \(RAC\). Oracle RAC is common among government departments, enterprises, and financial customers.

## Can I attach a Shared Block Storage device to ECS instances in different regions? {#section_adn_dlp_fhb .section}

No, you can attach a Shared Block Storage device only to ECS instances in the same zone and region.

## How many Shared Block Storage devices can be attached to one ECS instance? {#section_bdn_dlp_fhb .section}

When used as data disks, Shared Block Storage devices share the data disk quota with disks. That is, a maximum of 16 data disks can be attached to an instance.

## What are the specifications and performance of Shared Block Storage? {#section_cdn_dlp_fhb .section}

Shared SSD Block Storage and Shared Ultra Block Storage are available. For more information about their specifications and performance, see [Block Storage performance](reseller.en-US/Block Storage/Block storage performance.md#).

## How do I test the performance of Shared Block Storage? {#section_frj_h4p_fhb .section}

You can use the FIO tool to perform the performance stress test. During the test, the total iodepth value of all clients cannot exceed 384. For example, if the test is conducted simultaneously on four instances, we recommend that the iodepth value of each client does not exceed 96.

-   When you perform the performance stress test on two ECS instances:
    -   Run the following command to test random write IOPS:

        ``` {#codeblock_di6_gcy_9vw}
        FIO -direct=1 -iodepth=128 -rw=randwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Write_Testing
        ```

    -   Run the following command to test random read IOPS:

        ``` {#codeblock_75c_f9v_e9r}
        FIO -direct=1 -iodepth=128 -rw=randread -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Read_Testing
        ```

    -   Run the following command to test write throughput:

        ``` {#codeblock_36h_qyz_h0p}
        FIO -direct=1 -iodepth=64 -rw=write -ioengine=libaio -bs=64k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Write_PPS_Testing
        ```

    -   Run the following command to test read throughput:

        ``` {#codeblock_dlp_2bd_28t}
        FIO -direct=1 -iodepth=64 -rw=read -ioengine=libaio -bs=64k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Read_PPS_Testing
        ```

-   When you perform the performance stress test on four ECS instances:
    -   Run the following command to test random write IOPS:

        ``` {#codeblock_oid_2cn_f0i}
        FIO -direct=1 -iodepth=96 -rw=randwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Write_Testing
        ```

    -   Run the following command to test random read IOPS:

        ``` {#codeblock_lbc_tiv_l7e}
        FIO -direct=1 -iodepth=96 -rw=randread -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Read_Testing
        ```

    -   Run the following command to test write throughput:

        ``` {#codeblock_fyz_ar7_4wq}
        FIO -direct=1 -iodepth=64 -rw=write -ioengine=libaio -bs=64k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Write_PPS_Testing
        ```

    -   Run the following command to test read throughput:

        ``` {#codeblock_o2r_hh2_13m}
        FIO -direct=1 -iodepth=64 -rw=read -ioengine=libaio -bs=64k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Read_PPS_Testing
        ```


## What is a device name \(mount point\)? {#section_c9t_aqp_8au .section}

A device name \(mount point\) is the location of an ECS disk on the disk controller bus. The selected device name matches the disk device number in Linux and matches the disk sequence number in the disk manager in Windows.

## What is an independent disk? {#section_lth_2jp_fhb .section}

An independent disk is a disk that you purchase separately. It can be attached to or detached from any ECS instance in the same zone. Before using an independent disk, you must attach it to an instance and partition and format the disk. For more information, see [Create a Pay-As-You-Go cloud disk](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a Pay-As-You-Go cloud disk.md#).

## Can I attach one disk to multiple ECS instances? {#section_g5g_b2r_fhb .section}

No, a disk can be attached only to one ECS instance in the same zone.

## Do I need to partition and format a pay-as-you-go disk after I purchase it and attach it to an ECS instance? {#section_gps_gpr_fhb .section}

If you purchase a pay-as-you-go disk separately, you must attach it to an ECS instance and then partition and format it. For more information, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#) and [Format a data disk for a Windows instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#).

## Why am I unable to find the data disk that I purchased for a Linux instance? {#section_7hm_z6c_ttx .section}

If you purchase a pay-as-you-go disk separately, you must attach it to an ECS Linux instance and then partition and format the disk before using it. For more information, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#) and [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).

## How many disks can be attached to one ECS instance? {#section_hl8_hn5_p3n .section}

When used as data disks, Shared Block Storage devices and disks share the data disk quota. That is, up to 16 data disks can be attached to one ECS instance.

## Why am I unable to find my ECS instance when I attempt to attach a disk to it? {#section_ewk_3gr_fhb .section}

Check whether your ECS instance has been released. If no, make sure that it is in the same zone and region as the disk.

## Can I attach a disk to an ECS instance that is in a different zone from the disk? {#section_izt_uhb_fxk .section}

No, you can attach a pay-as-you-go disk only to an ECS instance that is in the same zone as the disk.

## Will data in my data disk be lost when I detach the disk? {#section_xzy_pnk_by6 .section}

-   In Windows, we recommend that you stop the read and write operations on all file systems of the disk to ensure data integrity. Otherwise, the data being read or written will be lost.
-   In Linux, you must log on to the ECS instance and run the umount command on the disk. After the command is executed, log on to the ECS console to detach the disk.

## Can I detach a system disk? {#section_2my_ijk_gy1 .section}

No, you cannot detach a system disk but you can replace it. For more information, see [Replace the system disk \(non-public image\)](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk (non-public image).md#).

## How is an independent pay-as-you-go data disk billed? {#section_v4m_b2r_fhb .section}

A pay-as-you-go data disk is billed based on the space usage. Note that if your account balance is insufficient, the services of the data disk will be suspended.

## A disk that I created separately was attached to my ECS instance. Why was the disk released with the instance? {#section_bjw_8f4_ju1 .section}

This is because you have set the disk to be released along with the instance when you attach the disk to the instance. You can change this setting at any time in the ECS console or by calling the related API operation. For more information, see [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).

## Can I attach an independent pay-as-you-go data disk to a subscription ECS instance? {#section_xtp_b2r_fhb .section}

Yes.

## Can I detach a data disk from a subscription ECS instance? {#section_tsb_3gr_fhb .section}

No, you cannot detach a data disk from a subscription ECS instance. The data disk will be released along with the instance when the instance expires. If you want to release the data disk, switch it to a pay-as-you-go data disk, and then detach and release it. For information about how to switch the billing method of disks, see [Convert the billing methods of cloud disks](reseller.en-US/Block Storage/Block storage/Convert the billing methods of cloud disks.md#).

## I have upgraded or downgraded an instance during renewal. Can I switch a subscription disk to a pay-as-you-go disk in the instance within the instance renewal period? {#section_nql_jnr_fhb .section}

No, you can switch a subscription disk to a pay-as-you-go disk only after the instance renewal period.

## When I delete a disk, will its snapshots also be deleted? {#section_a41_mgr_fhb .section}

If you have enabled **Delete Automatic Snapshots While Releasing Disk**, the automatic snapshots of the disk will be deleted when you delete the disk. However, the manual snapshots are retained. You can change this setting at any time. For more information, see [Apply or disable an automatic snapshot policy](../reseller.en-US/Snapshots/Automatic snapshot policies/Apply or disable an automatic snapshot policy.md#).

## Why are some automatic snapshots on my disk missing? {#section_jvf_shr_fhb .section}

When the number of snapshots reaches the upper limit, the earliest automatic snapshot are automatically deleted but manual snapshots are not affected.

**Note:** The automatic snapshot policy that is applied to a disk can be executed only after the disk is attached to an instance.

## Can I use a snapshot to create an independent disk? {#section_tz3_jnr_fhb .section}

Yes, you can use an existing snapshot to create an independent pay-as-you-go disk. For more information, see [Create a cloud disk by using a snapshot](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a cloud disk by using a snapshot.md#).

## What can I do if I cannot access the data in a Linux data disk because an error occurred while attaching the data disk? {#section_fz4_jnr_fhb .section}

Perform these steps to fix the error:

1.  Find the data disk and check whether it is attached to the corresponding ECS ​​instance by using either of the following methods:
    -   Perform the check in the ECS console. For more information, see [Monitor a cloud disk](reseller.en-US/Block Storage/Block storage/Monitor a cloud disk.md#).
    -   Log on to the instance, and run the `fdisk -l`command to check whether the data disk partition information is correct. Run the `df -h` and `mount | grep "<devpath>"` commands to view the mount information.
2.  Run the cat command to view the /etc/fstab file and check whether you have mounted two disks to the same directory.
    -   If two disks are mounted to the same directory, the second disk will replace the first disk, which causes data to become inaccessible. We recommend that you mount either of the disks to a different directory.
    -   If they are mounted to different directories but the mount information shows that they are in the same directory, run the ll command to check whether a link exists between the two directories. If yes, we recommend that you run the mkdir command to create a new directory, and mount either of the disks to the new directory. Then check whether the data can be accessed.

## What can I do if data is lost after I restart my ECS Linux instance? {#section_xyy_bb8_gma .section}

-   Problem description: All data in a directory such as /alidata is lost after you restart your ECS Linux instance.
-   Cause: After you run the `df -h` command, the command output shows that no data disk partitions are mounted to the directory.
-   Solution: This solution uses an I/O optimized instance as an example. If your ECS instance is a non-I/O optimized instance, enter the device name of a disk partition in the format of /dev/xvd\*1 in the mount command.
    1.  Run the `fdisk -l` command to view the data disk partitions that are not mounted.
    2.  Run the `mount /dev/vdb1 /alidata` command to mount a data disk partition to the directory.
    3.  Run the `df -h` command to check whether the data disk partition is mounted to the directory.
    4.  \(Optional\) You can configure the disk partition to be automatically mounted during system startup in the /etc/fstab file to avoid this problem.

## Are my snapshots retained if I reinitialize a disk? {#section_mx6_x6w_wn8 .section}

Yes, both the manual snapshots and automatic snapshots of the disk will be retained.

## What can I do if the data disk of my ECS Linux instance cannot be found after I restart the instance or reinitialize the system disk? {#section_eja_zx1_w6o .section}

-   Problem description: After restarting an ECS Linux instance or reinitializing the system disk, you log on to the instance and run the `df -h` command. The command output shows that no data disks are found.
-   Cause:
    -   Restarting an instance: Mount information was not written to the /etc/fstab file when data disks were mounted. As a result, data disks are not automatically mounted after the instance restarts.
    -   Reinitializing the system disk: The /etc/fstab file is reset after the system disk is initialized. As a result, data disks are not automatically mounted during system startup.
-   Solution:
    1.  Run the `mount /dev/xvdb1` command to re-mount the original data disk partition of the instance.
    2.  Run the mount command to check the format of files in the /dev/xvdb1 partition.
    3.  Assume that the format of files in the /dev/xvdb1 partition is ext3. Run the following command to write the partition mount information to the /etc/fstab file:

        ``` {#codeblock_vhi_ujh_2b9}
        echo '/dev/xvdb1 /data ext3 defaults 0 0' >> /etc/fstab
        ```

    4.  Restart the instance in the ECS console.

## How do I re-mount data disks after I reinitialize the system disk of my ECS Linux instance? {#section_vaw_x75_0rr .section}

After you reinitialize the system disk of your ECS Linux instance, data in the data disks that are attached to the instance remains unchanged, but the mount information of the data disks is lost. As a result, all the data disks are unmounted. Assume that the mount point is /dev/vdb1, and the mount point is named /InitTest before the system disk is reinitialized. Run the following commands to re-mount data disk partition /dev/vdb1:

1.  Run the `mount` command to view the mount information of data disks.

    The command output does not contain information of /dev/vdb1.

2.  Run the `fdisk -l` command to view data disk partitions.
3.  Run the `cat /etc/fstab` command to view the original mount point name of /dev/vdb1.
4.  Run the `mkdir /InitTest` command to re-create the mount point for the data disk partition.

    The new mount point name must be the same as the original name of mount point /dev/vdb1.

5.  Run the `mount /dev/vdb1 /InitTest` command to re-mount the data disk partition.
6.  Run the `df -h` command to check whether the data disk partition is mounted.
7.  Perform the following steps to check whether /dev/vdb1 can be mounted automatically:
    1.  Run the `umount /dev/vdb1` command to unmount /dev/vdb1.
    2.  Run the `mount` command to check whether the partition is unmounted.

        If yes, the command output does not contain information of /dev/vdb1.

    3.  Run the `mount -a` command to automatically mount /dev/vdb1.
    4.  Run the `mount` command to check whether the partition is automatically mounted.

        If yes, the command output shows information of /dev/vdb1.


## Are my snapshots retained if I replace a system disk? {#section_2u6_pq5_q3f .section}

This depends on the creation method of snapshots. Manual snapshots will be retained, but automatic snapshots will be deleted if Delete Automatic Snapshots While Releasing Disk is enabled.

**Note:** After a system disk is replaced, the disk ID changes. You cannot use the snapshots of the original system disk to roll back the new system disk.

## What must I be aware of before I replace a system disk? {#section_pc0_x40_gh9 .section}

We recommend that you create snapshots of the current system disk before you replace it. Make sure that the current system disk has enough space available. The recommended available disk space is 1 GiB or larger. If disk space is insufficient, the instance may not start properly after you replace the system disk.

## How do I resize a system disk? {#section_wdn_d4r_fhb .section}

You can resize a system disk in the ECS console or by calling the [../DNA0011860945/EN-US\_TP\_9892.md\#](../reseller.en-US/API Reference/Disk/ResizeDisk.md#) operation.

## Can I scale down a system disk after I scale it up? {#section_iiz_k8i_vkr .section}

No, you cannot scale down a system disk after you scale it up. We recommend that you scale the system disk up properly.

## What Block Storage devices can be resized when they are used as system disks, and do any regional limits apply to this operation? {#section_cbz_pdh_fhb .section}

Ultra disks, standard SSDs, and enhanced SSDs can be resized when they are used as system disks. You can resize system disks in all regions.

## Can the system disks of both subscription ECS instances and pay-as-you-go ECS instances be resized? {#section_tjd_xqr_fhb .section}

Yes, the system disks of both subscription ECS instances and pay-as-you-go ECS instances can be resized.

## What is the storage capacity range of a system disk? {#section_nx3_xqr_fhb .section}

The capacity range of a system disk varies depending on the operating system. For more information, see [Overview](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Overview.md#).

## I changed the specifications of my ECS instance when renewing it. Can I specify a new system disk capacity when I replace the system disk? {#section_k1m_xqr_fhb .section}

After you perform the [Renew for configuration downgrade](../reseller.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#) operation on your ECS instance, you can resize the system disk of the instance only after the next billing cycle starts.

## How I can use a temporary pay-as-you-go disk created from a snapshot of a data disk to resize the data disk without data loss? {#section_idx_soz_yoe .section}

If a data disk cannot be resized without data loss due to a disk error, you can purchase a temporary pay-as-you-go disk to store data and then format the data disk. To do so, perform the following steps:

1.  Create a snapshot of the current data disk \(source data disk\). For more information, see [Create a snapshot](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#).
2.  Go to the disk purchase page. Select the same region and zone as the ECS instance to purchase a pay-as-you-go disk. Click **Create from Snapshot**. In the dialog box that appears, select the snapshot created in the previous step.
3.  Log on to the ECS console and then attach the new data disk you purchased to the ECS instance.
4.  Log on to the ECS instance and run the mount command to mount the new data disk. For more information about how to mount a disk created from a snapshot, see [Create a cloud disk by using a snapshot](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a cloud disk by using a snapshot.md#).
5.  Check whether files in the new data disk are the same as those in the source data disk.
6.  Run the fdisk command to delete the original partition table. Then run commands such as fdisk and mkfs.ext3 to re-partition and re-format the source data disk, resizing it to the target capacity. For more information, see [Resize partitions and file systems of Linux data disks](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize partitions and file systems of Linux data disks.md#).
7.  Run the cp -R command to copy all the data in the new data disk back to the source data disk.

    You can add the --preserve=all parameter to preserve the files' properties when copying the files.

8.  Run the umount command to unmount the new data disk.
9.  Log on to the ECS console, detach the new data disk from the ECS instance, and release the disk.

## What can I do if the error message "Bad magic number in super-block while trying to open /dev/xvdb1" is returned when I resize a disk of an ECS Linux instance? {#section_td6_w72_q3x .section}

-   Problem description: When you run the `e2fsck -f /dev/xvdb` command to resize a disk of an ECS Linux instance, the error message "Bad magic number in super-block while trying to open /dev/xvdb1" is returned.
-   Cause: The disk to be resized is not partitioned.
-   Solution: Run the `e2fsck -f /dev/xvdb` and `resize2fs /dev/xvdb` commands to resize the disk. Then run the mount command to mount the disk.

## Can I partition a data disk for data storage? {#section_ppz_43v_fhb .section}

Yes, you can divide a data disk into multiple partitions based on your needs. We recommend that you use the system tool for partitioning.

## For a disk with multiple partitions, are snapshots created for the entire disk or only for a specific partition? {#section_q5b_p3v_fhb .section}

Snapshots are created for the entire disk, instead of for a specific partition.

## What must I be aware of before I re-partition a disk? {#section_nx1_3mv_fhb .section}

To ensure data security, we recommend that you create a snapshot of a disk before re-partitioning the disk. This way, you can roll back the disk if an exception occurs. For more information, see [Create a snapshot](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) and [Roll back a disk by using a snapshot](../reseller.en-US/Snapshots/Use snapshots/Roll back a disk by using a snapshot.md#).

## I rolled back a data disk by using a snapshot after I re-partitioned the disk. How many partitions are available in the disk? {#section_nyd_3mv_fhb .section}

When you roll a data disk back by using a snapshot, the disk returns to the state it was in when the snapshot was taken. If the disk has not been re-partitioned at the time when the snapshot was taken, only one partition is available in the disk.

## An error message similar to the following is returned when I attempt to roll back a disk: "A disk can be rolled back only when the associated instance has been stopped and the disk has no snapshots being created. If the operating system of an ECS instance has been replaced, the snapshot taken before the replacement cannot be used to roll back the system disk." What can I do? {#section_psz_3vy_ghb .section}

-   Problem description: When you attempt to roll back a disk by using a snapshot, an error message similar to the following is returned: "A disk can be rolled back only when the associated instance has been stopped and the disk has no snapshots being created. If the operating system of an ECS instance has been replaced, the snapshot taken before the replacement cannot be used to roll back the system disk."
-   Cause: The problem may be caused by incorrect disk properties or disk states.
-   Solution: You can troubleshoot the problem based on the instance state or snapshot state.
    -   Check whether the instance to which the disk is attached has stopped.

        You can only roll back disks attached to instances in the stopped state. You can log on to the ECS console and check the state of the instance on the Instances page.

    -   Check whether the system disk of the instance associated with the snapshot has been replaced.

        After you select a new image for the instance, a new system disk will be automatically re-created from the new image for the instance and the system disk ID will change. Therefore, you cannot use the snapshots taken before the system disk is replaced to roll back the system disk. However, you can create a custom image from one of these snapshots and then use this image to replace the system disk of the instance. In this way, the instance returns to the state it was in when the snapshot was taken. For more information, see [Create a custom image by using a snapshot](../reseller.en-US/Images/Custom image/Create custom image/Create a custom image by using a snapshot.md#) and [Replace the system disk \(non-public image\)](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk (non-public image).md#).

    -   Check whether the disk to be rolled back has a snapshot being created.

        To ensure data consistency, do not roll back a disk that has a snapshot being created. You can go to the Instance Details page. Click Instance Snapshots in the left-side navigation pane to go to the **Snapshots** page. Check the states of snapshots. A snapshot is being created if the **Progress** value is not **100%** and the **Status** value is **Progressing**.

        If you need to forcibly terminate the creation process of a snapshot to roll back the disk, select the snapshot and click **Delete**.


## How do I copy data across instances? {#section_i3j_nrv_fhb .section}

You can choose data copy methods based on the operating system:

-   Copy data between Linux instances
    -   Use the lrzsz tool

        Log on to the Linux instances, install the lrzsz tool, run the rz command to upload files to one Linux instance, and run the sz command to download these files to the other Linux instance.

        You can also first run the sz command to download files to your local PC and then run the rz command to upload these files to the other Linux instance.

    -   Use the FTP tool

        If you use the SFTP tool, we recommend that you use the root account for instance logon and file upload and download.

    -   Use the wget command

        After compressing a file or a folder, save it to the web directory to generate a download URL. Then run the wget command on the other Linux instance to download the file or folder.

-   Copy data between a Linux instance and a Windows instance

    We recommend that you use the SFTP tool to download files from the Linux instance to your local PC and then use the FTP tool to upload the files to the Windows instance.

-   Copy data between Windows instances
    -   Use the FTP tool
    -   Use TradeManager

## How do I test the performance of an enhanced SSD? {#ESSDperfor .section}

This topic describes how to configure the environment to perform a performance stress test on an enhanced SSD and obtain the one million IOPS result. Note that the disk type and actual environment used will impact the test result.

**Warning:** You can obtain accurate test results by testing bare disk partitions. However, you may destroy the file system structure in a bare disk partitions if you test the partition directly. Before you perform such a test, you must [create a snapshot of the disk](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) to back up your data. We recommend that you use newly purchased ECS instances that contain no data for the test to prevent data loss.

We recommend that you use the latest versions of Linux images provided by Alibaba Cloud, such as CentOS 7.4 64-bit, CentOS 7.3 64-bit, CentOS 7.2 64-bit, and Aliyun Linux 17.1 64-bit. This is because the drivers provided by Linux images of earlier versions and Windows images may not be applicable to enhanced SSDs.

We also recommend that you use the [FIO](https://linux.die.net/man/1/fio) tool for the performance stress test.

This example describes how to test the random write \(randwrite\) performance of an enhanced SSD. Assume that the instance type is ecs.g5se.18xlarge and the device name of the enhanced SSD is /dev/vdb.

1.  Connect to the Linux instance.
2.  Run the following commands to install the libaio and FIO tools:

    ``` {#codeblock_244_8wb_x30}
    sudo yum install libaio –y
    sudo yum install libaio-devel –y
    sudo yum install fio -y
    ```

3.  Run the `cd /tmp` command to switch to the /tmp directory.
4.  Run the `vim test100w.sh` command to create script test100w.sh and paste the following code to the script to test the random write \(randwrite\) IOPS.

    ``` {#test100w.sh}
    function RunFio
    {
     numjobs=$1  # The number of the threads to be tested. In this example, the value is 8.
     iodepth=$2  # The maximum number of concurrent I/O requests. In this example, the value is 64.
     bs=$3       # The size of the data block per I/O. In this example, the value is 4k.
     rw=$4       # The read and write policy. In this example, the value is randwrite.
     filename=$5 # The name of the file to be tested. In this example, the value is /dev/vdb.
     nr_cpus=`cat /proc/cpuinfo |grep "processor" |wc -l`
     if [ $nr_cpus -lt $numjobs ];then
         echo “Numjobs is more than cpu cores, exit!”
         exit -1
     fi
     let nu=$numjobs+1
     cpulist=""
     for ((i=1;i<10;i++))
     do
         list=`cat /sys/block/vdb/mq/*/cpu_list | awk '{if(i<=NF) print $i;}' i="$i" | tr -d ',' | tr '\n' ','`
         if [ -z $list ];then
             break
         fi
         cpulist=${cpulist}${list}
     done
     spincpu=`echo $cpulist | cut -d ',' -f 2-${nu}`
     echo $spincpu
     fio --ioengine=libaio --runtime=30s --numjobs=${numjobs} --iodepth=${iodepth} --bs=${bs} --rw=${rw} --filename=${filename} --time_based=1 --direct=1 --name=test --group_reporting --cpus_allowed=$spincpu --cpus_allowed_policy=split
    }
    echo 2 > /sys/block/vdb/queue/rq_affinity
    sleep 5
    RunFio 10 64 4k randwrite /dev/vdb
    ```

    **Note:** 

    -   You need to modify the parameter settings in the following commands based on your test environment:
        -   `list=`cat /sys/block/vdb/mq/*/cpu_list | awk '{if(i<=NF) print $i;}' i="$i" | tr -d ',' | tr '\n' ','`` command: vdb.
        -   `RunFio 10 64 4k randwrite /dev/vdb` command: 10, 64, 4k, randwrite, and /dev/vdb.
    -   The file system structure may be damaged if you test the bare disk partition directly. If you choose to proceed with this operation, set `filename` to a device name such as /dev/vdb. If you do not want to risk data loss, set `filename` to a file path such as /mnt/test.image.
5.  Run the `sh test100w.sh` command to start testing the performance of the enhanced SSD.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/10111/156810717842181_en-US.png)


Script details:

-   Block device parameters

    In the [script](#), the `echo 2 > /sys/block/vdb/queue/rq_affinity` command is used to set the `rq_affinity` parameter to 2.

    -   If `rq_affinity` is set to 1, the block device forwards the I/O Completion events it receives to the vCPU groups that submit the I/O requests. When multiple threads concurrently processes I/O requests, the I/O Completion events may run on the same vCPU, which results in a performance bottleneck.
    -   If `rq_affinity` is set to 2, the block device forwards the I/O Completion events it receives to the vCPU that submits the I/O requests. The performance of each vCPU is fully delivered when multiple threads concurrently process I/O requests.
-   Binding threads to corresponding vCPUs
    -   Typically, a device has only one Request-Queue. This unique Request-Queue becomes a performance bottleneck when multiple threads concurrently process I/O requests.
    -   In the latest Multi-Queue mode, one device can have multiple Request-Queues that process I/O requests, which deliver full performance of the back-end storage. If you have four I/O threads, you must bind them to the CPU cores that correspond to different Request-Queues. This allows you to use the full capabilities of Multi-Queue mode to improve the storage performance.

To ensure that the device delivers its full performance, you must assign the I/O requests to different Request-Queues. The following command in the [script](#) can be used to bind `jobs` to different CPU cores. `/dev/vd*` is the device name of your enhanced SSD, for example, /dev/vdb.

``` {#codeblock_ftc_f8g_hwu}
fio —ioengine=libaio —runtime=30s —numjobs=${numjobs} —iodepth=${iodepth} —bs=${bs} —rw=${rw} —filename=${filename} —time_based=1 —direct=1 —name=test —group_reporting —cpus_allowed=$spincpu —cpus_allowed_policy=split
```

FIO provides the `cpusallowed` and `cpus_allowed_policy` parameters to bind vCPUs. The preceding command runs multiple `jobs`. They are bound to different CPU cores and correspond to different queue IDs.

To view the CPU core ID that corresponds to a queue ID, perform the following steps:

-   Run the `ls /sys/block/vd/mq/` command to view the queue ID of the enhanced SSD whose device name is /dev/vd\*, for example, /dev/vdb.
-   Run the `cat /sys/block/vd/mq//cpu_list` command to view the CPU core ID corresponding to the queue ID.

