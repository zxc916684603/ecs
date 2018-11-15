# DiskDeviceMapping {#DiskDeviceMapping .reference}

Describe the relation between images and snapshots.

## Node Name {#section_jtq_ggp_ydb .section}

Depends on the methods.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|SnapshotId|String|Snapshot ID.|
|Size|String|Size of the created disk.|
|Device|String|Device information of the created disk: such as /dev/xvdb.|
|Format|String|Mirror format.|
|ImportOSSBucket|String|The OSS bucket that stores the image.|
|Importossobject|String|The image object in OSS.|

