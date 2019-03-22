# ResizeDisk {#doc_api_1111179 .reference}

扩容一块数据盘。

## 接口说明 {#description .section}

调用该接口时，您需要注意：

-   该接口暂时仅支持扩容数据盘，不支持扩容系统盘。
-   仅支持扩容磁盘类型为普通云盘（cloud）、高效云盘（cloud\_efficiency）和 SSD 云盘（cloud\_ssd）的数据盘。
-   当磁盘正在创建快照时，不允许扩容。
-   对于已挂载的数据盘：
    -   磁盘挂载的实例的状态必须为 运行中（Running）或者 已停止（Stopped）。
    -   扩容后，您需要在控制台 [重启实例](~~25440~~) 或者调用 API [RebootInstance](~~25502~~) 使操作生效。
-   磁盘挂载的实例的状态必须为 运行中（Running）或者 已停止（Stopped）。
-   扩容后，您需要在控制台 [重启实例](~~25440~~) 或者调用 API [RebootInstance](~~25502~~) 使操作生效。
-   扩容时，不会修改磁盘分区和文件系统，您需要在扩容后自行分配存储空间。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=ResizeDisk)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DiskId|String|是|d-diskid1|磁盘 ID。

 |
|NewSize|Integer|是|2100|希望扩容到的磁盘容量大小。单位为 GiB。取值范围：

 -   普通云盘（Cloud）：5~2000
-   高效云盘（Cloud\_efficiency）：5~2000
-   SSD 云盘（Cloud\_ssd）：5~2000

 指定的新磁盘容量必须比原磁盘容量大。且 2 TB 以下的磁盘不能扩容到 2 TB 以上。

 |
|Action|String|否|ResizeDisk|系统规定参数。取值：ResizeDisk

 |
|Type|String|否|online|是否在线扩容磁盘。取值范围：

 -   online：在线扩容，实例无需重启便能完成扩容。
-   offline（默认）：离线扩容，您需要重启实例以完成扩容。

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken** 只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](~~25693~~)。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=ResizeDisk
&DiskId=d-diskid1
&NewSize=2000
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ResizeDiskResponse>
  <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</ResizeDiskResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|InvalidDataDiskSize.ValueNotSupported|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|指定的数据盘大小已超过最大允许值。|
|403|OperationDenied|The type of the disk does not support the operation.|此磁盘种类不支持指定的操作。|
|403|OperationDenied|The status of the disk or the instance that the disk is attaching with does not support the operation.|此磁盘或实例状态无法执行指定的操作。|
|403|InvalidDiskSize.TooSmall|Specified new disk size is less than the original disk size.|指定的新磁盘小于原始磁盘。|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|包年包月实例已过期，请您续费后再进行操作。|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|403|DiskCreatingSnapshot|The operation is denied due to a snapshot of the specified disk is not completed yet.|指定的磁盘正在创建快照。|
|400|InvalidDataDiskCategory.ValueNotSupported|%s|参数不支持。|
|400|InvalidParameter.Conflict|%s|参数冲突。|
|400|InvalidDataDiskSize.ValueNotSupported|%s|参数不支持。|
|403|Operation.Conflict|The operation may conflicts with others.|该操作与其他操作冲突。|
|403|InstanceLockedForSecurity|The instance is locked due to security.|您的资源被安全锁定，拒绝操作。|
|403|UserNotInTheWhiteList|The user is not in disk white list.|您暂时不能使用该磁盘服务。|
|403|InvalidDiskCategory.NotSupported|The specified disk category is not supported.|该云盘类型不支持。|
|400|InvalidParam.Type|The specified type is not supported.|指定的参数无效。|
|403|InvalidRegion.NotSupport|The specified region does not support resize online.|该地域不支持在线扩容。|
|403|InvalidDiskCategory.NotSupported|The specified disk category does not support resize online.|指定的磁盘类型不支持在线扩容。|
|403|IncorrectInstanceStatus|The current status of the resource does not support resize online.|资源的当前状态不支持该操作。|
|403|IncorrectDiskStatus|The current status of the resource does not support resize online|该资源的状态不支持在线扩容磁盘。|
|403|InvalidOperation.InstanceTypeNotSupport|The instance type of the specified instance does not support resize online.|磁盘挂载的实例不支持磁盘在线扩容操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

