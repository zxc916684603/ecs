# Block storage performance {#concept_ytm_vwj_ydb .concept}

This topic describes the performance indexes, performance, and performance test methods of block storage devices such as cloud disks, Shared Block Storage, and local disks.

## Performance indexes {#section_bwf_vis_7i8 .section}

The main indexes for measuring storage performance include IOPS, throughput, and latency.

-   **IOPS**

    Input/Output Operations per Second \(IOPS\) refers to the number of write or read operations that can be performed each second. Transaction-intensive applications, such as database applications, are sensitive to IOPS.

    Common IOPS performance characteristics that are measured include sequential and random operations. The following table describes these performance characteristics.

    |Measurement|Description|
    |:----------|:----------|
    |Total IOPS|The total number of I/O operations per second|
    |Random read IOPS|The average number of random read I/O operations per second|Random access to locations on storage devices|
    |Random write IOPS|The average number of random write I/O operations per second|
    |Sequential read IOPS|The average number of sequential read I/O operations per second|Sequential access to locations on storage devices|
    |Sequential write IOPS|The average number of sequential write I/O operations per second|

-   **Throughput**

    Throughput measures the size of data successfully transferred per second.

    Applications that require mass read or write operations \(such as Hadoop offline computing applications\) are sensitive to throughput.

-   **Latency**

    Latency is the period that is needed to complete an I/O request.

    For latency-sensitive applications \(such as databases\) in which high latency may lead to performance reduction or error reports in applications, we recommend that you use ESSD disks, SSD disks, SSD Shared Block Storage, or local SSD disks.

    For throughput-sensitive applications \(such as Hadoop offline computing\) that are less sensitive to latency, we recommend that you use ECS instances with local HDD disks, such as instances of the d1 or d1ne instance type family.


## Performance {#section_ohf_x5t_fv7 .section}

Block storage capacity is measured in binary units, such as Kibibyte \(KiB\), Mebibyte \(MiB\), Gibibyte \(GiB\), or Tebibyte \(TiB\). This section describes the performance of different block storage devices.

**Note:** 1 KiB equals 1,024 bytes. 1MiB equals 1,024 KiB. 1GiB equals 1,024 MiB. 1TiB equals 1,024 GiB.

-   **Cloud disks**

    The following table lists the performance and typical scenarios of different types of cloud disks.

    |Measurement|ESSD cloud disk|SSD cloud disk|Ultra cloud disk|Basic cloud disk[\*\*\*](#cloud)|
    |:----------|:--------------|--------------|----------------|:-------------------------------|
    |Performance level \(PL\)|PL3|PL2|PL1|N/A|N/A|N/A|
    |Capacity of a single disk|32,768 GiB|32,768 GiB|32,768 GiB|2,000 GiB|
    |Max. IOPS|1,000,000|100,000|50,000|25,000[\*](#ssd)|5,000|Several hundreds|
    |Max. throughput|4,000 Mbit/s|750 Mbit/s|350 Mbit/s|300 Mbit/s[\*](#ssd)|140 Mbit/s|30−40 Mbit/s|
    |Formulas to calculate performance of a single disk[\*\*](#singledisk)|IOPS = min\{1,800 + 50 × capacity, 1,000,000\}|IOPS = min\{1,800 + 50 × capacity, 100,000\}|IOPS = min\{1,800 + 50 × capacity, 50,000\}|IOPS = min\{1,800 + 30 × capacity, 25,000\}|IOPS = min\{1,800 + 8 × capacity, 5,000\}|N/A|
    |Throughput = min \{120 + 0.5 × capacity, 4,000\} Mbit/s|Throughput = min \{120 + 0.5 × capacity, 750\} Mbit/s|Throughput = min \{120 + 0.5 × capacity, 3500\} Mbit/s|Throughput = min\{120 + 0.5 × capacity, 300\} Mbit/s|Throughput = min\{100 + 0.15 × capacity, 140\} Mbit/s|N/A|
    |Data reliability|99.9999999%|99.9999999%|99.9999999%|99.9999999%|
    |API name|cloud\_essd|cloud\_ssd|cloud\_efficiency|cloud|
    |Scenarios|     -   OLTP databases: relational databases such as MySQL, PostgreSQL, Oracle, and SQL Server
    -   NoSQL databases: non-relational databases such as MongoDB, HBase, and Cassandra
    -   ElasticSearch distributed logs: Elasticsearch, Logstash, and Kibana \(ELK\) log analysis
 |     -   Large and medium-sized relational databases, such as MySQL, SQL Server, PostgreSQL, and Oracle
    -   Large and medium-sized development or testing applications that require high data reliability
 |     -   Development and testing applications
    -   System disk
 |     -   Applications with infrequent access or low I/O load. If higher I/O performance is needed, we recommend that you use SSD disks.
    -   Applications that require low costs and random read and write I/O operations
 |

    \*The performance of SSD cloud disks varies according to the size of the data blocks. Smaller data blocks result in lower throughput and higher IOPS, as described in the following table. An SSD cloud disk can achieve a suitable IOPS performance only when it is attached to an I/O-optimized instance.

    |Data block size|Maximum IOPS|Throughput|
    |:--------------|:-----------|:---------|
    |4 KiB|About 25,000|About 100 Mbit/s|
    |16 KiB|About 17,200|About 260 Mbit/s|
    |32 KiB|About 9,600|About 300 Mbit/s|
    |64 KiB|About 4,800|About 300 Mbit/s|

    \*\*An SSD cloud disk is taken as an example to describe the performance of a single disk:

    -   The maximum IOPS: The baseline is 1,800 IOPS. It increases by 30 IOPS per GiB of storage. The maximum IOPS is 25,000.
    -   The maximum throughput: The baseline is 120 Mbit/s. It increases by 0.5 Mbit/s per GiB of storage. The maximum throughput is 300 Mbit/s.
    The random write latency varies according to disk categories. For the test commands, see [Performance tests](#).

    -   ESSD cloud disks: 0.2 ms
    -   SSD cloud disks: 0.5−2 ms
    -   Ultra cloud disks: 1−3 ms
    -   Basic cloud disks: 5−10 ms
    \*\*\*Basic cloud disks are last-generation cloud disks that are scheduled to be discontinued. We recommend that you use one of the newer cloud disk products that have better performance, such as Ultra cloud disks or SSD cloud disks.

-   **Shared Block Storage**

    The following table lists the performance and typical scenarios of different types of Shared Block Storage.

    |Measurement|SSD Shared Block Storage|Ultra Shared Block Storage|
    |:----------|:-----------------------|:-------------------------|
    |Maximum capacity|     -   Singe disk: 32,768 GiB
    -   Single instance: 128 TiB
 |     -   Singe disk: 32,768 GiB
    -   Single instance: 128 TiB
 |
    |Maximum random read/write IOPS[\*](#IOPS)|30,000|5,000|
    |Maximum sequential read/write throughput[\*](#IOPS)|512 Mbit/s|160 Mbit/s|
    |Formulas to calculate performance of a single disk[\*\*](#singledisk2)|IOPS = min\{1,600 + 40 × capacity, 30,000\}|IOPS = min\{1,000 + 6 × capacity, 5,000\}|
    |Throughput = min\{100 + 0.5 × capacity, 512\} Mbit/s|Throughput = min\{50 + 0.15 × capacity, 160\} Mbit/s|
    |Scenarios|     -   Oracle RAC
    -   Failover cluster
    -   High-availability architecture of servers
 |     -   High-availability architecture of servers
    -   High-availability architecture of development and testing databases
 |

    \* The maximum IOPS and throughput listed in the preceding table are the maximum performance of a bare Shared Block Storage device that is attached to two or more instances at the same time during stress tests.

    \*\* An SSD Shared Block Storage device is used as an example to describe the performance of a single disk:

    -   The maximum IOPS: The baseline is 1,600 IOPS. It increases by 40 IOPS per GiB of storage. The maximum IOPS is 30,000.
    -   The maximum throughput: The baseline is 100 Mbit/s. It increases by 0.5 Mbit/s per GiB of storage. The maximum throughput is 512 Mbit/s.
    The latency varies according to the Shared Block Storage categories as follows:

    -   SSD Shared Block Storage: 0.5−2 ms
    -   Ultra Shared Block Storage: 1−3 ms
-   **Local disks**

    For the performance of local disks, see [Local disks](reseller.en-US/Block Storage/Local disks.md#).


## Performance tests {#section_75g_wvn_nhi .section}

The FIO tool is recommended for testing block storage performance for both Linux and Windows instances.

**Note:** You can also use other tools to test block storage performance, but the resulting benchmark performance may be different. For example, tools like dd, sysbench, and iometer may be affected by test parameter configuration and file systems, and may not reflect the actual disk performance. The performance results in this topic are from a Linux instance tested with FIO, and are used as the performance reference of Shared Block Storage products. Before you test the disk, verify that the disk is 4 KiB aligned.

**Warning:** You can test bare disks to obtain more accurate performance data, but the structure of the file system will be damaged. Make sure that you back up your data before testing. We recommend that you use a new ECS instance without data to test the disks to avoid data loss.

-   Test random write IOPS:

    ``` {#codeblock_lh0_vbj_uun}
    fio -direct=1 -iodepth=128 -rw=randwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Write_Testing
    ```

-   Test random read IOPS:

    ``` {#codeblock_9l3_bbu_lza}
    fio -direct=1 -iodepth=128 -rw=randread -ioengine=libaio -bs=4k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Rand_Read_Testing
    ```

-   Test sequential write throughput:

    ``` {#codeblock_dlz_dzt_gyt}
    fio -direct=1 -iodepth=64 -rw=write -ioengine=libaio -bs=1024k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Write_PPS_Testing
    ```

-   Test sequential read throughput:

    ``` {#codeblock_srw_c33_cy6}
    fio -direct=1 -iodepth=64 -rw=read -ioengine=libaio -bs=1024k -size=1G -numjobs=1 -runtime=1000 -group_reporting -filename=iotest -name=Read_PPS_Testing
    ```

-   Test random write latency:

    ``` {#codeblock_196_knh_ctf}
    fio -direct=1 -iodepth=1 -rw=randwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -group_reporting -filename=iotest -name=Rand_Write_Latency_Testing
    ```

-   Test random read latency:

    ``` {#codeblock_wir_7ek_98p}
    fio -direct=1 -iodepth=1 -rwfio -direct=1 -iodepth=1 -rw=randread -ioengine=libaio -bs=4k -size=1G -numjobs=1 -group_reporting -filename=iotest -name=Rand_Read_Latency_Testingrandwrite -ioengine=libaio -bs=4k -size=1G -numjobs=1 -group_reporting -filename=iotest -name=Rand_Write_Latency_Testing
    ```


The command for testing random write IOPS is used as an example to describe the meaning of the parameters of a FIO command, as described in the following table.

|Parameter|Description|
|:--------|:----------|
|-direct=1|Ignore I/O buffer when testing. Data is written directly.|
|-iodepth=128|Indicates that when you use AIO, up to 128 I/O requests can be made at the same time.|
|-rw=randwrite|Indicates that the read and write policy is random write. Other options include: -   randread \(random read\)
-   read \(sequential read\)
-   write \(sequential write\)
-   randrw \(random read and write\)

 |
|-ioengine=libaio|Use libaio as the testing method \(Linux AIO, Asynchronous I/O\). Usually there are two ways for an application to use I/O: -   Synchronous I/O

In synchronous I/O, a thread sends out only one I/O request at a time and waits until the I/O request has completed. In this case, the iodepth is always less than 1 for a single job, which means low processing efficiency. You can increase the iodepth by using multiple concurrent jobs. Usually 16−32 concurrent jobs can fill up the iodepth.

-   Asynchronous I/O

The asynchronous method uses libaio to submit a batch of I/O requests each time, thus reducing interaction times and making interactions more efficient.


 |
|-bs=4k| Indicates the size of each block for one I/O is 4 KiB. If not specified, the default value 4 KiB is used.

 When IOPS is tested, we recommend that you set `bs` to a small value, such as 4k in this example command.

 When throughput is tested, we recommend that you set `bs` to a large value, such as 1,024k in this example command.

 |
|-size=1G|Indicates the size of the testing file is 1 GiB.|
|-numjobs=1|The number of testing jobs is 1.|
|-runtime=1000|Testing time is 1,000 seconds. If not specified, the test will write data of the file whose size is specified by `-size` block by block, with the data block size specified by `-bs`.|
|-group\_reporting|The display mode of the testing results. Group\_reporting means the statistics of each job are summed up, instead of showing all statistics of each job.|
|-filename=iotest|The name of the test files, for example, iotest. You can test bare disks to obtain more accurate performance data, but the test causes damage to the structure of the file system. Make sure that you back up your data before testing.|
|-name=Rand\_Write\_Testing|The name of the testing task.|

