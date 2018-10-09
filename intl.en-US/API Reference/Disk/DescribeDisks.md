# DescribeDisks {#DescribeDisks .reference}

Queries your available cloud disks.

## Description {#section_pl3_qn5_xdb .section}

-   You can specify request parameters to separate the possible response results. Request parameters, such as `RegionId`, `ZoneId`, `DiskIds`, and `InstanceId` act as a filter, and parameters are passed in the logical relation of AND \(`AND`\).

-   The value of parameter `DiskIds` is a JSON array in the format of \[“DiskId1”, “DiskId2”, “DiskId3”, …\], you can specify at most 100 DiskId each time. If `DiskIds` is not passed \(that is, `[]`\), all your cloud disks are queried.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeDisks.|
|RegionId|String|Yes|The Region ID of the disk. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|Encrypted|Boolean|No|Filter an encrypted disk. Optional values:-   true: Only query encrypted disks.
-   false: Have no restriction on the encryption attribute.

Default value: false.|
|ZoneId|String|No|The default value is null, which indicates a query of disks in all zones.|
|DiskIds|String|No|ID of the disk. ID of the disk. A formatted JSON Array: \[“d-xxxxxxxxx”, “d-yyyyyyyyy”, … “d-zzzzzzzzz”\]. A maximum of 10 IDs separated by single-byte commas.|
|InstanceId|String|No|ID of an instance.|
|DiskType|String|No|The type of disk. Optional values:-   all: Queries the system disk and data disks at the same time.
-   system: Queries the system disk only.
-   data: Queries the data disk only.

The default value: all.|
|Category|String|No|The disk category. Optional values:-   all: All kinds of disks.
-   cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: Cloud SSD.
-   ephemeral: Ephemeral disk.
-   local\_hdd\_pro: Local SATA HDD.
-   local\_ssd\_pro: Local NVMe SSD.
-   ephemeral\_ssd: Ephemeral SSD.

Default value: all.|
|Status|String|No|Disk status. See [Basic Cloud Disk Status](reseller.en-US/API Reference/Appendix/Basic cloud disk status table.md#) for more information. Optional values:-   In\_use
-   Available
-   Attaching
-   Detaching
-   Creating
-   ReIniting
-   All

The default value: All.|
|SnapshotId|String|No|The snapshot used to create the disk.|
|DiskName|String|No|The name of queried disk.|
|Portable|String|No|Whether or not the disk can be detached. Optional values:-   True: Disks can be freely attached and detached in a zone.
-   False: Disks are created and deleted along with instances.

If you attach or detach the specified disk, query disks with a property value of true. However, disk categories as follows have Portable=False by default.-   Local disks. For ephemeral disks,
-   Ephemeral SSD.
-   System disk that use basic cloud disk, cloud efficiency disk, and cloud SSD.
-   Subscribed disk that use basic cloud disk, cloud efficiency disk, and cloud SSD.

`false` indicates you cannot attach or detach the preceding disks independently.|
|DeleteWithInstance|String|No|Whether or not the disk is released along with the instance. Optional values:-   true: When the instance is released, this disk is released with it.
-   false: When the instance is released, this disk is retained.

Default value: false.|
|DeleteAutoSnapshot|String|No|Whether or not auto snapshots are deleted when the disk is deleted. Optional values:-   true: The auto snapshots are deleted with the disk.
-   false: The auto snapshots are retained.

Default value: false.|
|EnableAutoSnapshot|String|No|Whether the queried cloud disks have been applied automatic snapshot policies. Optional values:-   true: The queried cloud disks have been applied automatic snapshot policies.
-   false: The queried cloud disks have no automatic snapshot policies applied.

Default value: false.|
|Tag.n.Key|String|Yes|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|Yes|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|PageNumber|Integer|No|The current page of the disk status list. The start value: 1.Default value: 1.

|
|PageSize|Integer|No|The number of lines per page set for paging query. The maximum value: 100.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Encrypted|Boolean|Whether it is an encrypted disk.|
|TotalCount|Integer|The total number of instances.|
|PageNumber|Integer|The page number of the instance list.|
|PageSize|Integer|The number of lines per page set during input.|
|Disks|[DiskItemType](reseller.en-US/API Reference/Data type/DiskItemType.md#)|A collection composed of disk information, such as DiskItemType.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?action=DescribeDisks
&RegionId=cn-qingdao
&PageNumber=1
&ZoneId=cn-qingdao-b
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeDisksResponse>
    <Disks>
        <Disk>
            <DeleteAutoSnapshot>true</DeleteAutoSnapshot>
            <DeleteWithInstance>false</DeleteWithInstance>
            <EnableAutoSnapshot>false</EnableAutoSnapshot>
            <Category>cloud</Category>
            <Description></Description>
            <DiskName></DiskName>
            <Size>5</Size>
            <Type>data</Type>
            <InstanceId></InstanceId>
            <CreationTime>2014-07-23T02:44:07Z</CreationTime>
            <ImageId></ImageId>
            <ZoneId>cn-qingdao-b</ZoneId>
            <AttachedTime>2014-07-23T07:47:35Z</AttachedTime>
            <DetachedTime>2014-07-23T08:28:48Z</DetachedTime>
            <Device></Device>
            <OperationLocks></OperationLocks>
            <Portable>true</Portable>
            <ProductCode></ProductCode>
            <RegionId>cn-qingdao</RegionId>
            <DiskId>d-28m5zbua0</DiskId>
            <SourceSnapshotId></SourceSnapshotId>
            <Status>Available</Status>
        </Disk>
        <Disk>
            <DeleteAutoSnapshot>true</DeleteAutoSnapshot>
            <DeleteWithInstance>false</DeleteWithInstance>
            <EnableAutoSnapshot>false</EnableAutoSnapshot>
            <Category>cloud</Category>
            <Description></Description>
            <DiskName></DiskName>
            <Size>5</Size>
            <Type>data</Type>
            <InstanceId></InstanceId>
            <CreationTime>2014-07-23T02:44:06Z</CreationTime>
            <ImageId></ImageId>
            <ZoneId>cn-qingdao-b</ZoneId>
            <AttachedTime></AttachedTime>
            <DetachedTime></DetachedTime>
            <Device></Device>
            <OperationLocks></OperationLocks>
            <Portable>true</Portable>
            <ProductCode></ProductCode>
            <RegionId>cn-qingdao</RegionId>
            <DiskId>d-28zfrmo13</DiskId>
            <SourceSnapshotId></SourceSnapshotId>
            <Status>Available</Status>
        </Disk>
    </Disks>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <TotalCount>9</TotalCount>
    <RequestId>ED5CF6DD-71CA-462C-9C94-A61A78A01479</RequestId>
</DescribeDisksResponse>
```

 **JSON format** 

```
{
  "Disks": {
    "Disk": [
      {
        "AttachedTime": "2014-07-23T07:47:35Z",
        "Category": "cloud",
        "CreationTime": "2014-07-23T02:44:07Z",
        "DeleteAutoSnapshot": true,
        "DeleteWithInstance": false,
        "EnableAutoSnapshot": false
        "Description": "",
        "DetachedTime": "2014-07-23T08:28:48Z",
        "Device": "",
        "DiskId": "d-28m5zbua0",
        "DiskName": "",
        "ImageId": "",
        "InstanceId": "",
        "OperationLocks": {
            "OperationLock": []
        },
        "Portable": true,
        "ProductCode": "",
        "RegionId": "cn-qingdao",
        "Size": 5,
        "SourceSnapshotId": "",
        "Status": "Available",
        "Type": "data",
        "ZoneId": "cn-qingdao-b"
      },
      {
        "AttachedTime": "",
        "Category": "cloud",
        "CreationTime": "2014-07-23T02:44:06Z",
        "DeleteAutoSnapshot": true,
        "DeleteWithInstance": false,
        "EnableAutoSnapshot": false
        "Description": "",
        "DetachedTime": "",
        "Device": "",
        "DiskId": "d-28zfrmo13",
        "DiskName": "",
        "ImageId": "",
        "InstanceId": "",
        "OperationLocks": {
            "OperationLock": []
        },
        "Portable": true,
        "ProductCode": "",
        "RegionId": "cn-qingdao",
        "Size": 5,
        "SourceSnapshotId": "",
        "Status": "Available",
        "Type": "data",
        "ZoneId": "cn-qingdao-b"
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

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidCategory.ValueNotSupported|The specified disk category is not supported.|400|The specified Category is not supported. Otherwise, you are not authorized to use the specified DiskType.|
|InvalidDiskType.ValueNotSupported|The specified disk type is not supported.|400|The specified DiskType is not supported.|
|InvalidRegion.NotFound|The specified parameter RegionId is not valid.|400|The specified `RegionId` does not exist.|
|InvalidStatus.ValueNotSupported|The specified disk status is not supported.|400|The specified Status is not supported.|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|The specified `Tag.n.Key` and `Tag.n.Value` must be matched.|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|A maximum of 5 Tag.n.Key can be specified.|
|InvalidZoneId.NotFound|The ZoneId provided does not exist.|400|The specified `ZoneId` does not exist.|
|InvalidDiskIds.Malformed|The amount of specified disk Ids exceeds the limit.|403|The maximum number of `DiskId` is exceeded.|
|InvalidDiskChargeType.NotFound|The DiskChargeType does not exist.|404|The specified `DiskChargeType` does not exist.|
|InvalidLockReason.NotFound|The specified LockReason is not found.|404|The specified `LockReason` does not exist.|

