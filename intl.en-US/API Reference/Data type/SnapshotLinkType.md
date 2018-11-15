# SnapshotLinkType {#SnapshotLinkType .reference}

A set that consists of snapshot link information.

## Node {#section_qtj_3rp_ydb .section}

SnapshotLinks

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|SnapshotLinkId|String|The snapshot chain ID.|
|RegionId|String|The region to where a snapshot chain belongs.|
|SourceDiskId|String|The ID of the disk that maintains all the snapshots of a snapshot chain. If the specified disk has been released, the SourceDiskId is still returned.|
|SourceDiskSize|Integer|The size of a disk, measured in GiB.|
|TotalSize|Integer|The size of all the snapshots in a snapshot chain, measured in Byte.|
|TotalCount|Integer|The number of snapshots in a snapshot chain.|
|CreationTime|String|The moment when the snapshot is created.|

