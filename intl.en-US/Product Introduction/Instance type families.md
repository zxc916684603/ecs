# Instance type families {#concept_sx4_lxv_tdb .concept}

An ECS instance is the minimal unit that can provide computing capabilities and services for your business.

ECS instances are categorized into specification types, which are called type families, based on the business scenarios they can be applied to. You may select multiple type families for one business scenario.

Each type family contains multiple ECS instance types with different CPU and memory specifications, including the CPU model and clock speed. Besides the instance type, you must also define a block storage, an image, and the network service when you create an instance.

**Note:** The availability of instance type families and their types varies from region to region. Go to the [purchase page](https://ecs-buy-intl.aliyun.com/#/prepay) to check the available instance types.

Alibaba Cloud ECS provides two kinds of instance type families: enterprise-level instance type families and entry-level instance type families. Type families for enterprise-level computing feature stable performance and dedicated resources, while entry-level type families are ideal for small and mid-sized websites, or individual customers. For the differences, see [Enterprise-level instances and entry-level instances FAQ](https://www.alibabacloud.com/help/faq-detail/44078.htm).

**Note:** If you are using sn1, sn2, t1, s1, s2, s3, m1, m2, c1, c2, n1, n2, or e3, see [Phased-out instance types](https://www.alibabacloud.com/help/faq-detail/55263.htm).

Alibaba Cloud ECS instances are categorized into the following type families:

-   Type families for enterprise-level computing on the x86-architecture:
    -   [g5, general-purpose type family](#g5)
    -   [sn2ne, general-purpose type family with enhanced network performance](#sn2ne)
    -   [ic5, intensive compute instance type family](#ic5)
    -   [c5, compute instance type family](#c5)
    -   [sn1ne, compute optimized type family with enhanced network performance](#sn1ne)
    -   [r5, memory instance type family](#r5)
    -   [se1ne, memory optimized type family with enhanced network performance](#se1ne)
    -   [se1, memory optimized type family](#se1)
    -   [d1ne, big data type family with enhanced network performance](#d1ne)
    -   [d1, big data type family](#d1)
    -   [i2, type family with local SSD disks](#i2)
    -   [i1, type family with local SSD disks](#i1)
    -   [hfc5, compute optimized type family with high clock speed](#hfc5)
    -   [hfg5, general-purpose type family with high clock speed](#hfg5)
    -   [c4, cm4, and ce4, compute optimized type family with high clock speed](#c4)
-   Type families for enterprise-level heterogeneous computing:
    -   [gn5, compute optimized type family with GPU](#gn5)
    -   [gn4, compute optimized type family with GPU](#gn4)
    -   [f1, compute optimized type family with FPGA](#f1)
    -   [f2, compute optimized type family with FPGA](#f2)
-   ECS Bare Metal Instance type families and Super Computing Cluster \(SCC\) instance type families:
    -   [ebmhfg5, ECS Bare Metal Instance type family with high clock speed](#ebmhfg5)
    -   [ebmc4, computing ECS Bare Metal Instance type family](#ebmc4)
    -   [ebmg5, general-purpose ECS Bare Metal Instance type family](#ebmg5)
    -   [scch5, Super Computing Cluster \(SCC\) instance type family with high clock speed \(Coming soon\)](#scch5)
    -   [sccg5, geneneral-purpose Super Computing Cluster \(SCC\) instance type family \(Coming soon\)](#sccg5)
-   Type families for entry-level computing on the x86-architecture:
    -   [t5, burstable instances](#t5)
    -   [xn4/n4/mn4/e4, type families of previous generations for entry-level users, computing on the x86-architecture](#xn4-n4-mn4-e4)

## g5, general-purpose type family {#g5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:4
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Enterprise-level applications of various types and sizes
    -   Medium and small database systems, cache, and search clusters
    -   Data analysis and computing
    -   Computing clusters and data processing reliant on memory

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\) [\*\*](#pps)|NIC queues [\*\*\*](#queue)|ENIs [\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:---------------------------------------------------|:--------------------------|:--------------------|
|ecs.g5.large|2|8.0|N/A|1.0|300|2|2|
|ecs.g5.xlarge|4|16.0|N/A|1.5|500|2|3|
|ecs.g5.2xlarge|8|32.0|N/A |2.5|800|2|4|
|ecs.g5.4xlarge|16|64.0|N/A |5.0|1,000|4|8|
|ecs.g5.6xlarge|24|96.0|N/A |7.5|1,500|6|8|
|ecs.g5.8xlarge|32|128.0|N/A |10.0|2,000|8|8|
|ecs.g5.16xlarge|64|256.0|N/A |20.0|4,000|16|8|

Click [here](#top) to view other instance type families.

## sn2ne, general-purpose type family with enhanced network performance {#sn2ne .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:4
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) or Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Enterprise-level applications of various types and sizes
    -   Medium and small database systems, cache, and search clusters
    -   Data analysis and computing
    -   Computing clusters and data processing depending on memory

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.sn2ne.large|2|8.0|N/A|1.0|300|2|2|
|ecs.sn2ne.xlarge|4|16.0|N/A|1.5|500|2|3|
|ecs.sn2ne. 2xlarge|8|32.0|N/A|2.0|1,000|4|4|
|ecs.sn2ne. 4xlarge|16|64.0|N/A|3.0|1,600|4|8|
|ecs.sn2ne. 8xlarge|32|128.0|N/A|6.0|2,500|8|8|
|ecs.sn2ne. 14xlarge|56|224.0|N/A|10.0|4,500|14|8|

**Note:** You can change the configurations of an sn2ne to any instance type in the sn2, sn2ne, sn1, sn1ne, se1, and se1ne instance type family.

Click [here](#top) to view other instance type families.

## ic5, intensive compute instance type family {#ic5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:1
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Web front-end servers
    -   Data analysis, batch compute, and video coding
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Massively Multiplayer Online \(MMO\) game front-ends

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.ic5.large|2|2.0|N/A|1.0|300|2|2|
|ecs.ic5.xlarge|4|4.0|N/A|1.5|500|2|3|
|ecs.ic5.2xlarge|8|8.0|N/A|2.5|800|2|4|
|ecs.ic5.3xlarge|12|12.0|N/A|4.0|900|4|6|
|ecs.ic5.4xlarge|16|16.0|N/A|5.0|1,000|4|8|

Click [here](#top) to view other instance type families.

## c5, compute instance type family {#c5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:2
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Web front-end servers
    -   Massively Multiplayer Online \(MMO\) game front-ends
    -   Data analysis, batch compute, and video coding
    -   High performance science and engineering applications

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.c5.large|2|4.0|N/A|1.0|300|2|2|
|ecs.c5.xlarge|4|8.0|N/A|1.5|500|2|3|
|ecs.c5.2xlarge|8|16.0|N/A|2.5|800|2|4|
|ecs.c5.4xlarge|16|32.0|N/A|5.0|1,000|4|8|
|ecs.c5.6xlarge|24|48.0|N/A|7.5|1,500|6|8|
|ecs.c5.8xlarge|32|64.0|N/A|10.0|2,000|8|8|
|ecs.c5.16xlarge|64|128.0|N/A|20.0|4,000|16|8|

Click [here](#top) to view other instance type families.

## sn1ne, compute optimized type family with enhanced network performance {#sn1ne .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:2
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) or Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Web front-end servers
    -   Massively Multiplayer Online \(MMO\) game front-ends
    -   Data analysis, batch compute, and video coding
    -   High performance science and engineering applications

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.sn1ne.large|2|4.0|N/A|1.0|300|2|2|
|ecs.sn1ne.xlarge|4|8.0|N/A|1.5|500|2|3|
|ecs.sn1ne.2xlarge|8|16.0|N/A|2.0|1,000|4|4|
|ecs.sn1ne.4xlarge|16|32.0|N/A|3.0|1,600|4|8|
|ecs.sn1ne.8xlarge|32|64.0|N/A|6.0|2,500|8|8|

**Note:** You can change the configurations of an sn1ne instance to any instance type in the sn2, sn2ne, sn1, sn1ne, se1, and se1ne instance type family.

Click [here](#top) to view other instance type families.

## r5, memory instance type family {#r5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Ultra high packet forwarding rate
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   High performance databases and high memory databases
    -   Data analysis and mining, and distributed memory cache
    -   Hadoop, Spark, and other enterprise-level applications with large memory requirements

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.r5.large|2|16.0|N/A|1.0|300|2|2|
|ecs.r5.xlarge|4|32.0|N/A|1.5|500|2|3|
|ecs.r5.2xlarge|8|64.0|N/A|2.5|800|2|4|
|ecs.r5.4xlarge|16|128.0|N/A|5.0|1,000|4|8|
|ecs.r5.6xlarge|24|192.0|N/A|7.5|1,500|6|8|
|ecs.r5.8xlarge|32|256.0|N/A|10.0|2,000|8|8|
|ecs.r5.16xlarge|64|512.0|N/A|20.0|4,000|16|8|

Click [here](#top) to view other instance type families.

## se1ne, memory optimized type family with enhanced network performance {#se1ne .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:8
-   Ultra high packet receive and forwarding rate
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) or Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   High performance databases and large memory databases
    -   Data analysis and mining, and distributed memory cache
    -   Hadoop, Spark, and other enterprise-level applications with large memory requirements

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.se1ne.large|2|16.0|N/A|1.0|300|2|2|
|ecs.se1ne.xlarge|4|32.0|N/A|1.5|500|2|3|
|ecs.se1ne.2xlarge|8|64.0|N/A|2.0|1,000|4|4|
|ecs.se1ne.4xlarge|16|128.0|N/A|3.0|1,600|4|8|
|ecs.se1ne.8xlarge|32|256.0|N/A|6.0|2,500|8|8|
|ecs.se1ne.14xlarge|56|480.0|N/A|10.0|4,500|14|8|

**Note:** You can change the configurations of an se1ne instance to any instance type in the sn2, sn2ne, sn1, sn1ne, se1, and se1ne instance type family.

Click [here](#top) to view other instance type families.

## se1, memory optimized type family {#se1 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:8
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   High performance databases and large memory databases
    -   Data analysis and mining, and distributed memory cache
    -   Hadoop, Spark, and other enterprise-level applications with large memory requirements

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\)|Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:-------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.se1.large|2|16.0|N/A|0.5|100|1|2|
|ecs.se1.xlarge|4|32.0|N/A|0.8|200|1|3|
|ecs.se1.2xlarge|8|64.0|N/A|1.5|400|1|4|
|ecs.se1.4xlarge|16|128.0|N/A|3.0|500|2|8|
|ecs.se1.8xlarge|32|256.0|N/A|6.0|800|3|8|
|ecs.se1.14xlarge|56|480.0|N/A|10.0|1,200|4|8|

**Note:** You can change the configurations of an se1 instance to any instance type in the sn2, sn2ne, sn1, sn1ne, se1, and se1ne instance type family.

Click [here](#top) to view other instance type families.

## d1ne, big data type family with enhanced network performance {#d1ne .section}

**Features**

-   High-volume local SATA HDD disks with high I/O throughput and up to 35 Gbit/s of bandwidth for a single instance
-   vCPU to memory ratio = 1:4, designed for big data scenarios
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Hadoop MapReduce, HDFS, Hive, HBase, and so on
    -   Spark in-memory computing, MLlib, and so on
    -   Enterprises that require big data computing and storage analysis, such as those in the Internet and finance industries, to store and compute massive volumes of data
    -   Elasticsearch, logs, and so on

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.d1ne.2xlarge|8|32.0|4 \* 5500|6.0|1,000|4|4|
|ecs.d1ne.4xlarge|16|64.0|8 \* 5500|12.0|1,600|4|8|
|ecs.d1ne.6xlarge|24|96.0|12 \* 5500|16.0|2,000|6|8|
|ecs.d1ne.8xlarge|32|128.0|16 \* 5500|20.0|2,500|8|8|
|ecs.d1ne.14xlarge|56|224.0|28 \* 5500|35.0|4,500|14|8|

**Note:** 

-   You cannot change configurations of d1ne instances.
-   For more information about d1ne type families, see [FAQ on d1 and d1ne](https://www.alibabacloud.com/help/faq-detail/52993.htm).

Click [here](#top) to view other instance type families.

## d1, big data type family {#d1 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   High-volume local SATA HDD disks with high I/O throughput and up to 17 Gbit/s of bandwidth for a single instance
-   vCPU to memory ratio = 1:4, designed for big data scenarios
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Hadoop MapReduce, HDFS, Hive, HBase, and so on
    -   Spark in-memory computing, MLlib, and so on
    -   Enterprises that require big data computing and storage analysis, such as those in the Internet and finance industries, to store and compute massive volumes of data
    -   Elasticsearch, logs, and so on

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.d1.2xlarge|8|32.0|4 \* 5500|3.0|300|1|4|
|ecs.d1.4xlarge|16|64.0|8 \* 5500|6.0|600|2|8|
|ecs.d1.6xlarge|24|96.0|12 \* 5500|8.0|800|2|8|
|ecs.d1-c8d3.8xlarge|32|128.0|12 \* 5500|10.0|1,000|4|8|
|ecs.d1.8xlarge|32|128.0|16 \* 5500|10.0|1,000|4|8|
|ecs.d1-c14d3.14xlarge|56|160.0|12 \* 5500|17.0|1,800|6|8|
|ecs.d1.14xlarge|56|224.0|28 \* 5500|17.0|1,800|6|8|

**Note:** 

-   You cannot change configurations of d1 instances.
-   For more information about d1 type families, see [FAQ on d1 and d1ne](https://www.alibabacloud.com/help/faq-detail/52993.htm).

Click [here](#top) to view other instance type families.

## i2, type family with local SSD disks {#i2 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   High-performance local NVMe SSD disks with high IOPS, high I/O throughput, and low latency.
-   vCPU to memory ratio = 1:8, designed for high performance databases
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   OLTP and high performance relational databases
    -   NoSQL databases, such as Cassandra and MongoDB
    -   Search applications, such as Elasticsearch 

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.i2.xlarge|4|32.0|1 \* 894|1.0|500|2|3|
|ecs.i2.2xlarge|8|64.0|1 \* 1788|2.0|1,000|2|4|
|ecs.i2.4xlarge|16|128.0|2 \* 1788|3.0|1,500|4|8|
|ecs.i2.8xlarge|32|256.0|4 \* 1788|6.0|2,000|8|8|
|ecs.i2.16xlarge|64|512.0|8 \* 1788|10.0|4,000|16|8|

**Note:** You cannot change configurations of i2 instances.

Click [here](#top) to view other instance type families.

## i1, type family with local SSD disks {#i1 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   High-performance local NVMe SSD disks with high IOPS, high I/O throughput, and low latency
-   vCPU to memory ratio = 1:4, designed for big data scenarios
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   OLTP and high performance relational databases
    -   NoSQL databases, such as Cassandra and MongoDB
    -   Search applications, such as Elasticsearch

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.i1.xlarge|4|16.0|2 \* 104|0.8|200|1|3|
|ecs.i1.2xlarge|8|32.0|2 \* 208|1.5|400|1|4|
|ecs.i1.4xlarge|16|64.0|2 \* 416|3.0|500|2|8|
|ecs.i1-c5d1.4xlarge|16|64.0|2 \* 1456|3.0|400|2|8|
|ecs.i1.8xlarge|32|128.0|2 \* 832|6.0|800|3|8|
|ecs.i1-c10d1.8xlarge|32|128.0|2 \* 1456|6.0|800|3|8|
|ecs.i1.14xlarge|56|224.0|2 \* 1456|10.0|1,200|4|8|

**Note:** You cannot change configurations of i1 instances.

Click [here](#top) to view other instance type families.

## hfc5, compute optimized type family with high clock speed {#hfc5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Stable performance
-   3.1 GHz Intel Xeon Gold 6149 \(Skylake\) processors
-   vCPU to memory ratio = 1:2
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   High performance Web front-end servers
    -   High performance Web front-end servers
    -   Massively Multiplayer Online \(MMO\) games and video coding

**Instance types**

|Instance type|vCPU|Memory \(GiB\)|Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:-------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.hfc5.large|2|4.0|N/A|1.0|300|2|2|
|ecs.hfc5.xlarge|4|8.0|N/A|1.5|500|2|3|
|ecs.hfc5.2xlarge|8|16.0|N/A|2.0|1,000|2|4|
|ecs.hfc5.4xlarge|16|32.0|N/A|3.0|1,600|4|8|
|ecs.hfc5.6xlarge|24|48.0|N/A|4.5|2,000|6|8|
|ecs.hfc5.8xlarge|32|64.0|N/A|6.0|2,500|8|8|

**Note:** You can change the configurations of an hfc5 instance to any instance type in the hfc5 and hfg5 instance type families.

Click [here](#top) to view other instance type families.

## hfg5, general-purpose type family with high clock speed {#hfg5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Stable performance
-   3.1 GHz Intel Xeon Gold 6149 \(Skylake\) processors
-   vCPU to memory ratio = 1:4, except for the 56 vCPU instance type
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   High performance Web front-end servers
    -   High performance science and engineering applications
    -   Massively Multiplayer Online \(MMO\) games and video coding

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.hfg5.large|2|8.0|N/A|1.0|300|2|2|
|ecs.hfg5.xlarge|4|16.0|N/A|1.5|500|2|3|
|ecs.hfg5.2xlarge|8|32.0|N/A|2.0|1,000|2|4|
|ecs.hfg5.4xlarge|16|64.0|N/A|3.0|1,600|4|8|
|ecs.hfg5.6xlarge|24|96.0|N/A|4.5|2,000|6|8|
|ecs.hfg5.8xlarge|32|128.0|N/A|6.0|2,500|8|8|
|ecs.hfg5.14xlarge|56|160.0|N/A|10.0|4,000|14|8|

**Note:** You can change the configurations of an hfg5 instance to any instance type in the hfc5 and hfg5 instance type families.

Click [here](#top) to view other instance type families.

## c4, cm4, and ce4, compute optimized type family with high clock speed {#c4 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Stable performance
-   3.2 GHz Intel Xeon E5-2667 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   High performance Web front-end servers
    -   High performance science and engineering applications
    -   Massively Multiplayer Online \(MMO\) games and video coding

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.c4.xlarge|4|8.0|N/A|1.5|200|1|3|
|ecs.c4.2xlarge|8|16.0|N/A|3.0|400|1|4|
|ecs.c4.4xlarge|16|32.0|N/A|6.0|800|2|8|
|ecs.cm4.xlarge|4|16.0|N/A|1.5|200|1|3|
|ecs.cm4.2xlarge|8|32.0|N/A|3.0|400|1|4|
|ecs.cm4.4xlarge|16|64.0|N/A|6.0|800|2|8|
|ecs.cm4.6xlarge|24|96.0|N/A|10.0|1,200|4|8|
|ecs.ce4.xlarge|4|32.0|N/A|1.5|200|1|3|

Click [here](#top) to view other instance type families.

## gn5, compute optimized type family with GPU {#gn5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   NVIDIA P100 GPU processors
-   No fixed ratio of vCPU to memory
-   High performance local NVMe SSD disks
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Deep learning
    -   Scientific computing, such as computational fluid dynamics, computational finance, genomics, and environmental analysis
    -   High performance computing, rendering, multi-media coding and decoding, and other server-side GPU compute workloads

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|GPU|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.gn5-c4g1.xlarge|4|30.0|440|1 \* NVIDIA P100|3.0|300|1|3|
|ecs.gn5-c8g1.2xlarge|8|60.0|440|1 \* NVIDIA P100|3.0|400|1|4|
|ecs.gn5-c4g1.2xlarge|8|60.0|880|2 \* NVIDIA P100|5.0|1,000|2|4|
|ecs.gn5-c8g1.4xlarge|16|120.0|880|2 \* NVIDIA P100|5.0|1,000|4|8|
|ecs.gn5-c28g1.7xlarge|28|112.0|440|1 \* NVIDIA P100|5.0|1,000|8|8|
|ecs.gn5-c8g1.8xlarge|32|240.0|1760|4 \* NVIDIA P100|10.0|2,000|8|8|
|ecs.gn5-c28g1.14xlarge|56|224.0|880|2 \* NVIDIA P100|10.0|2,000|14|8|
|ecs.gn5-c8g1.14xlarge|54|480.0|3520|8 \* NVIDIA P100|25.0|4,000|14|8|

**Note:** 

-   For more information, see [Create a gn4 or a gn5 instance](../../../../intl.en-US/User Guide/Instances/Create an instance/Create a gn4 or a gn5 instance.md#).
-   You cannot change configurations of gn5 instances.

Click [here](#top) to view other instance type families.

## gn4, compute optimized type family with GPU {#gn4 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   NVIDIA M40 GPU processors
-   No fixed ratio of CPU to memory
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Deep learning
    -   Scientific computing, such as computational fluid dynamics, computational finance, genomics, and environmental analysis
    -   High performance computing, rendering, multi-media coding and decoding, and other server-side GPU compute workloads

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|GPU|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.gn4-c4g1.xlarge|4|30.0|N/A|1 \* NVIDIA M40|3.0|300|1|3|
|ecs.gn4-c8g1.2xlarge|8|60.0|N/A|1 \* NVIDIA M40|3.0|400|1|4|
|ecs.gn4.8xlarge|32|48.0|N/A|1 \* NVIDIA M40|6.0|800|3|8|
|ecs.gn4-c4g1.2xlarge|8|60.0|N/A|2 \* NVIDIA M40|5.0|500|1|4|
|ecs.gn4-c8g1.4xlarge|16|60.0|N/A|2 \* NVIDIA M40|5.0|500|1|8|
|ecs.gn4.14xlarge|56|96.0|N/A|2 \* NVIDIA M40|10.0|1,200|4|8|

**Note:** 

-   For more information, see [Create a gn4 or a gn5 instance](../../../../intl.en-US/User Guide/Instances/Create an instance/Create a gn4 or a gn5 instance.md#).
-   You can change the configurations of a gn4 instance within the gn4 family.

Click [here](#top) to view other instance type families.

## f1, compute optimized type family with FPGA {#f1 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Intel ARRIA 10 GX 1150 FPGA
-   vCPU to memory ratio = 1:7.5
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Deep learning and reasoning
    -   Genomics research
    -   Financial analysis
    -   Picture transcoding
    -   Computational workloads, such as real-time video processing and security

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|FPGA|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:---|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.f1-c8f1.2xlarge|8|60.0|N/A|Intel ARRIA 10 GX 1150|3.0|400|4|4|
|ecs.f1-c28f1.7xlarge|28|112.0|N/A|Intel ARRIA 10 GX 1150|5.0|2,000|8|8|

**Note:** You cannot change configurations of f1 instances.

Click [here](#top) to view other instance type families.

## f2, compute optimized type family with FPGA {#f2 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Xilinx Kintex UltraScale XCKU115
-   vCPU to memory ratio = 1:7.5
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   Higher computing specifications matching higher network performance
-   Ideal for:
    -   Deep learning and reasoning
    -   Genomics research
    -   Financial analysis
    -   Picture transcoding
    -   Computational workloads, such as real-time video processing and security

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|FPGA|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:---|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.f2-c8f1.2xlarge|8|60.0|N/A|Xilinx Kintex UltraScale XCKU115|2.0|800|4|4|
|ecs.f2-c8f1.4xlarge|16|120.0|N/A|2 \* Xilinx Kintex UltraScale XCKU115|5.0|1,000|4|8|
|ecs.f2-c28f1.7xlarge|28|112.0|N/A|Xilinx Kintex UltraScale XCKU115|5.0|1,000|8|8|
|ecs.f2-c28f1.14xlarge|56|224.0|N/A|2 \* Xilinx Kintex UltraScale XCKU115|10.0|2,000|14|8|

**Note:** You cannot change configurations of f2 instances.

Click [here](#top) to view other instance type families.

## ebmhfg5, ECS Bare Metal Instance type family with high clock speed {#ebmhfg5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:4
-   3.7 GHz Intel Xeon E3-1240v6 \(Skylake\) processors, 8-core vCPU, up to 4.1 GHz Turbo Boot
-   High network performance: 2 million pps packet forwarding rate
-   Supports VPC network only
-   Provides dedicated hardware resources and physical isolation
-   Supports Intel SGX
-   Ideal for:
    -   Workloads that require direct access to physical resources, or scenarios where binding a license to the hardware is required
    -   Gaming or financial applications featuring high performance
    -   High performance Web servers
    -   Enterprise-level applications, such as high performance databases

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENISs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:--------------------|
|ecs.ebmhfg5.2xlarge|8|32.0|N/A|6.0|2,000|8|6|

**Note:** For more information about ECS Bare Metal Instance, see [ECS Bare Metal Instance and Super Computing Clusters](intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

Click [here](#top) to view other instance type families.

## ebmc4, computing ECS Bare Metal Instance type family {#ebmc4 .section}

**Feature**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:2
-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors, up to 2.9 GHz Turbo Boot
-   High network performance: 4 million pps packet forwarding rate
-   Supports VPC network only
-   Provides dedicated hardware resources and physical isolation
-   Ideal for:
    -   Scenarios where a large volume of packets are received and transmitted, such as the re-transmission of telecommunication services
    -   Enterprise-level applications of various types and sizes
    -   Medium and large database systems, caches, and search clusters
    -   Data analysis and computing

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.ebmc4.8xlarge|32|64.0|N/A|10.0|4,000|8|12|

**Note:** For more information about ECS Bare Metal Instance, see [ECS Bare Metal Instance and Super Computing Clusters](intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

Click [here](#top) to view other instance type families.

## ebmg5, general-purpose ECS Bare Metal Instance type family {#ebmg5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   vCPU to memory ratio = 1:4
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors, 96-core vCPU, up to 2.7 GHz Turbo Boot
-   High network performance: 4.5 million pps packet forwarding rate
-   Supports VPC network only
-   Provides dedicated hardware resources and physical isolation
-   Ideal for:
    -   Workloads that require direct access to physical resources, or scenarios where binding a license to the hardware is required
    -   Third-party virtualization \(includes but is not limited to Xen and KVM\), and AnyStack \(includes but is not limited to OpenStack and ZStack\)
    -   Containers \(includes but is not limited to Docker, Clear Container, and Pouch\)
    -   Enterprise-level applications, such as medium and large databases
    -   Video coding

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.ebmg5.24xlarge|96|384.0|N/A|10.0|4,500|8|32|

**Note:** For more information about ECS Bare Metal Instance, see [ECS Bare Metal Instance and Super Computing Clusters](intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

Click [here](#top) to view other instance type families.

## scch5, Super Computing Cluster \(SCC\) instance type family with high clock speed \(Coming soon\) {#scch5 .section}

**Features**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Supports both RoCE and VPC networks, of which RoCE is dedicated to RDMA communication
-   With all features of ECS Bare Metal Instance
-   3.1 GHz Intel Xeon Gold 6149 \(Skylake\) processors
-   vCPU to memory ratio = 1:3
-   Ideal for:
    -   Large-scale machine learning applications
    -   Large-scale high-performance scientific and engineering applications
    -   Large-scale data analysis, batch computing, video encoding

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |GPU|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|RoCE \(Inbound/Outbound\) \(Gbit/s\) |NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:--|:--------------------|:--------------------------------------------------|:------------------------------------|:-------------------------|:-------------------|
|ecs.scch5.16xlarge|64|192.0|N/A|10.0|4,500|46|12|32|

**Note:** For more information about SCC, see [ECS Bare Metal Instance and Super Computing Clusters](intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

Click [here](#top) to view other instance type families.

## sccg5, geneneral-purpose Super Computing Cluster \(SCC\) instance type family \(Coming soon\) {#sccg5 .section}

**Feature**

-   I/O-optimized
-   Supports SSD Cloud Disks and Ultra Cloud Disks
-   Supports both RoCE and VPC networks, of which RoCE is dedicated to RDMA communication
-   With all features of ECS Bare Metal Instance
-   2.5 GHz Intel Xeon Platinum 8163 \(Skylake\) processors
-   vCPU to memory ratio = 1:4
-   Ideal for:
    -   Large-scale machine learning applications
    -   Large-scale high-performance scientific and engineering applications
    -   Large-scale data analysis, batch computing, video encoding

**Instance types**

|Instance type|vCPU|Memory \(GiB\) |GPU|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|RoCE \(Inbound/Outbound\) \(Gbit/s\) |NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:--|:--------------------|:--------------------------------------------------|:------------------------------------|:-------------------------|:-------------------|
|ecs.sccg5.24xlarge|96|384.0|N/A|10.0|4,500|46|12|32|

**Note:** For more information about SCC, see [ECS Bare Metal Instance and Super Computing Clusters](intl.en-US/Product Introduction/Instances/ECS Bare Metal Instance and Super Computing Clusters.md#).

Click [here](#top) to view other instance type families.

## t5, burstable instances {#t5 .section}

**Features**

-   2.5 GHz Intel Xeon processors
-   The latest DDR4 memory
-   No fixed ratio of vCPU to memory
-   Baseline CPU performance, burstable, but restricted by accumulated CPU credits
-   Resource balance among compute, memory, and networks
-   Supports VPC network only
-   Ideal for:
    -   Web application servers
    -   Lightweight web servers
    -   Development and testing environments

**Instance types**

|Type|vCPU|Memory \(GiB\) |CPU credits/hour |Max CPU credit balance |Avg baseline CPU performance|ENIs[\*\*\*\*](#eni)|
|:---|:---|:--------------|:----------------|:----------------------|:---------------------------|:-------------------|
|ecs.t5-lc2m1.nano|1|0.5|6|144|10%|1|
|ecs.t5-lc1m1.small|1|1.0|6|144|10%|1|
|ecs.t5-lc1m2.small|1|2.0|6|144|10%|1|
|ecs.t5-lc1m2.large|2|4.0|12|288|10%|1|
|ecs.t5-lc1m4.large|2|8.0|12|288|10%|1|
|ecs.t5-c1m1.large|2|2.0|18|432|15%|1|
|ecs.t5-c1m2.large|2|4.0|18|432|15%|1|
|ecs.t5-c1m4.large|2|8.0|18|432|15%|1|
|ecs.t5-c1m1.xlarge|4|4.0|36|864|15%|2|
|ecs.t5-c1m2.xlarge|4|8.0|36|864|15%|2|
|ecs.t5-c1m4.xlarge|4|16.0|36|864|15%|2|
|ecs.t5-c1m1.2xlarge|8|8.0|72|1728|15%|2|
|ecs.t5-c1m2.2xlarge|8|16.0|72|1728|15%|2|
|ecs.t5-c1m4.2xlarge|8|32.0|72|1728|15%|2|
|ecs.t5-c1m1.4xlarge|16|16.0|144|1728|15%|2|
|ecs.t5-c1m2.4xlarge|16|32.0|144|1728|15%|2|

**Note:** For more information about t5, see [Burstable instances](intl.en-US/Product Introduction/Instances/Burstable instances.md#).

Click [here](#top) to view other instance type families.

## xn4/n4/mn4/e4, type families of previous generations for entry-level users, computing on the x86-architecture {#xn4-n4-mn4-e4 .section}

**Features**

-   2.5 GHz Intel Xeon E5-2682 v4 \(Broadwell\) processors
-   The latest DDR4 memory
-   No fixed ratio of CPU to memory

|Type family |Features|vCPU to memory ratio |Ideal for|
|:-----------|:-------|:--------------------|:--------|
|xn4|Compact entry-level instances|1:1| -   Front ends of Web applications
-   Light load applications and microservices
-   Applications for development or testing environments

 |
|n4|General entry-level instances |1:2| -   Websites and Web applications
-   Development environment, building servers, code repositories, microservices, and testing and staging environment
-   Lightweight enterprise applications

 |
|mn4|Balanced entry-level instances|1:4| -   Websites and Web applications
-   Lightweight databases and cache
-   Integrated applications and lightweight enterprise services

 |
|e4|Memory entry-level instances |1:8| -   Applications that require large volume of memory
-   Lightweight databases and cache

 |

**Note:** You can change the configurations of an instance between any two type families of xn4, n4, mn4, and e4, and within the same instance type family.

**xn4**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues [\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:-------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:--------------------------|:-------------------|
|ecs.xn4.small|1|1.0|N/A|0.5|50|1|1|

**n4**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues [\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:-------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:--------------------------|:-------------------|
|ecs.n4.small|1|2.0|N/A|0.5|50|1|1|
|ecs.n4.large|2|4.0|N/A|0.5|100|1|1|
|ecs.n4.xlarge|4|8.0|N/A|0.8|150|1|2|
|ecs.n4.2xlarge|8|16.0|N/A|1.2|300|1|2|
|ecs.n4.4xlarge|16|32.0|N/A|2.5|400|1|2|
|ecs.n4.8xlarge|32|64.0|N/A|5.0|500|1|2|

**mn4**

|Instance type |vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:-------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.mn4.small|1|4.0|N/A|0.5|50|1|1|
|ecs.mn4.large|2|8.0|N/A|0.5|100|1|1|
|ecs.mn4.xlarge|4|16.0|N/A|0.8|150|1|2|
|ecs.mn4.2xlarge|8|32.0|N/A|1.2|300|1|2|
|ecs.mn4.4xlarge|16|64.0|N/A|2.5|400|1|2|

**e4**

|Instance type|vCPU|Memory \(GiB\) |Local disks \(GiB\)[\*](#localdisk)|Bandwidth \(Gbit/s\) |Packet forwarding rate \(Thousand pps\)[\*\*](#pps)|NIC queues[\*\*\*](#queue)|ENIs[\*\*\*\*](#eni)|
|:------------|:---|:--------------|:----------------------------------|:--------------------|:--------------------------------------------------|:-------------------------|:-------------------|
|ecs.e4.small|1|8.0|N/A|0.5|50|1|1|

Click [here](#top) to view other instance type families.

\* Cache disks, or Local disks, are the disks located on the physical servers \(host machines\) that ECS instances are hosted on. They provide temporary block level storage for instances. In some cases, such as when the computing resources of an instance, including CPU and memory, are released, or an instance is in the downtime migration, data on the local disks is erased. For more information, see [Local disks](intl.en-US/Product Introduction/Block storage/Local disks.md#).

\*\* The maximum packet forwarding rate of inbound or outbound traffic. For more information about packet forwarding rate testing, see [Test network performance](https://www.alibabacloud.com/help/faq-detail/55757.htm).

\*\*\* The maximum number of NIC queues that an instance type supports. If your instance is running CentOS 7.3, the maximum number of NIC queues is used by default.

\*\*\*\* An enterprise-level instance with two or more vCPU cores supports elastic network interfaces. An entry-level instance with four or more vCPU cores supports elastic network interfaces. For more information about elastic network interfaces, see [Elastic network interfaces](intl.en-US/Product Introduction/Network and security/Elastic network interfaces.md#).

