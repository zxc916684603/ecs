# Snapshot concepts {#concept_zbn_tzw_ydb .concept}

Alibaba Cloud ECS offers the snapshot service to create snapshots for disks and Shared Block Storage \(hereinafter referred to as disks\) as scheduled operations. Such operations allow you to retain disk data for one or more specific points in time. Snapshots can guarantee service security while also improving your application deployment efficiency.

## Incremental snapshots {#section_yvf_5zw_ydb .section}

After a disk is formatted, data blocks are divided based on logical block addressing \(LBA\). All service data that is written to data blocks is measured using snapshots. The first snapshot of a disk is a full snapshot that does not contain empty data blocks. Subsequent snapshots are incremental snapshots, which are copies of service data and dirty data generated since the last snapshot. Therefore, each data block is copied multiple times and is stored across multiple snapshots. The figure below illustrates the preceding concepts. In the figure, snapshots 1, 2, and 3 represent the first, second, and third snapshots of a disk.

![Incremental snapshots](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9575/15687129945243_en-US.jpg)

When a snapshot is created, the file system checks all the data blocks, and only data blocks with data changes are copied to the snapshot.

-   Snapshot 1 copies all data on the disk for the specific point in time that the snapshot is created.
-   Snapshot 2 copies only data blocks B1 and C1 that have been modified since snapshot 1. Data blocks A and D are referenced from snapshot 1.
-   Snapshot 3 copies only data block B2 that has been modified since snapshot 2. Data blocks A and D are referenced from snapshot 1, and data block C1 is referenced from snapshot 2.
-   If you roll back the disk to the state of snapshot 3, the **Roll Back Disk** feature copies data blocks A, B2, C1, and D to the disk to replicate snapshot 3.
-   If you delete snapshot 2, data block B1 is deleted, but data block C1 is retained because it is being referenced in other snapshots. If you roll back a disk to snapshot 3, data block C1 will still be recovered.

## Snapshot chain {#SnapshotChain .section}

A snapshot chain contains all snapshots of a specific disk. Each disk has a snapshot chain. The disk and the snapshot chain share an identical ID. A snapshot chain records the relationships between data blocks and contains the following information:

-   Snapshot capacity: the storage space occupied by each snapshot in the snapshot chain.

    **Note:** The snapshot service is billed by snapshot capacity. You can use the snapshot chain to check the snapshot capacity of each disk.

-   Snapshot quota: Each disk can have up to 256 manual snapshots and 256 automatic snapshots. For more information, see [Limits](../../../../reseller.en-US/Product Introduction/Limits.md#).

    **Note:** If the snapshot quota has been reached, but more automatic snapshots are required, the earliest automatic snapshots are deleted first to make room for new automatic snapshots. If you want to create manual snapshots, then you must first delete unneeded snapshots. For more information, see [Apply or disable an automatic snapshot policy](reseller.en-US/Snapshots/Automatic snapshot policies/Apply or disable an automatic snapshot policy.md#) and [Delete a snapshot](../../../../reseller.en-US/Snapshots/Use snapshots/Reduce snapshot fees.md#).

-   Snapshot node: Each node in the snapshot chain represents a snapshot of the corresponding disk. Each snapshot chain can have up to 512 snapshot nodes made up of 256 manual snapshot nodes and 256 automatic snapshot nodes.

## Snapshot deletion {#section_dkx_mpl_xdb .section}

If you no longer need a snapshot, you can delete it. If the number of snapshots exceeds the snapshot quota, you must delete some snapshots to release storage space. The figure below shows the workflow and logic when you delete a snapshot from a snapshot chain. In this example, snapshot S1 is deleted.

![Snapshot deletion](https://gw.alipayobjects.com/zos/onekb/GEmePRxTvdRaZPCgtUhF.png)

1.  Alibaba Cloud ECS analyzes all of the data blocks in snapshot S1 to be deleted, and then deletes the data blocks that are not referenced by other snapshots in the chain.
2.  Alibaba Cloud ECS adds the dirty data blocks of snapshot S1 to snapshot S2. Other snapshots record the information of 10 data blocks altogether:
    -   Six data blocks from snapshot S0
    -   Two dirty data blocks from snapshot S1
    -   Two data blocks from snapshot S2

