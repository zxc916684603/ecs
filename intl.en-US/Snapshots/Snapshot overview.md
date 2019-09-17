# Snapshot overview {#concept_qft_2zw_ydb .concept}

A snapshot is a stateful data file of a disk or Shared Block Storage at a point in time. A snapshot is commonly used to back up data, restore data, and create custom images.

**Note:** When you create a snapshot, the I/O performance of Block Storage will degrade by up to 10%, resulting in a transient I/O speed decrease. We recommend that you create snapshots during off-peak hours.

## Scenarios {#section_b5r_krq_wgb .section}

You can use snapshots in the following scenarios to protect your data:

-   Disaster recovery and backup: Create snapshots for disks to be used as base data of other disks to implement zone-disaster recovery and geo-disaster recovery. For more information, see [Create a snapshot](reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#).
-   Version rollback: Roll back disks by using snapshots if system errors occur after an upgrade. For more information, see [Roll back a disk by using a snapshot](reseller.en-US/Snapshots/Use snapshots/Roll back a disk by using a snapshot.md#).
-   Environment duplication: Create an instance that has the same environment as an existing instance by creating a custom image from the system disk snapshot of the existing instance and then create an instance from the custom image. For more information, see [Create a custom image by using a snapshot](../../../../reseller.en-US/Images/Custom image/Create custom image/Create a custom image by using a snapshot.md#) and [Create an instance by using a custom image](../../../../reseller.en-US/Instances/Create an instance/Create an instance by using a custom image.md#).

-   Data development: Provide near-real-time data for applications such as data mining, report query, and development and test by creating snapshots of production data.
-   Data recovery and restoration:
    -   Restore the data on your disks by using snapshots in scenarios such as incorrect data being mistakenly stored on the disk, mistakenly released ECS instances, data errors caused by application errors, or malicious read and write operations.
    -   Use snapshots to regularly back up critical disk data and eliminate the risk of data loss resulting from incorrect operations, attacks, or viruses.
    -   Create one or more snapshots when you replace your OS, update your applications, or migrate your service data so that you can restore your data in the event any failure occurs.

## Snapshot types {#section_f5r_krq_wgb .section}

Snapshots can be categorized into the following types based on how they are created:

-   Manual snapshot: a disk snapshot that you manually create.
-   Automatic snapshot: a disk snapshot that is created automatically based on an automatic snapshot policy. You create and apply an automatic snapshot policy to a disk. Then ECS will create snapshots automatically for the disk at specified points in time. For information about automatic snapshot policies, see [Automatic snapshot policy overview](reseller.en-US/Snapshots/Automatic snapshot policies/Automatic snapshot policy overview.md#).

Snapshots can also be categorized into the following types based on the portion of data contained within them:

-   Full snapshot: the first snapshot of a disk that contains all of the data on the disk at the time of snapshot creation.
-   Incremental snapshot: a disk snapshot created after the initial full snapshot of a disk. An incremental snapshot contains the portion of data that has been changed relative to the preceding snapshot. For more information, see [Snapshot concepts](reseller.en-US/Snapshots/Snapshot concepts.md#).

## Billing {#section_i5r_krq_wgb .section}

A snapshot is billed based on the amount of the storage space used by a snapshot. After you create a disk snapshot, you can view the size of the snapshot by using the **Snapshot Chains** feature in the ECS console. You can also view the total size of all snapshots in a region by using the **Snapshot Size** feature in the ECS console.

For more information about the billing methods and unit price of snapshot storage space, see [Billing of snapshots](../../../../reseller.en-US/Pricing/Billing of snapshots.md#).

## Service advantages {#section_j5r_krq_wgb .section}

The Alibaba Cloud snapshot service provides high snapshot quotas and flexible snapshot policies. The following table describes the user benefits and typical scenarios of the service.

|Item|Description|User benefit|Typical scenario|
|:---|:----------|:-----------|:---------------|
|Snapshot quotas|Each disk can have up to 256 manual snapshots and 256 automatic snapshots.|Longer protection cycle with a finer granularity| -   Snapshot for non-critical service data disks are created at 00:00 every day. These snapshots can store backup data of more than 16 months.
-   Snapshots for critical service data disks are created every four hours. These snapshots can store backup data of more than four months.

 |
|Automatic snapshot policies|In an automatic snapshot policy, you can customize when a snapshot is created, how often a snapshot is created in a week, and how long a snapshot is stored. You can also query the number and other details of the disks that are associated with the automatic snapshot policy.|More flexible protection policies| -   You can select up to 24 different hour-long intervals for which to create an automatic snapshot each day.
-   Snapshots can be created automatically on multiple days each week.
-   Snapshots can be stored for a specified period of time or stored permanently.

**Note:** When the snapshot quota is reached, the system automatically deletes the earliest snapshot.


 |

## Technical advantages {#section_q5r_krq_wgb .section}

The following table describes the advantages of the Alibaba Cloud ECS snapshot service over traditional snapshot services.

|Metric|ECS snapshot service|Traditional snapshot service|
|:-----|:-------------------|:---------------------------|
|Capacity|Unlimited capacity, ensuring that all of your service data can be protected.|Limited capacity. Only the initially purchased storage capacity is available, and only critical data can be protected.|
|Scalability|Support for Auto Scaling. You can scale storage devices within seconds.|Lower scalability. Storage scaling is constrained by performance, available capacity, and vendor support.|
|Security|Support for the encryption service. You can set ECS disk encryption as necessary to encrypt your disk snapshots. However, a non-encrypted snapshot cannot be converted to an encrypted snapshot. Similarly, an encrypted snapshot cannot be converted to a non-encrypted snapshot. For more information, see [ECS disk encryption](reseller.en-US/Block Storage/Block storage/ECS disk encryption.md#).|Encryption attributes and policies rely on the underlying storage logic. If the storage architecture has defects in its security design, created snapshots may not be secure.|
|Impact on performance|Redirect-on-write \(ROW\) -   The impact of snapshot tasks on storage I/O performance is reduced.
-   Snapshots do not affect your service and can be created at any time without affecting user experience.

 |Copy-on-write \(COW\) or other techniques such as ROW. COW has an impact on the data write capability of the source system.|

## Related operations {#section_6u2_lk9_x6u .section}

-   [Create a snapshot](reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#)
-   [Create a cloud disk by using a snapshot](../../../../reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a cloud disk by using a snapshot.md#)
-   [Roll back a disk by using a snapshot](reseller.en-US/Snapshots/Use snapshots/Roll back a disk by using a snapshot.md#)
-   [Create a custom image by using a snapshot](../../../../reseller.en-US/Images/Custom image/Create custom image/Create a custom image by using a snapshot.md#)

