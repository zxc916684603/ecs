# Overview {#concept_e1g_44g_ydb .concept}

You can resize cloud disks as your business and application data grows.

## Scenarios {#section_ilv_yg2_2hb .section}

You can resize the storage capacity of a single instance in the following ways:

-   [Resize an existing cloud disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks offline.md#). You need to resize an existing partition or a new partition.
-   [Create a new cloud disk](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a Pay-As-You-Go cloud disk.md#), [attach](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#) it to the instance as a data disk, and then [partition or format](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#) the disk.
-   [Change a system disk](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk by using a public image.md#) and specify a higher system disk capacity.

This topic describes the thresholds of extended disks and how to resize an existing cloud disk.

## Thresholds of extended system disks {#section_xhc_q4g_ydb .section}

The new capacity value must be greater than the existing capacity of the system disk, but equal to or less than 500 GiB. The following table describes the thresholds of extended system disks for different images.

|Image|Maximum capacity \(GiB\)|
|:----|:-----------------------|
|Linux \(excluding CoreOS\) and FreeBSD|Max \{20, current capacity of the system disk\} to 500|
|CoreOS|Max \{30, current capacity of the system disk\} to 500|
|Windows|Max \{40, current capacity of the system disk\} to 500|

For example, the current capacity of the system disk of a CentOS instance is 35 GiB. After you resize the system disk, its capacity must be equal to or greater than 35 GiB, but equal to or less than 500 GiB.

## Thresholds of extended data disks {#section_hzp_wzv_42b .section}

The new value must be greater than the existing capacity of the data disk. The following table lists the data disk resizing limits for different cloud disk categories.

|Disk type|Current capacity \(GiB\)|Maximum capacity \(GiB\)|
|:--------|:-----------------------|:-----------------------|
|Basic disk|< 2,000|2,000|
|SSD disk or ultra disk|< 6,144|6,144|
|SSD disk or ultra disk|≥ 6,144|Cannot be extended|
|ESSD disk|< 32,768|32,768|

## Resize a cloud disk {#section_0jb_ce8_ots .section}

1.  Log on to the console or use the API \(ResizeDisk\) to [resize a cloud disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks offline.md#).
2.  Log on to the console or use the API \(RebootInstance\) to [restart an instance](../../../../reseller.en-US/Instances/Manage instances/Restart an instance.md#).
3.  Remote access the instance and resize the partition and file system:

    |Before you resize the cloud disk|After you resize the cloud disk \(GiB\)|Resize the partition and file system|
    |--------------------------------|---------------------------------------|------------------------------------|
    |Not partitioned|< 2,048|     -   [Partition or format a Windows data disk](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#)
    -   [Partition or format a Linux data disk](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#)
 |
    |≥ 2,048|[Partition or format a data disk of more than 2 TiB](reseller.en-US/Block Storage/Block storage/Format a data disk/Partition and format data disks larger than 2 TiB.md#)|
    |Partitioned|< 2,048|     -   [Resize a file system of a Windows disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Extend a Windows file system.md#)
    -   [Resize a file system of a Linux system disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Extend the file system of the Linux system disk.md#)
    -   [Resize a file system of a Linux data disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize partitions and file systems of Linux data disks.md#)
 |
    |≥ 2,048|     -   For the GPT partition format:
        -   [Resize a file system of a Windows disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Extend a Windows file system.md#)
        -   [Resize a file system of a Linux system disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Extend the file system of the Linux system disk.md#)
        -   [Resize a file system of a Linux data disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize partitions and file systems of Linux data disks.md#)
    -   For the MBR partition format: You cannot resize the partition

**Note:** If you want to resize a cloud disk to more than 2,048 GiB, the cloud disk cannot use the MBR partition format. In this case, you must first query the partition format of the cloud disk. If the MBR partition format is used, we recommend that you create and attach another data disk. Format a GPT partition and copy the data in the MBR partition to the GPT partition.

 |


