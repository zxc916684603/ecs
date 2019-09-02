# Shared Block Storage {#concept_abt_gpv_xgb .concept}

Shared Block Storage is a block-level data storage service that features high concurrency, high performance, and high reliability. It supports concurrent reads and writes on multiple ECS instances, and provides data reliability of up to 99.9999999%.

## Benefits {#section_uv2_4pf_xv7 .section}

Shared Block Storage stores three copies of each piece of data, and distributes the copies across different servers. This achieves 99.9999999% data reliability for ECS instances. Shared Block Storage automatically copies your data within a zone to ensure data availability and prevent service disruptions, for example, due to a hardware failure.

## Scenarios {#section_c1n_z2w_xgb .section}

In a traditional cluster architecture, multiple computing nodes access the same copy of data to provide services. To prevent service disruptions due to single point of failures, you can use Shared Block Storage to ensure access to the data, achieving high availability. We recommend that you store business data in Shared Block Storage devices and use a cluster file system to manage these devices. Data consistency can be guaranteed between multiple front-end computing nodes during concurrent read/write operations.

The high availability architecture of Shared Block Storage is suitable for enterprise-level applications. It provides shared access to block storage devices in a shared-everything architecture, such as the high availability server cluster architecture and Oracle Real Application Clusters \(RAC\). Oracle RAC is common among government departments, enterprises, and financial customers.

## Types {#sharedBlock .section}

Shared Block Storage can be divided into the following types based on performance:

-   Shared SSD Block Storage

    Shared SSD Block Storage uses SSDs as storage media to provide stable and high-performance storage with enhanced random I/O and data reliability.

-   Shared Ultra Block Storage

    Shared Ultra Block Storage uses a combination of SSDs and HDDs as storage media.


## Performance {#section_qhm_gfw_xgb .section}

For more information about the performance of Shared Block Storage, see [Block storage performance](reseller.en-US/Block Storage/Block storage performance.md#).

## Pricing {#section_inz_nbw_ydb .section}

Shared Block Storage is free and under public preview.

## Operations {#section_mnz_nbw_ydb .section}

-   You can create, attach, detach, and release Shared Block Storage devices in a similar manner as disks.
-   Shared Block Storage devices can only be created separately and used only as data disks.
-   A single Shared Block Storage device can be attached to a maximum of eight ECS instances in the same zone and region at the same time.
-   When attached to an ECS instance, Shared Block Storage devices share the data disk quota with disks, that is, up to 16 data disks can be attached to each ECS instance.
-   You can allocate the capacity of Shared Block Storage devices in a similar manner as hard disks. You can format and partition Shared Block Storage devices that are attached to an ECS instance and create a file system.

## File system {#section_6zk_pfk_3eb .section}

Shared Block Storage devices are not pre-installed with a cluster file system. However, you can install cluster file systems such as Google File System \(GFS\) and General Parallel File System \(GPFS\) to manage these devices. If Oracle RAC is deployed, we recommend that you use Automatic Storage Management \(ASM\) to manage storage volumes and file systems.

We recommend that you do not use a traditional file system to manage Shared Block Storage devices because the following two errors may occur:

-   Disk space allocation conflict

    If a Shared Block Storage device is attached to multiple instances and one of these instances \(for example, instance A\) writes data to a file, instance A checks the file system and available disk space. After the write operation is complete, the space allocation record is changed in instance A, but the records in other instances are not updated. In this case, when another instance \(for example, instance B\) tries to write data to the file, this instance may allocate the disk space that has been already allocated by instance A, resulting in a disk space allocation conflict.

-   Data file inconsistency

    After an instance \(for example, instance A\) reads and caches data, another process that accesses the same data will directly read the data from the cache. However, if a copy of the same data that is stored on another instance \(for example, instance B\) is modified during this period, and instance A does not update according to the latest data change, instance A still reads the data from the cache. Data inconsistency occurs as a result.


