# AttachDisk {#doc_api_1030732 .reference}

为一台ECS实例挂载一块数据盘。

## 接口说明 {#description .section}

调用该接口时，您需要注意：

-   待挂载的ECS实例的状态必须为运行中（Running）或者已停止（Stopped）。
-   挂载数据盘时，云盘的状态必须为待挂载（Available）。
-   被 [安全控制](~~25695~~) 的ECS实例的OperationLocks不能标记为"LockReason" : "security"。
-   即使您在挂载云盘时，将DeleteWithInstance置为false，一旦ECS实例被安全控制，且 OperationLocks中标记了"LockReason" : "security"，释放ECS实例时会忽略云盘的DeleteWithInstance属性而被同时释放。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=AttachDisk)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DiskId|String|是|d-23jbf2v5m|待挂载的云盘ID。云盘（DiskId）和实例（InstanceId）必须在同一个可用区。

 |
|InstanceId|String|是|i-instance1|待挂载的ECS实例ID。

 |
|Action|String|否|AttachDisk|系统规定参数。取值：AttachDisk

 |
|DeleteWithInstance|Boolean|否|false|释放实例时，该云盘是否随实例一起释放。默认值：False

 |
|Device|String|否|/dev/xvda|磁盘设备名称。该参数即将被弃用，为提高兼容性，请尽量使用其他参数。

 |
|OwnerAccount|String|否|ECSforCloud@Alibaba.com|RAM 用户的账号登录名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=AttachDisk
&DiskId=d-23jbf2v5m
&InstanceId=i-instance1
&DeleteWithInstance=false
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AttachDiskResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</AttachDiskResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidDevice.Malformed|The specified device is not valid.|指定的磁盘设备名不存在。|
|403|InstanceDiskLimitExceeded|The amount of the disk on instance in question reach its limits.|指定实例已经达到可挂载磁盘的最大值。|
|403|InvalidDevice.InUse|The specified device has been occupied.|指定的设备已经挂载了磁盘。|
|403|InstanceLockedForSecurity|The instance is locked due to security.|您的资源被安全锁定，拒绝操作。|
|403|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|包年包月实例已过期，请您续费后再进行操作。|
|400|IncorrectInstanceStatus|The current status of the resource does not support this operation.|该资源目前的状态不支持此操作。|
|403|DiskError|IncorrectDiskStatus.|指定的磁盘状态不合法。|
|403|DiskId.ValueNotSupported|The specified parameter diskid is not supported.|当前磁盘类型不支持此操作|
|403|DiskId.StatusNotSupported|The specified disk status is not supported.|不支持指定的磁盘状态。|
|404|InvalidDisk.InUse|The specified disk has been occupied.|指定的磁盘已占用。|
|403|UserNotInTheWhiteList|The user is not in disk white list.|您暂时不能使用该磁盘服务。|
|400|InvalidOperation.InstanceTypeNotSupport|The instance type of the specified instance does not support hot attach disk.|磁盘挂载的实例不支持磁盘热插拔操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

