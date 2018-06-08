# Triplicate technology {#concept_pnm_hdw_ydb .concept}

The Alibaba Cloud distributed File System provides stable and efficient data access and reliability for ECS. Triplicate technology, that is, the process of triple replication of data, is the priciple concept designed by Alibaba Cloud and implemented in the Distributed File System.

## Chunks {#section_lgj_jdw_ydb .section}

The read and write to Virtual Disks by ECS users are finally mapped as read and write to the files on the Alibaba Cloud data storage platform. The Distributed File System of Alibaba Cloud uses a flat design in which a linear address space is divided into slices, also called chunks. Each chunk has three copies stored on different server nodes on different racks. This guarantees data reliability.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9559/5222_en-US.png)

## How triplicate technology works {#section_ngj_jdw_ydb .section}

Triplicate technology involves three key components: Master, Chunk Server, and Client. To demonstrate how triplicate technology works, in this example, the write operation of an ECS user undergoes several conversions before being executed by the Client. The process is as follows:

1.  The Client determines the location of a chunk corresponding to one of your write operations.
2.  The Client sends a request to the Master to query the storage locations \(that is, the Chunk Servers\) of the three copies of the chunk.
3.  he Client sends write requests to the corresponding three Chunk Servers according to the results returned from the Master.
4.  The Client returns a message to the user indicating whether the operation was successful.

The distribution policy for the Mater takes into account all Chunk Server disk usage, distribution under different switch racks, power supply conditions, and load conditions, to ensure that all copies of one chunk are distributed on different Chunk Servers under different racks, avoiding data unavailability due to the breakdown of one Chunk Server or a rack.

## Data protection {#section_pgj_jdw_ydb .section}

If a system failure occurs because of a corrupted node or hard drive failure, some chunks may lose one or more of the three valid chunk copies associated with them. If this occurs and triplicate technology is enabled, the Master replicates data between Chunk Servers to reinstate the missing chunk copies across different nodes.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9559/5223_en-US.png)

Triplicate technology is strongly recommended to be used in conjunction with other data protection means, such as regular data backups or snapshots.

As for the loss of data in the ECS instance due to soft failures such as virus infection, human error removal, hacker intrusion, and so on, you need to use backup, [Snapshots](intl.en-US/Product Introduction/Snapshots.md#) and other technical means to solve. No technique solves all the problems, and the appropriate data protection measures build a solid line of defense for your valuable business data.

