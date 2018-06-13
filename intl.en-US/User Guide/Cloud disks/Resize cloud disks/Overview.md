# Overview {#concept_e1g_44g_ydb .concept}

To meet the expanded business needs, you can increase the size of a cloud disk when it is used as a system disk or a data disk. To resize the disks, use different features:

-   For a system disk: **Change System Disk**
-   For a data disk: **Resize Disk**

## Size limits of cloud disks {#section_whc_q4g_ydb .section}

The size limits of cloud disks for resizing vary between system disks and data disks.

## System disks {#section_xhc_q4g_ydb .section}

By using the **Change system disk** feature, you can keep the system disk size unchanged or increase the size only, but not reduce the size. For example, before changing, the system disk of a CentOS instance is of 35 GiB, so it must be equal to or greater than 35 GiB **after changing**.  The size limit for changing is determined by the image and the current size of the system disk, as displayed in the following table.

|Image|Size limit \(GiB\)|
|:----|:-----------------|
|Linux \(excluding CoreOS\) + FreeBSD|\[Max\{20, current size of the system disk\}, 500\]|
|CoreOS|\[Max\{30, current size of the system disk\}, 500\]|
|Windows|\[Max\{40, current size of the system disk\}, 500\]|

## Data disk {#section_zhc_q4g_ydb .section}

By using the **Resize Disk** feature, you can keep the data disk size unchanged or increase the size only, but not reduce the size. The following table lists the capacity limit of a data disk after resizing, which is determined by the cloud disk types.

|Cloud disk type|Current capacity|Capacity after resizing|
|:--------------|:---------------|:----------------------|
|Basic Cloud Disk |Any|2000 GiB|
|SSD Cloud Disk or Ultra Cloud Disk|equal or less than 2048 GiB|2048 GiB|
|SSD Cloud Disk or Ultra Cloud Disk|\> 2048 GiB|Cannot be resized|

## Operations {#section_d3c_q4g_ydb .section}

You can perform the following tasks:

-   To increase the size of the system disk of an ECS instance, see [Increase system disk size](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Increase system disk size.md#).
-   To resize a data disk attached to a Windows instance, see [Windows \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#).
-   To resize a data disk attached to a Linux instance, see [Linux \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Linux _ Resize a data disk.md#).

