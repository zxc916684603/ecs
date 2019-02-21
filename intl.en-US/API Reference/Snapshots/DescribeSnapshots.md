# DescribeSnapshots {#DescribeSnapshots .reference}

Queries one or more of your available snapshots. The request parameters InstanceId, DiskId, and SnapshotIds are not required. However, they act as a filter. Logically, they are in an And \(&&\) relation.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSnapshots.|
|RegionId|String|Yes|The Region ID of snapshot.|
|InstanceId|String|No|The specified instance ID.|
|DiskId|String|No|The specified disk ID.|
|Encrypted|Boolean|No|Queries the encrypted snapshots. Optional values:-   true: Encrypted snapshots.
-   false: No encryption attribute limit.

Default value: false.|
|SnapshotIds|String|No|The Snapshot ID. The value can contain arrays of up to 10 snapshot IDs. The IDs are displayed in the format of \["s-xxxxxxxxx", "s-yyyyyyyyy", … "s-zzzzzzzzz"\]  and separated by commas \(`,`\).|
|SnapshotName|String|No|The snapshot name.|
|Status|String|No|The snapshot status. Optional values:-   progressing: The snapshots are being created.
-   accomplished: The snapshots are ready to use.
-   failed: The snapshot creation failed.
-   all: All status.

Default value: all.|
|SnapshotType|String|No|The snapshot category. Optional values:-   auto: Auto snapshots.
-   user: Manual snapshots.
-   all: Auto and manual snapshots.

Default value: all.|
|SourceDiskType|String|No|Whether the snapshots are created for system disks or data disks. Optional values:-   System: The snapshots are created for system disks.
-   Data: The snapshots are created for data disks.

|
|Usage|String|No|Whether the snapshots are used to create resources or not. Optional values:-   image: The snapshots are used to [create custom images](reseller.en-US/API Reference/Images/CreateImage.md#).
-   disk: The snapshots are used to [CreateDisk](reseller.en-US/API Reference/Disk/CreateDisk.md#).
-   mage\_disk: The snapshots are used to create custom images and data disks.
-   none: The snapshots are not used yet.

|
|Tag.n.Key|String|Yes|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|Yes|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|PageNumber|Integer|No|Displays the snapshots on several pages.  Start value: 1.  Default value: 1.

|
|PageSize|Integer|No|The maximum entries on a page.  Maximum value: 100.  Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number.|
|PageNumber|Integer|The page number of the list.|
|PageSize|Integer|The number of lines per page set during input.|
|Snapshots|[SnapshotType](reseller.en-US/API Reference/Data type/SnapshotType.md#)|A collection composed of snapshot details SnapshotType.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSnapshots
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example**

**XML format** 

```
<DescribeSnapshotsResponse>
    <Snapshots>
        <Snapshot>
            <CreationTime>2014-07-24T13:00:52Z</CreationTime>
            <Description></Description>
            <SourceDiskId>d-23x0r79qy</SourceDiskId>
            <SourceDiskType>DATA</SourceDiskType>
            <ProductCode></ProductCode>
            <SnapshotName>auto_20140724_2</SnapshotName>
            <Progress>100%</Progress>
            <SourceDiskSize>50</SourceDiskSize>
            <Status>accomplished</Status>
            <SnapshotId>s-23f2i9s4t</SnapshotId>
            <Usage>none</Usage>
        </Snapshot>
        <Snapshot>
            <CreationTime>2014-07-24T13:00:42Z</CreationTime>
            <Description></Description>
            <SourceDiskId>101-70105379</SourceDiskId>
            <SourceDiskType>DATA</SourceDiskType>
            <ProductCode></ProductCode>
            <SnapshotName>auto_20140724_2</SnapshotName>
            <Progress>100%</Progress>
            <SourceDiskSize>5</SourceDiskSize>
            <Status>accomplished</Status>
            <SnapshotId>s-23izto5qm</SnapshotId>
            <Usage>none</Usage>
        </Snapshot>
    </Snapshots>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <TotalCount>36</TotalCount>
    <RequestId>2F409D67-329A-4405-B924-2FC28566B366</RequestId>
</DescribeSnapshotsResponse>
```

**JSON format** 

```
{
  "PageNumber": 1,
  "PageSize": 2,
  "RequestId": "659F91C6-1949-43B0-90C4-B6342CA757D5",
  "Snapshots": {
    "Snapshot": [
      {
        "CreationTime": "2015-07-30T05:00:14Z",
        "Progress": "100%",
        "SnapshotId": "s-943ypfgic",
        "SnapshotName": "auto_20150730_3",
        "SourceDiskId": "d-944qyqjfa",
        "SourceDiskSize": 20,
        "SourceDiskType": "system",
        "Status": "accomplished",
        "Usage": "none"
      },
      {
        "CreationTime": "2015-07-30T05:00:14Z",
        "Progress": "100%",
        "SnapshotId": "s-94osg320e",
        "SnapshotName": "auto_20150730_3",
        "SourceDiskId": "d-94j355jsq",
        "SourceDiskSize": 20,
        "SourceDiskType": "system",
        "Status": "accomplished",
        "Usage": "none"
      }
    ]
  },
  "TotalCount": 36
}
```

## Error codes {#ErrorCode .section}

|Error code| Error message|HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|The specified `Tag.n.Key` and `Tag.n.Value`  must be a matched key-value.|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|The maximum number of the Tag.n.Key and Tag.n.Value is 5.|
|InvalidSnapshotIds.Malformed|The amount of specified specified snapshot Ids exceeds the limit.|403|The value of the specified `SnapshotIds` is incorrect.|
|InvalidSnapshotType.NotFound|The specfied SnapshotType is not found.|404|The specified `SnapshotType` does not exist.|
|InvalidSourceDiskType|The specifed SourceDiskType is not valid.|404|The specified `SourceDiskType` is invalid.|
|InvalidStatus.NotFound|The specified Status is not found.|404|The specified `Status` is invalid.|
|InvalidUsage|The specifed Usage is not valid.|404|The specified `Usage` is invalid.|

