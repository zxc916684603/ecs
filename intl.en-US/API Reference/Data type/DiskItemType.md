# DiskItemType {#DiskItemType .reference}

Enumerates the type of disk information entry.

## Node name {#section_h34_v3p_ydb .section}

Disk

## Subodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|DiskId |String|Disk ID.|
|RegionId |String|Region ID of the instance.|
|ZoneId |String|The Zone to which the disk belongs.|
|DiskName |String|Disk name.|
|Description |String|Disk description.|
|Type |String |Disk type. Possible values: -   system: System disk.
-   data: Data disk.

|
|Category|String|Category of disk. Possible values:-   cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra Cloud Disks.
-   cloud\_ssd: SSD Cloud Disks.
-   ephemeral\_ssd: Ephemeral SSD.
-   ephemeral: Ephemeral disk.

|
|Encrypted |Boolean|Whether the disk is encrypted or not. Possible values:-   true: The disk is encrypted.
-   false: The disk is not encrypted.

|
|Size |Integer|Disk size in GiB.|
|ImageId |String|ID of the image from which the disk is created. It is null unless the disk is created using an image. Its value remains unchanged throughout the life cycle of the disk.|
|SourcesnapshotId |String|Snapshot used to create the disk. It is null if no snapshot is used to create the disk. Its value remains unchanged throughout the life cycle of the disk.|
|IOPSRead|String |Disk I/O reads, measured in /s.|
|IOPSWrite|String |Disk I/O writes, measured in /s.|
|IOPS|String |Disk I/O reads and writes, measured in /s.|
|Portable |String |Whether the disk is detachable. Possible values:-   true: The disk is an independent basic cloud disk. This type of disk exists independently and can be attached or detached in the same zone.
-   false: The disk is a non-independent basic cloud disk. Such disk is created or deleted along with an instance.

Only when the `Portable` attribute of the disk is `true` you can operate [AttachDisk](reseller.en-US/API Reference/Disk/AttachDisk.md#) or [DetachDisk](reseller.en-US/API Reference/Disk/DetachDisk.md#) on a disk. The `Portable` attribute is `false`. For subscribed ephemeral disks, ephemeral SSDs, basic cloud system disks, and basic cloud disks. Their portable attribute cannot be modified.|
|Status |String|Disk status. Possible values:-   In\_use
-   Available
-   Attaching
-   Detaching
-   Creating
-   ReIniting

|
|OperationLocks|OperationLocksType|The reason why the disk is locked.|
|InstanceId |String|ID of the related instance. It is null unless the `Status` is **In Use** \(`In_use`\).|
|Device |String| Device information of the related instance, such as /dev/xvdb. It is null unless the `Status`  is **In Use** \(`In_use`\).|
|DeleteWithInstance|String|Whether the disk is released along with the release of the instance or not. Possible values:-   true: The disk is released along with the release of the instance.
-   false: The disk is not released along with the release of the instance.

|
|DeleteAutoSnapshot|String|Whether auto snapshots are deleted or not when the disk is deleted. Possible values:-   true: Deletes the snapshot simultaneously.
-   false: Retains the snapshot.

Snapshots created using [CreateSnapshot](reseller.en-US/API Reference/Snapshots/CreateSnapshot.md#) or in the console are not affected. They are retained permanently.|
|EnableAutoSnapshot|String|Whether auto snapshot policies are enforced or not for the disk. Possible values:-   true: Auto snapshot policies are enforced for the disk.
-   false: Auto snapshot policies are not enforced for the disk.

Default: false.|
|CreationTime |String|Creation time. It is represented according to [ISO8601](reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#), and UTC time is used. Format: YYYY-MM-DDThh:mmZ.|
|AttachedTime|String|The time when the disk is attached. It is represented according to [ISO8601](reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#), and UTC time is used. Format: YYYY-MM-DDThh:mmZ Only when the `Status`  is **In Use** \(`In_use`\), it is valid.|
|DetachedTime|String|Time when the disk is detached. It is represented according to [ISO8601](reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#), and UTC time is used. Format: YYYY-MM-DDThh:mmZ. Only when the `Status` is **Available** \(`Available`\), it is valid.|
|DiskChargeType|String|The billing method of the disk. Possible values:-   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go.

|

