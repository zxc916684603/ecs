# DescribeSnapshotsUsage {#DescribeSnapshotsUsage .reference}

Queries the number of snapshots stored in a region and the total size of the snapshots. If you want to view the snapshot usage information on each disk in the current region, we recommend that you call the DescribeSnapshotLinks operation to query snapshot chain information.

## Request parameters {#RequestParameter .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSnapshotsUsage.|
|RegionId|String|Yes|The ID of the region where the snapshot is stored.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|

## Response parameters {#ResponseParameter .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|SnapshotCount|Integer|The number of snapshots stored in the current region.|
|SnapshotSize|Long|The size of snapshots stored in the current region. Unit: Bytes.|

## Examples {#Samples .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSnapshotsUsage
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response examples**

**XML format**

```
<DescribeSnapshotsUsageResponse>
	<SnapshotCount>5</SnapshotCount>
	<SnapshotSize>122</SnapshotSize>
    
    <RequestId>ED5CF6DD-71CA-462C-9C94-A61A78A01479</RequestId>
</DescribeSnapshotsUsageResponse>
```

**JSON format**

```
{
	"SnapshotCount": "5",
	"SnapshotSize": "122",
	"RequestId": "ACD9BBB0-A9D1-46D7-9630-B7A69889E110"
}
```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [Common error codes](../reseller.en-US/API Reference/Getting started/Response results.md#commonErrorCodes).

