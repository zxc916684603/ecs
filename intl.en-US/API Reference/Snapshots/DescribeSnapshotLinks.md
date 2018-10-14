# DescribeSnapshotLinks {#DescribeSnapshotLinks .reference}

Describes the snapshot chains of one or more disks. A snapshot chain is a chain of all the snapshots of a disk, and a disk corresponds to a chain of snapshots, so the snapshot chain ID is the disk ID.

## Description {#section_vg2_jb1_ydb .section}

When you call this interface, consider the following:

-   Request parameters, such as `RegionId`, `DiskIds` and `InstanceId`, act as a filter. A logical AND relation exists among parameters.

-   If no parameter is specified, the filter does not take effect. When `DiskIds` and `SnapshotLinkIds` are empty array \(`[]`\), the filter still takes effect, but a null result is returned.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSnapshotLinks.|
|RegionId|String|Yes|Region ID of the instance. For more information, call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|No|The instance ID.|
|Diskids|String|No|Disk ID. The disk ID. You can specify a maximum of 100 disk IDs each time. The value of `DiskIds` is a JSON array of which the format is displayed as  \["d-xxxxxxxxx", "d-yyyyyyyyy", … "d-zzzzzzzzz"\], IDs are separated by commas \(,\).|
|SnapshotLinkIds|String|No|The snapshot chain ID. The snapshot chain ID. You can specify a maximum of 100 snapshot chain IDs each time. The value of `SnapshotLinkIds` is a JSON array of which the format is displayed as \["p-xxxxxxxxx", "p-yyyyyyyyy", … "p-zzzzzzzzz"\], IDs are separated by a half-angle comma.|
|PageNumber|Integer|No|Page number of a disk status list. Initial value: 1.Default value: 1.

|
|PageSize|Integer|No|The maximum entries on a page. Value range: \[1, 50\].Default value: 10.

|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|RegionId|String|Region ID of the snapshot chain.|
|TotalCount|Integer|Total number of snapshot chains.|
|PageNumber|Integer|Page number of the snapshot chain list.|
|PageSize|Integer|Number of lines per page set during input.|
|SnapshotLinks|[SnapshotLinkType](reseller.en-US/API Reference/Data type/SnapshotLinkType.md#)|A set that consists of snapshot chain information.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSnapshotLinks
&RegionId=cn-beijing
&ZoneId=cn-beijing-btc-a01
&PageNumber=1
&<Common parameter request>
```

**Response example** 

**XML format** 

```
<DescribeSnapshotLinksResponse>
    <SnapshotLinks>
        <SnapshotLink>
            <SnapshotLinkId>d-25okbh2pj</SnapshotLinkId >
            <SourceDiskId>d-25okbh2pj</SourceDiskId>
            <SourceDiskType>data</SourceDiskType>
            <SourceDiskSize>20</SourceDiskSize>
            <RegionId> cn-beijing-btc-a01</RegionId>
            <TotalCount>1</TotalCount>
            <TotalSize>2097152</TotalSize>
        </SnapshotLink>
        <SnapshotLink>
            <SnapshotLinkId>d-2ze0y1jwzpb1geqxkroq</SnapshotLinkId >
            <SourceDiskId>d-2ze0y1jwzpb1geqxkroq</SourceDiskId>
            <SourceDiskType>system</SourceDiskType>
            <SourceDiskSize>40</SourceDiskSize>
            <RegionId> cn-beijing-btc-a01</RegionId>
            <TotalCount>1</TotalCount>
            <TotalSize>2097152</TotalSize>
         </SnapshotLink>
    </SnapshotLinks>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <TotalCount>9</TotalCount>
    <RequestId>ED5CF6DD-71CA-462C-9C94-A61A78A01479</RequestId>
</DescribeSnapshotLinksResponse>
```

 **JSON format** 

```
{
    "SnapshotLinks": {
    "SnapshotLink": [
    {
        "SourceDiskSize": 20,
        "TotalSize": 2097152,
        "SourceDiskType": "data",
        "RegionId": "cn-beijing-btc-a01",
        "SnapshotLinkId": "d-25okbh2pj",
        "SourceDiskId": "d-25okbh2pj",
        "TotalCount": 1
    },
    {
        "SourceDiskSize": 40,
        "TotalSize": 2097152,
        "SourceDiskType": "data",
        "RegionId": "cn-beijing-btc-a01",
        "SnapshotLinkId": "d-2ze0y1jwzpb1geqxkroq",
        "SourceDiskId": "d-2ze0y1jwzpb1geqxkroq",
        Totalcount: 1
    }
    ]
    },
    "PageNumber": 1,
    "PageSize": 2,
    "RequestId": "ACD9BBB0-A9D1-46D7-9630-B7A69889E110",
    "TotalCount": 9
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidDiskIds|The specified diskIds is invalid.|400|The specified `DiskIds` is invalid.|
|InvalidRegionId|The specified regionId is invalid.|400|The specified `RegionId`  parameter is invalid.|
|InvalidSnapshotLinkIds|The specified snapshotLinkIds is invalid.|400|The specified  `SnapshotLinkIds` is invalid.|
|InternalError |The request processing has failed due to some unknown error.| 500|Internal error.|

