# Local disks {#concept_g3w_qzv_tdb .concept}

This topic provides information about local disks that you can purchase along with instances.

## Background information {#section_zb2_tbv_jhb .section}

Local disks are disks attached to a machine on which ECS instances are hosted, and are designed to provide local storage and access for instances. Features of local disks include low latency, high random IOPS, high throughput, and cost-effective performance. For more information, see [Instance type families](../../../../reseller.en-US/Instances/Instance type families.md#). If you are using phased-out local SSDs, see [Ephemeral SSDs](https://partners-intl.aliyun.com/help/doc-detail/35241.htm).

## Disk types {#section_hdp_m2w_ydb .section}

Currently, Alibaba Cloud provides the following two local disks:

-   NVMe SSD: A local disk type that can be used by such instance type families as i2, i1, and gn5. NVMe SSDs are suitable for the following scenarios:
    -   Online services such as online gaming, e-commerce, live video, and media, where instance type families such as i1 and i2 meet low latency and high I/O performance required by I/O intensive applications in block storage.
    -   Service scenarios with high requirements for I/O performance and high-availability architecture at the application layer, such as NoSQL non-relational databases, MPP data warehouses, and distributed file systems.
-   SATA HDD: A local disk type that can be used by such instance type families as d1ne and d1, which are applicable to multiple industries with high requirements for big data computing, storage analysis, massive data storage, and offline computing \(for example, e-commerce and financial industries\). SATA HDDs are designed to meet the requirements of distributed computing service types \(for example, Hadoop\) for instance storage performance, storage capacity, and intranet bandwidth.

## NVMe SSD performance {#section_kdp_m2w_ydb .section}

The following table describes the performance indexes of the NVMe SSD disk type.

|NVMe SSD index|Single disk performance|Overall instance performance|
|:-------------|:----------------------|:---------------------------|
|Maximum capacity|1456 GiB|2,912 GiB|
|Maximum IOPS|240,000|480,000|
|Write IOPS [\*](#)|min\{165 \* capacity, 240,000\}|2 \* min\{165 \* capacity, 240,000\}|
|Read IOPS [\*](#)|
|Maximum read throughput|2 GBps|4 GBps|
|Read throughput [\*](#)|min\{1.4 \* capacity, 2,000\} MBps|2 \* min\{1.4 \* capacity, 2,000\} MBps|
|Maximum write throughput|1.2 GBps|2.4 GBps|
|Write throughput [\*](#)|min\{0.85 \* capacity, 1,200\} MBps|2 \* min\{0.85 \* capacity, 1,200\} MBps|
|Access latency|Microsecond \(μs\)|

\* The performance of a single disk is calculated as follows:

-   Write IOPS: 165 IOPS for each GiB, up to 240,000 IOPS
-   Write throughput: 0.85 MBps for each GiB, up to 1,200 Mbit/s

To obtain the standard performance data and measure the Quality of Service \(QoS\) of Alibaba Cloud local disks, you can test the bandwidth, IOPS, and latency of the NVMe SSD by using the method described in the [NVMe SSD performance test](#).

## SATA HDD performance {#section_qdp_m2w_ydb .section}

The following table describes the performance indexes of the SATA HDD disk type.

|SATA HDD index|Single disk performance|Overall instance performance|
|:-------------|:----------------------|:---------------------------|
|Maximum capacity|5,500 GiB|154,000 GiB|
|Maximum throughput|190 MBps|5,320 MBps|
|Access latency|Millisecond \(ms\)|

## Billing {#section_sdp_m2w_ydb .section}

The fees billed for local disks are included in the fees billed for the instances to which local disks are attached. For more information about instance billing methods, see [Subscription](../../../../reseller.en-US/Pricing/Subscription.md#) and [Pay-As-You-Go](../../../../reseller.en-US/Pricing/Pay-As-You-Go.md#).

## Limits {#section_ydp_m2w_ydb .section}

-   A single point of failure \(SPOF\) may be evident at the application layer due to each local disk being attached to a single host machine, meaning data reliability is dependent on the reliability of the host machine. We recommend that you implement data redundancy at the application layer to guarantee data availability.

    **Warning:** When you use a local disk to store data, there is a risk of data loss \(for example, if a hardware fault occurs to the host machine\). Therefore, we recommend you do not use a local disk to store any data that you need to keep for a long term. If your applications have no data reliability architecture, we recommend that you use [cloud disks or Shared Block Storage](reseller.en-US/Block Storage/Block storage/Cloud disks and Shared Block Storage.md#) in your instances to increase data reliability.

-   After you purchase an instance along with a local disk, you need to log on to the instance to [partition and format the local disk](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#).
-   Regarding disk operations, you are not able to:
    -   Create a separate local disk.
    -   Use a snapshot to create a local disk.
    -   Attach a local disk.
    -   Detach and release a local disk separately.
    -   Resize a local disk.
    -   Reinitialize a local disk.
    -   Create a snapshot for a local disk.
    -   Use a snapshot to roll back a local disk.

## Disk initialization sequence {#section_r12_4tl_wgb .section}

When you create an instance along with a local disk, all disks are initialized according to the following rules:

-   Rule 1: If the specified image does not have a data disk snapshot, the local disk is initialized before the cloud disks created along with the instance.
-   Rule 2: If the specified image has a data disk snapshot, the sequence of the data disks recorded in the snapshot is retained, subject to Rule 1.

For example, for a Linux image that includes a snapshot of two data disks, the disks are initialized according to the following sequence.

-   If the original device names of the two data disks are /dev/xvdb and /dev/xvdc respectively, these names are allocated to the specified data disks in the image. The disk initialization starts from the system disk, then proceeds to data disk 1 specified in the image, data disk 2 specified in the image, local disk 1, local disk 2, cloud disk 1, cloud 2, and in such a sequence until initialization is completed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9561/155721521339625_en-US.png)

-   If the original device names of the two data disks are /dev/xvdc and /dev/xvdd respectively, these names are allocated to the specified data disks in the image. Then, the remaining device names are allocated to the local disks. The disk initialization starts from the system disk, then proceeds to local disk 1, data disk 1 specified in the image, data disk 2 specified in the image, local disk 2, cloud disk 1, cloud 2, and in such a sequence until initialization is completed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9561/155721521339626_en-US.png)


## Life cycle {#section_tdp_m2w_ydb .section}

The life cycle of a local disk is the same as that of the instance to which the local disk is attached. For more information, see [ECS instance life cycle](../../../../reseller.en-US/Instances/ECS instance life cycle.md#).

## Impact of instance operations on the data in local disks {#section_vdp_m2w_ydb .section}

The following table describes the impact of instance operations on the data stored in local disks.

|Instance operation|Data status of the local disk|Data on the local disk|
|:-----------------|:----------------------------|:---------------------|
|Restart the operating system, [restart the instance by using the ECS console](../../../../reseller.en-US/Instances/Manage instances/Restart an instance.md#), or forcibly restart the instance.|Retained|Retained|
|Shut down the operating system, [stop the instance by using the ECS console](../../../../reseller.en-US/Instances/Manage instances/Start or stop an instance.md#), or forcibly stop the instance.|Retained|Retained|
|[The instance is restored automatically](../../../../reseller.en-US/.md#).|Erased|Erased|
|[Release the instance](../../../../reseller.en-US/Instances/Manage instances/Release an instance.md#).|Erased|Erased|
|A Subscription instance is stopped upon expiry or your account has an overdue payment, but the instance is not released.|Retained|Retained|
|A Subscription instance is stopped upon expiry or your account has an overdue payment, and the instance is released.|Erased|Erased|

## NVMe SSD performance test {#section_wl1_rc4_fhb .section}

We recommend that you use the fio tool to test the performance of a local disk for Linux instances and Windows instances. The following example describes how to test the block storage performance of a bare disk /dev/vdx. For a description of the test command parameters, see [performance indexes of block storage](reseller.en-US/Block Storage/Storage parameters and performance tests.md#).

**Warning:** A direct bare disk test destroys the file system structure. Therefore, you must back up your data before the test. Additionally, the write operation overwrites the data on local disks. We recommend that you only test local disk performance on newly purchased ECS instances. If you decide to test a bare disk, we recommend that you exercise caution when performing this action.

-   **NVMe SSD bandwidth performance test**

    -   To test the read bandwidth, run the following command:

        ```
        fio –direct=1 –iodepth=128 –rw=read –ioengine=libaio –bs=128k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

    -   To test the write bandwidth, run the following command:

        ```
        fio –direct=1 –iodepth=128 –rw=write –ioengine=libaio –bs=128k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

-   **NVMe SSD IOPS performance test**

    -   To test the random read IOPS, run the following command:

        ```
        fio –direct=1 –iodepth=32 –rw=randread –ioengine=libaio –bs=4k –numjobs=4 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

    -   To test the random write IOPS, run the following command:

        ```
        fio –direct=1 –iodepth=32 –rw=randwrite –ioengine=libaio –bs=4k –numjobs=4 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

-   **NVMe SSD latency performance test**

    -   To test the random read latency, run the following command:

        ```
        fio –direct=1 –iodepth=1 –rw=randread –ioengine=libaio –bs=4k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

    -   To test the random write latency, run the following command:

        ```
        fio –direct=1 –iodepth=1 –rw=randwrite –ioengine=libaio –bs=4k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

    -   To test the sequential read latency, run the following command:

        ```
        fio –direct=1 –iodepth=1 –rw=read –ioengine=libaio –bs=4k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```

    -   To test the sequential write latency, run the following command:

        ```
        fio –direct=1 –iodepth=1 –rw=write –ioengine=libaio –bs=4k –numjobs=1 –time_based=1 –runtime=1000 –group_reporting –filename=/dev/vdx
        ```


