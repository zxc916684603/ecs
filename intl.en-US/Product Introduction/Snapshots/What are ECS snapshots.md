# What are ECS snapshots {#concept_qft_2zw_ydb .concept}

A snapshot is a copy of data on an elastic block storage device at a given time point. For more information about how snapshots are created, see Incremental snapshot mechanism.

**Note:** Creation of a snapshot may reduce the I/O performance of a block storage device, generally by less than 10%, resulting in sharp decrease in I/O speed. We recommend that you create snapshots during off-peak business hours.

## Features {#section_usk_hzw_ydb .section}

Currently, Alibaba Cloud provides Snapshot 2.0 service. Compared with the former version, Snapshot 2.0 has better performance in capacity limit, scalability, cost, and usability. For more information, see ECS Snapshot 2.0 vs. traditional storage products.

**Note:** The Snaphsot 2.0 service is currently online. Unless and otherwise specified, either “snapshot” or “snapshot service” in all ECS articles is assumed as Snaphsot 2.0 service.

## Scenarios {#section_vsk_hzw_ydb .section}

The snapshot service meets your requirements, such as:

-   Creating an elastic block storage device that has the data of an existing storage device. For example, by using the snapshot service, you can create a cloud disk from a snapshot.
-   Restoring the data on an elastic block storage device. You can roll back the storage device from a snapshot. For example, when the data on an elastic block storage device is incorrect caused by an application error or the data is maliciously tampered by hackers by using an application vulnerability, you can use its snapshot to restore its data to the expected status.
-   Creating multiple copies of production data. You can create a custom image from a snapshot of a system disk of an existing instance, and then create the image to create a new instance.

For more information, see Scenarios.

## Classification {#section_xsk_hzw_ydb .section}

Snapshots are classified into two categories:

-   Manual snapshots, which are created manually. You can create snapshots for an elastic block storage device at any time to back up data.
-   Auto snapshots, which are created automatically according to the automatic snapshot policy applied to an elastic block storage device. You can create an automatic snapshot policy and apply it to the storage device. Then snapshots will be created automatically at the given time points.

## Snapshot charges {#section_z5d_lzw_ydb .section}

Currently, the snapshot service is free of charge.

## View the size of snapshots {#section_awh_nzw_ydb .section}

A snapshot chain of an elastic block storage device is created once the first snapshot is created. You can view the total size of the snapshots of an elastic block storage device by using the **Snapshot Chain** feature in the ECS console.

## Encryption {#section_btk_hzw_ydb .section}

All the snapshots of encrypted cloud disks or shared block storage are encrypted. These snapshots are called encrypted snapshots. Encrypted snapshots cannot be converted to unencrypted snapshots, and vice versa. For more information, see ECS disk encryption.

## Delete snapshots {#section_ctk_hzw_ydb .section}

If your business no longer requires a snapshot of an elastic block storage device, you can delete the snapshot. If you have applied an automatic snapshot policy to the storage device, you can delete the automatic snapshot policy.

