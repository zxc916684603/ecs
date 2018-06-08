# Incremental snapshot mechanism {#concept_zbn_tzw_ydb .concept}

Alibaba Cloud provides the snapshot feature. You can create snapshots as scheduled. Save disk data at a specific time to guranttee the availability of your business. 

## Incremental snapshot mechanism {#section_yvf_5zw_ydb .section}

In this method, two snapshots are compared and only the data that has changed is copied. See the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9575/5243_en-US.jpg)

-   In the preceding figure, Snapshot 1, Snapshot 2, and Snapshot 3 are the first, second, and third snapshots of a disk.  The file system checks the disk data by blocks. When a snapshot is created, only the blocks with changed data are copied to the snapshot. In this example:

    1.  In Snapshot 1, all data on the disk is copied because it is the first disk snapshot.
    2.  Snapshot 2 only copies the changed data blocks B1 and C1. Data blocks, A and D, are referenced from Snapshot 1.
    3.  Snapshot 3 copies the changed data block B2 but references data blocks, A, D, from Snapshot 1, and references C1 from Snapshot 2.
-   When you roll back the disk to Snapshot 3, blocks A, B2, C1, and D are copied to the disk, to replicate Snapshot 3.

-   When you delete Snapshot 2, block B1 is deleted, but block C1 is retained because blocks that are referenced by other snapshots cannot be deleted. When you roll back a disk to Snapshot 3, block C1 is recovered.


## Creation time {#section_cwf_5zw_ydb .section}

Snapshot creation time varies depending on actual volume to be copied.  It takes long time to create the first snapshot of a disk, because the snapshot copies the global data.  Then only the blocks with changed data are copied to a snapshot, which consumes shorter time.

## Influence of snapshot creation {#section_dwf_5zw_ydb .section}

When snapshot creation is in progress, the performance of a disk is reduced.

## Snapshot chains {#section_ewf_5zw_ydb .section}

A snapshot chain contains all snapshots of a disk. Each disk has one snapshot chain, and the snapshot chain ID is identical to the disk ID. A snapshot chain has the following information:

-   Snapshot quantity: The number of existing snapshots of a disk.

-   Snapshot capacity: The storage space that all the snapshots in the chain occupy.

    **Note:** The snapshot service charges according to the snapshot capacity. You can use the snapshot chain to check the snapshot capacity for each disk.

-   Snapshot quota: Each disk has a maximum of 64 snapshots. Therefore, each chain can have up to 64 snapshots, including manual and automatic snapshots.

    **Note:** When the snapshot quota is exceeded, if more automatic snapshots are to be created, the automatic snapshots are deleted automatically in a chronological order; if you want to create more snapshots manually, delete unnecessary snapshots manually.  For more information, see Apply an automatic snapshot policy to a disk and Delete a snapshot


