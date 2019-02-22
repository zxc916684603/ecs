# CreateSnapshot {#doc_api_1006124 .reference}

为一块ECS磁盘创建一份快照。

## 描述 {#description .section}

调用该接口时，您需要注意：

-   一块磁盘最多能创建 64 份快照。
-   磁盘挂载的实例必须处于 **已停止**（`Stopped`）或者 **运行中**（`Running`）状态，否则无法创建快照。
-   磁盘必须已经挂载到实例上，否则无法创建快照。
-   磁盘挂载的实例从未启动过时，无法创建快照。
-   被 [安全控制](~~25695~~) 的 ECS 实例的 `OperationLocks` 中标记了 `"LockReason" : "security"` 时，实例挂载的磁盘无法创建快照。
-   新建一台云服务器 ECS（[RunInstances](~~63440~~)）、更换系统盘（[ReplaceSystemDisk](~~25521~~)）或者根据快照新增数据盘（[CreateDisk](~~25513~~)），由于尚未完成数据加载，无法创建快照。新建一台云服务器 ECS 或者更换系统盘大约 1 小时后可以创建快照，新增一块数据盘可创建快照的时间取决于磁盘数据的大小。
-   如果创建快照还未完成，您无法为该磁盘再次创建快照。
-   如果创建快照还未完成，这份快照无法用于创建自定义镜像 （[CreateImage](~~25535~~)）。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=CreateSnapshot)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DiskId|String|是|d-diskid1|磁盘ID。

 |
|Action|String|否|CreateSnapshot|系统规定参数。取值：CreateSnapshot

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken** 只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](~~25693~~)。

 |
|Description|String|否|FinanceDepet|快照的描述。长度为 2~256 个英文或中文字符，不能以 http:// 和 https:// 开头。

 默认值：空

 |
|OwnerAccount|String|否|ECSforCloud@Alibaba.com|RAM用户的账号登录名称。

 |
|SnapshotName|String|否|FinanceJoshua|快照的显示名称。长度为 2~128 个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 为防止和 自动快照 的名称冲突，不能以auto开头。

 |
|Tag.N.Key|String|否|FinanceDept|快照的标签键。n 的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持 64 个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |
|Tag.N.Value|String|否|FinanceDept.Joshua|快照的标签值。n的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持 128 个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |
|Tag.N.key|String|否|FinanceDept|快照的标签键。n 的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持 64 个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |
|Tag.N.value|String|否|FinanceDept.Joshua|快照的标签值。n的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持 128 个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。无论调用接口成功与否，我们都会返回请求 ID。

 |
|SnapshotId|String|s-snapshotid1|快照 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=CreateSnapshot
&DiskId=d-diskid1
&SnapshotName=FinanceJoshua
&Description=FinanceDepet
&ClientToken=123e4567-e89b-12d3-a456-426655440000
&Tag.1.value=FinanceDept.Joshua
&Tag.1.key=FinanceDept
&Tag.1.Key=FinanceDept
&Tag.1.Value=FinanceDept.Joshua
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateSnapshotResponse>
  <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
  <SnapshotId>s-923FE2BF0</SnapshotId>
</CreateSnapshotResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C8B26B44-0189-443E-9816-D951F59623A9",
	"SnapshotId":"s-923FE2BF0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidDescription.Malformed|The specified description is wrongly formed.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|403|QuotaExceed.Snapshot|The snapshot quota exceeds.|快照额度超过限制，若要存储新快照，在不影响业务的情况下，请您删除已有的老快照。|
|403|DiskInArrears|The specified operation is denied as your disk has expired.|磁盘欠费过期。|
|403|DiskId.ValueNotSupported|The specified parameter diskid is not supported.|当前磁盘类型不支持此操作|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|账号余额不足，请您先充值再进行该操作。|
|404|InvalidVolumeId.NotFound|The specified volume does not exist.|指定的共享块存储不存在，请您检查共享块存储是否正确。|
|403|IdempotentParameterMismatch|The specified clientToken is used.|指定的token已被使用。|
|403|IncorrectDiskStatus.Invalid|The specified device status invalid, restart instance and try again.|指定磁盘的状态无效，请重启实例后重试。|
|403|IncorrectDiskType.NotSupport|The specified device type is not supported.|指定磁盘存储类型不支持此操作。|
|403|IncorrectDiskStatus.Transferring|The specified device is transferring, you can retry after the process is finished.|指定磁盘正在迁移中，请在迁移完毕后重试。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

