# AutoSnapshotPolicyType {#AutoSnapshotPolicyType .reference}

Type of an automatic snapshot policy, including its detailed settings.

## Node Name {#section_ybk_b2p_ydb .section}

Depends on the interface.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|AutoSnapshotPolicyId|String|Automatic snapshot policy ID|
|RegionId|String|Regionid to which the auto-Snapshot policy belongs|
|Autosnapshotpolicyname|String|The name of the automatic snapshot policy.|
|TimePoints|String|Specifies the point in time at which the automatic snapshot is created. The minimum unit is hours, from 8: 00 ~ A total of 24 time points are available, and the parameters are 0 ~ Number of 23, for example: 1 represents in 1-0 point in time. You can select more than one point in time. The pass-through parameter is a JSON array with a format: \["0", "1 ",... "23"\], up to 24 Seven dots of time separated by half-angle comma characters.|
|Repeatweekdays|String|Specifies the repeat date for the automatic snapshot. The date on which the snapshot needs to be created from Monday to Sunday, with a parameter of 1 ~ Number of 7, for example: 1 indicates Monday. Allows you to select multiple dates. The pass-through parameter is a JSON array with a format: \["1", "2 "... "7" \].|
|RetentionDays|Integer|Specifies the retention time, in days, of the automatic snapshot. -1: Permanent save 1 ~ 65536: specify the number of days to save|
|DiskNums|Integer|Number of disks on which this policy is enabled|
|OperationLocks|OperationLocksType|Snapshot lock reason type|
|Status|String|Automatic snapshot policy status, value: Creating | available|
|CreationTime|String|Creation time Formatted according to the ISO8601 standard, and uses UTC time. Format: YYYY-MM-DDThh:mmZ|

