# Storage parameters and performance test {#concept_ytm_vwj_ydb .concept}

This article describes the performance index of block storage, performance testing methods, and how to read the testing results.

## Performance index of block storage {#section_b5z_vzv_ydb .section}

The main index for measuring storage performance includes IOPS, throughput, and latency.

**IOPS**

IOPS stands for Input/Output Operations per Second, which means the amount of write or read operations can be done in one second.  Transaction-intensive applications are sensitive to IOPS.

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
|Capacity of a single disk|32,768 GiB|32,768 GiB|2000 GiB|
|Maximum IOPS|20000[\*](https://help.aliyun.com/document_detail/25382.html?spm=a2c4g.11186623.6.552.AXb2YZ#ssd)|3000|Several hundreds|
|Maximum throughput|300 MBps[\*](https://help.aliyun.com/document_detail/25382.html?spm=a2c4g.11186623.6.552.AXb2YZ#ssd)|80 MBps|30 MBps−40 MBps|
|Formulas to calculate performance of a single disk[\*\*](https://help.aliyun.com/document_detail/25382.html?spm=a2c4g.11186623.6.552.AXb2YZ#formula)|IOPS = min\{1200 + 30 \* capacity, 20000\}|IOPS = min\{1000 + 6 \* capacity, 3000\}|N/A|
|Throughput = min \{80 + 0.5 \* capacity, 300\} Mbps|Throughput = min\{50 + 0.1 \* capacity, 80\} MBps|N/A|
|Data reliability|99.9999999%|99.9999999%|99.9999999%|
|API name|Cloud\_ssd|Cloud\_efficiency|Cloud|
|Typical scenarios| -   Small or medium-sized rational databases, such as MySQL, SQL Server, PostgreSQL, or Oracle
-   Small or medium-sized development or testing applications that require high data reliability

 | -   Small or medium-sized rational databases, such as MySQL, SQL Server, or PostgreSQL
-   Small or medium-sized development or testing applications that require high data reliability and medium performance

 | -   Applications with infrequent access or low I/O operations
-   Applications that require low costs and random read and write I/O operations

 |

The performance of an SSD Cloud Disk varies according to the size of the data blocks. Smaller data blocks result in lower throughput and higher IOPS, as shown in the following table. An SSD Cloud Disk can achieve the expected performance only when it is attached to an I/O-optimized instance.

|Data block size|Maximum IOPS|Throughput|
|:--------------|:-----------|:---------|
|4 KiB or 8 KiB|About 20,000|Small, far smaller than 300 MBps|
|16 KiB|About 17,200|Close to 300 MBps|
|32 KiB|About 9,600|
|64 KiB|About 4,800|

\*\* Take an SSD Cloud Disk as an example to describe how to calculate the performance of a single disk:

-   The maximum IOPS: The base is 1,200 IOPS, increase by 30 IOPS per GiB storage, and the maximum IOPS of a single disk is 20,000.
-   The maximum throughput: The base is 80 MBps, increase by 0.5 MBps per GiB storage, and the maximum throughput of a singled disk is 300 MBps.

The latency varies according to the disk categories as follows:

-   SSD Cloud Disks: 0.5 ms−2 ms
-   Ultra Cloud Disks: 1 ms−3 ms
-   Basic Cloud Disks: 5 ms−10 ms

**Shared Block Storage**

The following table lists the features and typical scenarios of different types of Shared Block Storage.

|Parameters|SSD Shared Bock Storage|Ultra Shared Block Storage|
|:---------|:----------------------|:-------------------------|
|Capacity|Singe disk: 32,768 GiB All disks attached to one instance: Up to 128 TiB|Single disk: 32,768 GiB All disks attached to one instance: Up to 128 TiB|
|Maximum random read/write IOPS\*|30000|5000|
|Maximum sequential read/write throughput\*|512 MBps|160 MBps|
|Formulas to calculate performance of a single disk\*\*|IOPS = min\{40 \* capacity, 30000\}|IOPS = min\{1000 + 6 \* capacity, 5000\}|
|Throughput = min\{50 + 0.5 \* capacity, 512\} MBps|Throughput = min\{50 + 0.15 \* capacity, 160\} MBps|
|Typical scenarios| -   Oracle RAC
-   SQL Server
-   Failover Cluster
-   Failover clusters

 | -   High-availability of servers
-   High-availability architecture of development and testing databases

 |

\* The maximum IOPS and throughput listed in the preceding table are the maximum performance of a bare shared block storage device that is attached to two or more instances at the same time during stress tests.

\*\* Take an SSD Shared Block Storage as an example to describe how to calculate the performance of a single disk:

-   The maximum IOPS: The base is 0, increase by 40 IOPS per GiB storage, and the maximum IOPS is 30,000 IOPS.
-   The maximum throughput: The base is 50 MBps, increase by 0.5 MBps per GiB storage, and the maximum throughput is 512 MBps.

The latency varies according to the shared block storage categories as follows:

-   SSD Shared Block Storage: 0.5 ms
-   Ultra Shared Block Storage: 1 ms

**Local disks**

For the performance of local disks, see [Local disks](https://www.alibabacloud.com/help/doc-detail/63138.htm).

**Local disks**

For the performance of local disks, see [Local disks](https://partners-intl.aliyun.com/help/doc-detail/63138.htm).

## Test disk performance {#section_jvz_vzv_ydb .section}

According to the OS on which an instance is running, you can use different tools to test disk performance:

-   Linux: DD, fio, or sysbench is recommended.
-   Windows: fio or Iometer is recommended.

This section takes a Linux instance and fio as an example to describe how to test the disk performance by using fio.  Before testing the disk, you must make sure the disk is 4K aligned. You can use fio to test the performance of a cloud disk.

**Warning:** Testing bare disks can obtain more accurate performance data, but damages the structure of the file system. Make sure that you back up your data before testing. We recommend that you use a new ECS instance without data on the disks to test the disks by using fio.

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
|-iodepth=128|Indicates that when you use AIO, the maximum number of I/O issues at the same time is 128.|
|-rw=randwrite| Read and write policies.  Available options:-   randread \(random read\)
-   read\(sequential read\)
-   write\(sequential write\)
-   randrw \(random read and write\).

|
|-ioengine=libaio|Use libaio as the testing method \(Linux AIO, Asynchronous I/O\).  Usually you have two ways for an application to use I/O: synchronous and asynchronous. Synchronous I/O only sends out one I/O request each time, and returns only after the kernel is completed. In this case, the iodepth is always less than 1 for a single job, but can be resolved by multiple concurrent jobs. Usually 16-32 concurrent jobs can fill up the iodepth. Asynchronous method uses libaio to submit a batch of I/O requests each time, thus reduces interaction times, and makes interaction more effective.|
|-bs=4k|The size of each block for one I/O is 4k. If not specified, the default value 4k is used.  When IOPS is tested, we recommend that you set the bs to a small value, such as 4k in this example command.  When throughput is tested, we recommend that you set the bs to a big value, such as 1024k in the IOPS tests.|
|-size=1G|The size of the testing file is 1 GiB.|
|-numjobs=1|The number of testing jobs is 1.|
|-runtime=1000|Testing time is 1000 seconds. If not specified, the test will go on with the value specified for -size, and write data in -bs each time.|
|-group\_reporting|The display mode of showing the testing results. Group\_reporting means sums up statistics of each job, instead of showing statistics by different jobs.|
|-filename=iotest|The output path and name of the test files. Testing bare disks can obtain more accurate performance data, but damages the structure of the file sytem. Make sure that you back up your data before testing.|
|-name=Rand\_Write\_Testing|The name of the testing task.|

Take the output of a random reads IOPS test on an SSD cloud disk of 800 GiB capacity as an example, we describe how to explain the test report.

```

Rand_Read_Testing: (g=0): rw=randread, bs=4K-4K/4K-4K/4K-4K, ioengine=libaio, iodepth=128
fio-2.2.8
Starting 1 process
Jobs: 1 (f=1): [r(1)] [21.4% done] [80000KB/0KB/0KB /s] [20.0K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [28.6% done] [80000KB/0KB/0KB /s] [20.0K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [35.7% done] [80000KB/0KB/0KB /s] [20.0K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [42.9% done] [80004KB/0KB/0KB /s] [20.1K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [50.0% done] [80004KB/0KB/0KB /s] [20.1K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [57.1% done] [80000KB/0KB/0KB /s] [20.0K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [64.3% done] [80144KB/0KB/0KB /s] [20.4K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [71.4% done] [80388KB/0KB/0KB /s] [20.1K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [78.6% done] [80232KB/0KB/0KB /s] [20.6K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [85.7% done] [80260KB/0KB/0KB /s] [20.7K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [92.9% done] [80016KB/0KB/0KB /s] [20.4K/0/0 iops] [eta 00Jobs: 1 (f=1): [r(1)] [100.0% done] [80576KB/0KB/0KB /s] [20.2K/0/0 iops] [eta 00m:00s]
Rand_Read_Testing: (groupid=0, jobs=1): err= 0: pid=9845: Tue Sep 26 20:21:01 2017
read : io=1024.0MB, bw=80505KB/s, iops=20126, runt= 13025msec
slat (usec): min=1, max=674, avg= 4.09, stdev= 6.11
clat (usec): min=172, max=82992, avg=6353.90, stdev=19137.18
lat (usec): min=175, max=82994, avg=6358.28, stdev=19137.16
clat percentiles (usec):
| 1.00th=[ 454], 5.00th=[ 668], 10.00th=[ 812], 20.00th=[ 996],
| 30.00th=[ 1128], 40.00th=[ 1256], 50.00th=[ 1368], 60.00th=[ 1480],
| 70.00th=[ 1624], 80.00th=[ 1816], 90.00th=[ 2192], 95.00th=[79360],
| 99.00th=[81408], 99.50th=[81408], 99.90th=[82432], 99.95th=[82432],
| 99.99th=[82432]
bw (KB /s): min=79530, max=81840, per=99.45%, avg=80064.69, stdev=463.90
lat (usec) : 250=0.04%, 500=1.49%, 750=6.08%, 1000=12.81%
LAT (MSEC): 2 = 65.86%, 4 = 6.84%, 10 = 0.49, 20 = 0.04%, 100 = 6.35%
cpu : usr=3.19%, sys=10.95%, ctx=23746, majf=0, minf=160
IO depths : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
submit : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
complete : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.1%
issued : total=r=262144/w=0/d=0, short=r=0/w=0/d=0, drop=r=0/w=0/d=0
latency : target=0, window=0, percentile=100.00%, depth=128
Run status group 0 (all jobs):
READ: io=1024.0MB, aggrb=80504KB/s, minb=80504KB/s, maxb=80504KB/s, mint=13025msec, maxt=13025msec
Disk stats (read/write):
vdb: ios=258422/0, merge=0/0, ticks=1625844/0, in_queue=1625990, util=99.30%
```

In the result, you must pay the most attention to the following code line:

```
read : io=1024.0MB, bw=80505KB/s, iops=20126, runt= 13025msec
```

The line means that fio did a total of 1 GiB of I/O at 80 MB/s for a total of 20126 IOPS \(at the default 4k block size\), and ran for 13 seconds. According to the formula, the maximum IOPS of an SSD cloud disk is: 20126，而根据公式计算的数值为：

*IOPS = min\{1200+30 ∗ capacity, 20000\} = IOPS = min\{1200+30 ∗ 800, 20000\} = 20,000*

The calculated IOPS is similar to the value in the output report, 20,126.

