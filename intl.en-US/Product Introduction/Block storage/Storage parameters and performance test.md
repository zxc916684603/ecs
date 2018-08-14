# Storage parameters and performance test {#concept_ytm_vwj_ydb .concept}

This article describes the performance index of block storage, performance testing methods, and how to read the testing results.

## Performance index of block storage {#section_b5z_vzv_ydb .section}

The main index for measuring storage performance includes IOPS, throughput, and latency.

**IOPS**

IOPS stands for Input/Output Operations per Second, which means the amount of write or read operations that can be done each second. Transaction-intensive applications are sensitive to IOPS.

The following table lists the most common performance characteristics measured: sequential operations and random operations.

|IOPS performance characteristics|Description|
|:-------------------------------|:----------|
|Total IOPS|The total number of I/O operations per second|
|Random read IOPS|The average number of random read I/O operations per second|Random access to locations on storage devices|
|Random write IOPS|The average number of random write I/O operations per second|
|Sequential read IOPS|The average number of sequential read I/O operations per second|Sequential access to locations on storage devices contiguously|
|Sequential write IOPS|The average number of sequential write I/O operations per second|

**Throughput**

Throughput measures the data size successfully transferred per second.

Applications that require mass read or write operations are sensitive to throughput.

**Latency**

Latency is the period that is needed to complete an I/O request.

For latency-sensitive applications, such as databases, in which high latency may lead to error reports in applications, we recommend that you use SSD Cloud disks, SSD Shared Block Storage, or local SSD disks.

For throughput-sensitive applications that are not sensitive to latency, such as I/O intensive applications, we recommend that you use ECS instances with local HDD disks, such as instances of the d1 or d1ne instance type family.

## Performance {#section_i5z_vzv_ydb .section}

This section describes the performance of various block storage.

**Cloud disks**

The following table lists the features and typical scenarios of different types of cloud disks.

|Parameters|SSD Cloud Disks|Ultra Cloud Disks|Basic Cloud Disks|
|:---------|:--------------|:----------------|:----------------|
|Capacity of a single disk|32,768 GiB|32,768 GiB|2,000 GiB|
|Maximum IOPS|20,000\*|3,000|Several hundreds|
|Maximum throughput|300 MBps\*|80 MBps|30 MBps−40 MBps|
|Formulas to calculate performance of a single disk\*\*|IOPS = min\{1200 + 30 \* capacity, 20000\}|IOPS = min\{1000 + 6 \* capacity, 3000\}|N/A|
|Throughput = min \{80 + 0.5 \* capacity, 300\} MBps|Throughput = min\{50 + 0.1 \* capacity, 80\} MBps|N/A|
|Data reliability|99.9999999%|99.9999999%|99.9999999%|
|API name|cloud\_ssd|cloud\_efficiency|cloud|
|Typical scenarios| -   Small or medium-sized rational databases, such as MySQL, SQL Server, PostgreSQL, or Oracle
-   Small or medium-sized development or testing applications that require high data reliability

 | -   Small or medium-sized rational databases, such as MySQL, SQL Server, or PostgreSQL
-   Small or medium-sized development or testing applications that require high data reliability and medium performance

 | -   Applications with infrequent access or low I/O operations
-   Applications that require low costs and random read and write I/O operations

 |

\* The performance of an SSD Cloud Disk varies according to the size of the data blocks. Smaller data blocks result in lower throughput and higher IOPS, as shown in the following table. An SSD Cloud Disk can achieve the expected performance only when it is attached to an I/O-optimized instance.

|Data block size|Maximum IOPS|Throughput|
|:--------------|:-----------|:---------|
|4 KiB or 8 KiB|About 20,000|Small, far smaller than 300 MBps|
|16 KiB|About 17,200|Close to 300 MBps|
|32 KiB|About 9,600|
|64 KiB|About 4,800|

\*\* Here, an SSD Cloud Disk is taken as an example to describe the performance of a single disk:

-   The maximum IOPS: The baseline is 1,800 IOPS. It can increase by 30 IOPS per GiB of storage. The maximum IOPS is 25,000.
-   The maximum throughput: The baseline is 120 MBps. It can increase by 0.5 MBps per GiB of storage. The maximum throughput is 300 MBps.

The latency varies according to the disk categories as follows:

-   SSD Cloud Disks: 0.5−2 ms
-   Ultra Cloud Disks: 1−3 ms
-   Basic Cloud Disks: 5−10 ms

**Shared Block Storage**

The following table lists the features and typical scenarios of different types of Shared Block Storage.

|Parameters|SSD Shared Bock Storage|Ultra Shared Block Storage|
|:---------|:----------------------|:-------------------------|
|Capacity| -   Singe disk: 32,768 GiB
-   All disks attached to one instance: Up to 128 TiB

 | -   Single disk: 32,768 GiB
-   All disks attached to one instance: Up to 128 TiB

 |
|Maximum random read/write IOPS\*|30,000|5,000|
|Maximum sequential read/write throughput\*|512 MBps|160 MBps|
|Formulas to calculate performance of a single disk\*\*|IOPS = min\{1600 + 40 \* capacity, 30000\}|IOPS = min\{1000 + 6 \* capacity, 5000\}|
|Throughput = min\{100 + 0.5 \* capacity, 512\} MBps|Throughput = min\{50 + 0.15 \* capacity, 160\} MBps|
|Typical scenarios| -   Oracle RAC
-   SQL Server
-   Failover cluster
-   High-availability of servers

 | -   High-availability of servers
-   High-availability architecture of development and testing databases

 |

\* The maximum IOPS and throughput listed in the preceding table are the maximum performance of a bare shared block storage device that is attached to two or more instances at the same time during stress tests.

\*\* Here, an SSD Shared Block Storage is used as an example to describe the performance of a single disk:

-   The maximum IOPS: The baseline is 0 IOPS. It can increase by 40 IOPS per GiB of storage. The maximum IOPS is 30,000.
-   The maximum throughput: The baseline is 50 MBps. It can increase by 0.5 MBps per GiB of storage. The maximum throughput is 512 MBps.

The latency varies according to the shared block storage categories as follows:

-   SSD Shared Block Storage: 0.5−2 ms
-   Ultra Shared Block Storage: 1−3 ms

**Local disks**

For the performance of local disks, see [Local disks](intl.en-US/Product Introduction/Block storage/Local disks.md#).

## Test disk performance {#section_jvz_vzv_ydb .section}

According to the OS on which an instance is running, you can use different tools to test disk performance:

-   Linux: DD, fio, or sysbench is recommended.
-   Windows: fio or Iometer is recommended.

This section describes how to test disk performance, taking the fio tool used with a Linux instance as an example. Before you test the disk, you must make sure the disk is 4K aligned.

You can use fio to test the performance of a cloud disk.

**Warning:** You can test bare disks to obtain more accurate performance data, but the test causes damage to the structure of the file system. Make sure that you back up your data before testing. We recommend that you use a new ECS instance without data on the disks to test the disks by using fio.

-   Test random write IOPS

    ```
    fio -direct=1 -iodepth=128 -rw=randwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Write_Testing
    ```

-   Test random read IOPS

    ```
    fio -direct=1 -iodepth=128 -rw=randread -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Read_Testing
    ```

-   Test write throughput

    ```
    fio -direct=1 -iodepth=64 -rw=write -ioengine=libaio -bs=1024k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Write_PPS_Testing
    ```

-   Test read throughput

    ```
    fio -direct=1 -iodepth=64 -rw=read -ioengine=libaio -bs=1024k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Read_PPS_Testing
    ```


Take the command for testing random read IOPS as an example to describe the meaning of the parameters of a fio command, as shown in the following table.

|Parameter|Description|
|:--------|:----------|
|-direct=1|Ignore I/O buffer when testing. Data is written directly.|
|-rw=randwrite| Read and write policies. Available options:-   randread \(random read\)
-   randwrite\(random write\)
-   read\(sequential read\)
-   write\(sequential write\)
-   randrw \(random read and write\).

|
|-ioengine=libaio|Use libaio as the testing method \(Linux AIO, Asynchronous I/O\). Usually there are two ways for an application to use I/O: synchronous and asynchronous. Synchronous I/O only sends out one I/O request at a time, and returns only after the kernel is completed. In this case, the iodepth is always less than 1 for a single job, but can be resolved by multiple concurrent jobs. Usually 16−32 concurrent jobs can fill up the iodepth. The asynchronous method uses libaio to submit a batch of I/O requests each time, thus reducing interaction times, and makes interaction more effective.|
|-bs=4k|The size of each block for one I/O is 4k. If not specified, the default value 4k is used. When IOPS is tested, we recommend that you set the bs to a small value, such as 4k in this example command. When throughput is tested, we recommend that you set the bs to a large value, such as 1024k in the IOPS tests.|
|-size=1G|The size of the testing file is 1 GiB.|
|-numjobs=1|The number of testing jobs is 1.|
|-runtime=1000|Testing time is 1,000 seconds. If not specified, the test will go on with the value specified for -size, and write data in -bs each time.|
|-group\_reporting|The display mode for showing the testing results. Group\_reporting means the statistics of each job are summed up, instead of all statistics of each job being shown.|
|-filename=iotest|The output path and name of the test files. You can test bare disks to obtain more accurate performance data, but the test causes damage to the structure of the file system. Make sure that you back up your data before testing.|
|-name=Rand\_Write\_Testing|The name of the testing task.|

