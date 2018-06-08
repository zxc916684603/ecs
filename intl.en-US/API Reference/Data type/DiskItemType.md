# DiskItemType {#DiskItemType .reference}

Enumerates the type of disk information entry.

## Node name {#section_h34_v3p_ydb .section}

Disk.

## Subodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|DiskId |String |Disk ID. |
|RegionId |String|Region ID of the instance.  |
|ZoneId |String|The Zone to which the disk belongs.|
|DiskName |String |Disk name. |
|Description |String |Disk description. |
|Type |String |Disk type.  Optional values: -   system: System disk.
-   data: Data disks.

|
|Category|String |Category of disk. Optional values: -   cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra Cloud Disks.
-   cloud\_ssd:  SSD Cloud Disks.
-   ephemeral\_ssd: Ephemeral SSD.
-   ephemeral: Ephemeral disk.

|
|Encrypted |Boolean |Whether the disk is encrypted or not. Optional values:-   true: The disk is encrypted.
-   false: The disk is not encrypted.

|
|Size |Integer |Disk size in GB.|
|ImageId |String | ID of the image from which the disk is created. It is null unless the disk is created using an image.  Its value remains unchanged throughout the life cycle of the disk.|
|SourcesnapshotId |String |Snapshot used to create the disk. It is null if no snapshot is used to create the disk.  Its value remains unchanged throughout the life cycle of the disk.|
|ProductCode|String|ID of a product available in the image marketplace.|
|IOPSRead|String | Disk IO reads, measured in /s.|
|IOPSWrite|String |Disk IO writes, measured in /s.|
|IOPS|String | Disk IO reads and writes, measured in /s.|
|Portable |String | Whether the disk is detachable. Optional values:-   true: The disk is an independent basic cloud disk. This type of disk exists independently and can be attached or detached in the same zone.
-   false: The disk is a non-independent basic cloud disk. Such disk is created or deleted along with an instance.

Only when the `Portable` attribute of the disk is `true` you can operate [AttachDisk](intl.en-US/API Reference/Disk/AttachDisk.md#) or [DetachDisk](intl.en-US/API Reference/Disk/DetachDisk.md#) on a disk,  The `Portable` attribute  is  `false`. for subscribed ephemeral disks, ephemeral SSDs, basic cloud system disks, and basic cloud disks. Their portable attribute cannot be modified.|
|Status |String |Disk status.   Optional values:-   In\_use 
-   Available 
-   Attaching 
-   Detaching 
-   Creating 
-   ReIniting

|
|OperationLocks|OperationLocksType|The reason why the disk is locked.|
|InstanceId |String |ID of the related instance .  It is null unless the `Status` is `In_use` .|
|Device |String | Device information of the related instance, such as /dev/xvdb. It is null unless the `Status`  is `In_use`.|
|DeleteWithInstance|String |Whether the disk is released along with the release of the instance or not.  Optional values:-   true: The disk is released along with the release of the instance.
-   false: The disk is not released along with the release of the instance.

|
|DeleteAutoSnapshot|String | Whether auto snapshots are deleted or not when the disk is deleted.  Optional values:-   true: Deletes the snapshot simultaneously. 
-   false: Retains the snapshot. 

Snapshots created using [CreateSnapshot](intl.en-US/API Reference/Snapshots/CreateSnapshot.md#) or on the console are not affected. They are retained permanently.|
|EnableAutoSnapshot|String| Whether auto snapshot policies are enforced or not for the disk.  Optional values:-   true: Auto snapshot policies are enforced for the disk.
-   false: Auto snapshot policies are not enforced for the disk.

Default: false.|
|CreationTime |String |Creation time. It is represented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC time is used.  Format: YYYY-MM-DDThh:mmZ.|
|AttachedTime|String | The time when the disk is attached.  It is represented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC time is used. Format: YYYY-MM-DDThh:mmZ Only when the `Status`  is `In_use`. it is valid.|
|DetachedTime|String | Time when the disk is detached.  It is represented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC time is used. Format:  YYYY-MM-DDThh:mmZ Only when the `Status` is `Available`. it is valid.|
|DiskChargeType|String | The billing method of the disk.  Optional values:-   PrePaid： Subscription.
-   PostPaid: Pay-As-You-Go.

|

