# ECS Snapshot 2.0 {#concept_f3f_nbx_ydb .concept}

Built on original basic snapshot features, ECS Snapshot 2.0 data backup service provides a higher snapshot quota and more flexible automatic task policies, further reducing its impact on business I/O. The features of ECS Snapshot 2.0 are described in the following table.

**Note:** Disks in this topic refer to Elastic Block Storage. For more information, see [Elastic block storage](intl.en-US/Product Introduction/Block storage/Elastic block storage.md#).

|Feature|Original snapshot specifications|Snapshot 2.0 specifications|User benefit|Example|
|:------|:-------------------------------|:--------------------------|:-----------|:------|
|Snapshot quota|\(Number of disks\)\*6+6|64 snapshots for each disk|Longer protection circle Smaller protection granularity| -   Snapshot backup of a data disk for non-core businesses occurs at 00:00 every day. This backup data is retained for over 2 months.
-   Snapshot backup of a data disk for core businesses occurs every 4 hours. This backup data is retained for over 10 days.

 |
|Automatic task policy|Hardcoded, triggered once daily, and unmodifiable|Customizable weekly snapshot day, time of day, and snapshot retention period Query-able disk quantity and related details associated with an automatic snapshot policy|More flexible protection policy| -   A user can take snapshots on the hour and for several times in a day.
-   A user can choose any day as the recurring day for taking weekly snapshots.
-   A user can specify the snapshot retention period or choose to retain it permanently. When the maximum number of automatic snapshots has been reached, the oldest automatic snapshot will be deleted.

 |
|Implementation principle|COW \(Copy-on-write\)|ROW \(Redirect-on-write\)|Mitigated performance impact of the snapshot task on business I/O write|The implementation principle is not made visible to users, allowing snapshots to be taken at any time of day without affecting user experience.|

