# DescribeDisks {#DescribeDisks .reference}

查询您已经创建的磁盘。

## 描述 {#section_pl3_qn5_xdb .section}

-   请求参数 `RegionId`、`ZoneId`、`DiskIds` 和 `InstanceId` 等都是过滤器的概念，参数间是逻辑与（`AND`）关系。

-   请求参数 `DiskIds` 是一个 JSON 格式的数组（Array），如果参数为空，则过滤器不起作用，但是 `DiskIds` 如果是一个空 Array（即 `[]`），则视为该过滤器有效，且返回空。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeDisks|
|RegionId|String|是|磁盘所属于的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|Encrypted|Boolean|否|是否过滤加密磁盘。取值范围:-   true：只筛选出加密磁盘
-   false：不做加密属性的筛选

默认值：false|
|ZoneId|String|否|可用区 ID。|
|DiskIds|String|否|磁盘 ID。一个带有格式的 Json Array：\["d-xxxxxxxxx", "d-yyyyyyyyy", … "d-zzzzzzzzz"\]，最多 100 个 ID，用半角逗号字符隔开。|
|InstanceId|String|否|实例 ID。|
|DiskType|String|否|要查询的磁盘类型。取值范围：-   all：同时查询系统盘与数据盘
-   system：只查询系统盘
-   data：只查询数据盘

默认值：all|
|Category|String|否|磁盘种类。取值范围：-   all：所有磁盘
-   cloud：普通云盘
-   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD 盘
-   local\_ssd\_pro：I/O 密集型本地盘
-   local\_hdd\_pro：吞吐密集型本地盘
-   ephemeral：本地磁盘
-   ephemeral\_ssd：本地 SSD 盘

默认值：all|
|Status|String|否|磁盘状态，参考文档 [普通云盘状态](cn.zh-CN/API参考/附录/普通云盘状态表.md#)。取值范围：-   In\_use
-   Available
-   Attaching
-   Detaching
-   Creating
-   ReIniting
-   All

默认值：All|
|SnapshotId|String|否|创建磁盘使用的快照。|
|DiskName|String|否|磁盘名称。|
|Portable|String|否|要查询的磁盘是否支持卸载，该属性为不可修改属性。取值范围：-   true：可卸载磁盘，可以独立存在且可以自由在可用区内挂载和卸载
-   false：不可卸载磁盘，不可以独立存在且不可以自由在可用区内挂载和卸载

这个属性为 `true` 的磁盘才能挂载和卸载其中：-   本地盘
-   本地 SSD 盘
-   普通云盘，高效云盘和 SSD 盘的系统盘
-   包年包月的普通云盘、高效云盘、SSD 盘

该属性都为 `false`。|
|DeleteWithInstance|String|否|磁盘是否随实例释放。取值范围：-   true：实例释放时，这块磁盘随实例一起释放
-   false：实例释放时，这块磁盘保留不释放

默认值：false|
|DeleteAutoSnapshot|String|否|删除磁盘时，是否同时删除自动快照。取值范围：-   true：同时删除自动快照
-   false：保留自动快照

默认值：false|
|EnableAutoSnapshot|String|否|磁盘是否执行自动快照策略（前提是用户整体的自动快照策略已经开启）。取值范围：-   true：表示这块磁盘执行自动快照策略
-   false：表示这块磁盘不执行自动快照策略

默认值：false|
|Tag.n.Key|String|否|标签键，n 的取值范围为 \[1, 5\]。不允许为空字符串。|
|Tag.n.Value|String|否|标签值，n 的取值范围为 \[1, 5\]。允许为空字符串。|
|PageNumber|Integer|否|磁盘状态列表的页码，起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数，最大值：100默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|Encrypted|Boolean|是否为加密磁盘|
|TotalCount|Integer|磁盘总个数|
|PageNumber|Integer|磁盘列表的页码|
|PageSize|Integer|输入时设置的每页行数|
|Disks|[DiskItemType](cn.zh-CN/API参考/数据类型/DiskItemType.md#)|磁盘信息组成的集合|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?action=DescribeDisks
&RegionId=cn-qingdao
&PageNumber=1
&ZoneId=cn-qingdao-b
&<公共请求参数>
```

**返回示例** 

**XML 格式**

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

 **JSON 格式** 

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

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidCategory.ValueNotSupported|The specified disk category is not supported.|400|指定的磁盘种类不支持，或者您暂时没有权限使用此类磁盘。|
|InvalidDiskType.ValueNotSupported|The specified disk type is not supported.|400|指定的磁盘属性不支持。|
|InvalidRegion.NotFound|The specified parameter RegionId is not valid.|400|指定的 `RegionId` 不存在。|
|InvalidStatus.ValueNotSupported|The specified disk status is not supported.|400|指定的磁盘状态不支持。|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|指定的 `Tag.n.Key` 和 `Tag.n.Value` 不匹配。|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|指定的标签数超过了 5 个。|
|InvalidZoneId.NotFound|The ZoneId provided does not exist.|400|指定的 `ZoneId` 不存在。|
|InvalidDiskIds.Malformed|The amount of specified disk Ids exceeds the limit.|403|指定的 `DiskId` 格式不正确。|
|InvalidDiskChargeType.NotFound|The DiskChargeType does not exist.|404|指定的 `DiskChargeType` 不存在。|
|InvalidLockReason.NotFound|The specified LockReason is not found|404|指定的 `LockReason` 不存在。|

