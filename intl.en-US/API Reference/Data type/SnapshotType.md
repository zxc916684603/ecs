# SnapshotType {#SnapshotType .reference}

Data type of snapshot details.

## Node {#section_yrq_4rp_ydb .section}

Depends on the method.

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|SnapshotId|String |Snapshot ID. |
|SnapshopName|String | Display name of the snapshot. It is returned if a display name is specified at the creation.|
|Description |String |Description information. |
|Encrypted |Boolean |Whether the specified snapshot is encrypted or not.|
|Progress|String |Progress of snapshot creation, presented in percentage.|
|SourceDiskId|String |Source disk ID, which is retained after the source disk of the snapshot is deleted.|
|SourceDiskSize|Integer |Size of the source disk, measured in GB.|
|SourceDiskType|String |Source disk attribute. Optional values:-   System 
-   Data 

|
|ProductCode |String |Product code on the image market place. |
|RetentionDays|Integer |The number of days that an automatic snapshot retains in the console for your instance.|
|CreationTime |String |Creation time.  Time of creation. It is represented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC time is used. Format: YYYY-MM-DDThh:mmZ.|
|Status |String |Snapshot status. Optional values:-   progressing
-   accomplished
-   failed

|
|Usage |String |The type of resource that has a reference relationship.  Optional values:-   image
-   disk
-   Image\_disk
-   none

|

