# InvokeCommand {#InvokeCommand .reference}

为一台或多台 ECS 实例触发一条云助手命令。

## 描述 {#section_amn_fm4_ydb .section}

当您使用该接口时，请注意：

-   该接口仅支持专有网络（VPC）实例。
-   目标 ECS 实例的状态必须为 **运行中**（`Running`）。
-   目标 ECS 实例必须预先安装 [云助手客户端](../intl.zh-CN/产品简介/云助手/云助手客户端.md#)。
-   执行类型为 PowerShell 的命令时，您需要确保目标 ECS Windows 实例已经配置了 PowerShell 模块。
-   对于单次执行（`Timed=False`），只执行一次命令。
-   对于周期执行（`Timed=True`），第一次将根据参数 `Frequency` 指定的时间点开始执行任务，后续按照参数 `Frequency` 的指定的时间定时执行。上次的执行结果不对下一次执行产生任何影响。
-   周期执行的时间设置基准为 UTC +08:00，且该时间以 ECS 实例的系统时间为准，您需要确保您的 ECS 实例的时间或者时区与您预期的时间一致。
-   您可以选择多个 ECS 实例，若其中某个实例不满足执行条件时，您需要重新选择。
-   命令的执行可能会因为目标实例的状态异常、网络异常或云助手客户端异常而出现无法执行的情况，无法执行时不会生成执行信息。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：InvokeCommand|
|RegionId|String|是|地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|InstanceIds|Array|是|需要执行命令的实例列表。参数取值为一个带有格式的 Json Array，格式为 \[`InstanceId1`, `instanceId2`, …\]，最多能指定 100 台实例 ID，用半角逗号字符隔开。|
|CommandId|String|是|命令 ID。您可以通过接口 [DescribeCommands](intl.zh-CN/API参考/云助手/DescribeCommands.md#) 查询所有可用的 `CommandId`。|
|Timed|Boolean|否|命令是否为周期执行。取值范围：-   True：是周期执行
-   False：不是周期执行

默认值：False|
|Frequency|String|否|周期任务的执行周期。当参数 [`Timed`](#Timed) 的值为 `True` 时，参数 `Frequency` 为必需参数。该参数取值遵循 Cron 表达式，参阅 [Cron 表达式](https://help.aliyun.com/document_detail/64769.html)[Cron 表达式](https://www.alibabacloud.com/help/faq-detail/64769.htm)。

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|InvokeId|String|命令执行 ID|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=InvokeCommand
&RegionId=cn-hangzhou
&InstanceIds=i-bp185dy2o3o6nxxxxxxx
&CommandId=c-e996287206324975b5fbe1dxxxxxxxxx
&Timed=true
&Frequency=0 0-5 14 * * ?
&<公共请求参数>
```

**正常返回示例** 

**XML 格式**

```
<InvokeCommandResponse>
    <RequestId>540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx</RequestId>
    <InvokeId>t-1fad2a8876de47068cc734d5xxxxxxxxx</InvokeId>
</InvokeCommandResponse>
```

 **JSON 格式** 

```
{
    "RequestId":"540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx",
    "InvokeId":"t-1fad2a8876de47068cc734d5xxxxxxxxx"
}
```

**异常返回示例** 

**XML 格式**

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.CommandId</Code>
    <Message>The input parameter “CommandId” that is mandatory for processing this request is not supplied.</Message>
</Error>
```

 **JSON 格式** 

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.CommandId"
    "Message": "The input parameter “CommandId” that is mandatory for processing this request is not supplied."
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidInstance.NoClient|The specified instances have no cloud assistant client installed.|400|指定的 ECS 实例中未安装云助手客户端。您可以参阅 [云助手客户端](../intl.zh-CN/产品简介/云助手/云助手客户端.md#) 安装并使用云助手客户端。|
|InvalidInstance.NotVpc|The specified instances must be VPC instances.|400|参数 `InstanceIds` 只能包含 VPC 实例的 ID。|
|InvalidInstanceStatus|The specified instance’s status can not execute this operation|400|指定实例的状态必须为运行中；或者指定实例的网络状态异常。|
|MissingParameter.CommandId|The input parameter “CommandId” that is mandatory for processing this request is not supplied.|400|您必须指定必需参数 `CommandId`。|
|MissingParameter.InstanceIds|The input parameter “InstanceIds” that is mandatory for processing this request is not supplied.|400|您必须指定必需参数 `InstanceIds`。|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|您必须指定必需参数 `RegionId`，或者您暂时不能使用指定 `RegionId` 里的资源。|
|MissingParameter.Frequency|The frequency parameter must exist when create a timed Invocation.|400|当参数 `Timed` 的值为 `True` 时，您必须指定参数 `Frequency`。|
|InvalidCmdId.NotFound|The specified commandId does not exist.|404|指定的 `CommandId` 不存在。|
|InvalidInstance.NotFound|The specified instances does not exist.|404|指定的 `InstanceId` 不存在。|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|指定的 `RegionId` 不存在。|
|InternalError.Dispatch|An internal error occurred when dispatching your request.|500|内部错误，请稍后尝试。|

