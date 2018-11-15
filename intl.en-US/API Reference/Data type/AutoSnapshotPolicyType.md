# AutoSnapshotPolicyType {#AutoSnapshotPolicyType .reference}

Type of an automatic snapshot policy, including its detailed settings.

## Node Name {#section_ybk_b2p_ydb .section}

Depends on the interface.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|AutoSnapshotPolicyId|String|Automatic snapshot policy ID.|
|RegionId|String|Regionid to which the auto-Snapshot policy belongs.|
|Autosnapshotpolicyname|String|The name of the automatic snapshot policy.|
|TimePoints|String|Specifies the point in time at which the automatic snapshot is created. The minimum unit is hours, from 00: 00 ~ 23:00. A total of 24 time points are available, and the parameters are 0 ~ 23. For example: 1 represents 01:00. You can select multiple time points. The pass-through parameter is a JSON array in a format of \["0", "1 ",... "23"\] \(at most 24 time points\) separated by half-angle commas \(,\).|
|Repeatweekdays|String|Specifies the repeat date for the automatic snapshot. The date on which the snapshot needs to be created from Monday to Sunday, with a parameter of 1 ~ 7. For example: 1 indicates Monday. You can select multiple dates. The pass-through parameter is a JSON array in a format of \["1", "2 "... "7" \].|
|RetentionDays|Integer|Specifies the retention time, in days, of the automatic snapshot. -1: Permanent save 1 ~ 65536: specify the number of days to save.|
|DiskNums|Integer|Number of disks on which this policy is enabled.|
|OperationLocks|OperationLocksType|Snapshot lock reason type.|
|Status|String|Automatic snapshot policy status, value: Creating | available.|
|CreationTime|String|Creation time, formatted according to the ISO8601 standard, and uses UTC time. Format: YYYY-MM-DDThh:mmZ.|

