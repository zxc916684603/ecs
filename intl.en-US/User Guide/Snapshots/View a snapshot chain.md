# View a snapshot chain {#concept_w51_1rl_xdb .concept}

The snapshot service fee is related to the snapshot capacity. This article describes how to view the capacity of all snapshots on a single disk and all snapshot capacity on a region.

## View individual disk snapshot capacity {#section_cx4_3rl_xdb .section}

When you create snapshots of an elastic block storage device, such as a cloud disk or a shared block storage device, you can view the size of all the snapshots of the device by using the  **Snapshot Chain** feature in the ECS console.

A snapshot chain is composed of all the snapshots of an elastic block storage device. After you create a snapshot, the device has a snapshot chain. The chain has the identical ID with that of the device. A snapshot chain provides the following information:

-   Snapshot node: one node in the snapshot chain represents a single snapshot of the disk.
-   Snapshot nodes: Each snapshot node of the chain represents one snapshot of the device.
-   Snapshot capacity: The storage space occupied by all the snapshots of the device. Snapshot quota: Each device has up to 64 snapshots, including those created manually or automatically.

## Prerequisites {#section_gfm_srl_xdb .section}

You have [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#).

## Procedure {#section_a25_trl_xdb .section}

To view the total size of all the snapshots of an elastic block storage device, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, select **Snapshots & Images** \> **Snapshot list** .
4.  Find the disk ID of the snapshot. The disk should have at least one snapshot.

    ![](images/4574_en-US.png)

5.  In the left-side navigation pane, click **Snapshot Chain**.
6.  View all the snapshot capacities for the disk according to the disk ID that was found in step 4. You can view the total number and size of snapshots of the disk in the list.

    ![](images/4578_en-US.png)


In the **Actions** column, click **Details** to go to the  Snapshot Chain Details page. On the page, you can see all the snapshots of the disk, which you can use to [Roll back a cloud disk](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) or  [Create a custom mirror using a snapshot](intl.en-US/User Guide/Images/Create custom image/Create a custom mirror using a snapshot.md#).

## View all snapshot capacities under a region. {#section_sbv_2sl_xdb .section}

Follow these steps to view all snapshot capacities in a region:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-hand navigation bar, select **Snapshots & Images** \> **Snapshots** .

You can view the total number and size of snapshots of the disk in the list.

![](images/4581_en-US.png)

