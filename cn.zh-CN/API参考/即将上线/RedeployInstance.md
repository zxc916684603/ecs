# RedeployInstance {#RedeployInstance .reference}

当 ECS 实例收到系统事件通知时，RedeployInstance 可以重新部署这台实例。

## 描述 {#Limits .section}

RedeployInstance 为异步调用接口，会重启迁移实例。重新部署成功后，实例进入 **运行中**（`Running`）状态。重新部署失败时，实例返回原有的物理服务器，进入 **已停止**（`Stopped`）状态。调用该接口时，您需要注意：

-   RedeployInstance 能响应以下系统事件类型，更多有关系统事件的详情，请参阅 [系统事件](../cn.zh-CN/用户指南/运维与监控/系统事件.md#)：

    -   **待执行**（`Scheduled`）状态下的实例重启（`SystemMaintenance.Reboot`）事件和实例重新部署（`SystemMaintenance.Redeploy`）事件。

    -   **执行中**（`Executing`）状态下的实例异常重启（`SystemFailure.Reboot`）事件（仅支持本地盘实例规格）。

**警告：** 重新部署本地盘实例会重新初始化本地盘，磁盘数据被清空。请慎重操作。

-   目标实例必须处于运行中或者已停止状态，调用接口后的实例状态变化：

    -   处于 **运行中**（`Running`）的实例会进入 **停止中**（`Stopping`）状态。

    -   处于 **已停止**（`Stopped`）的实例会进入 **启动中**（`Starting`）状态。

-   被安全控制的实例的 OperationLocks 中标记了 `"LockReason": "security"` 时，不支持重新部署。

-   不支持重新部署专有宿主机上的实例。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|接口名称。取值: RedeployInstance|
|InstanceId|String|是|处于运行中或者已停止状态的实例 ID。|
|ForceStop|Boolean|否|是否强制停止 **运行中**（`Running`）的实例。默认值：false**说明：** 强制停止等同于典型的服务器断电关机，实例操作系统中暂未写入磁盘的数据会丢失。建议您尽量对已停止实例做重新部署操作。

|

## 返回参数 {#ResponseParameter .section}

全是公共返回参数。参阅[公共返回参数](../cn.zh-CN/API参考/HTTP调用方式/公共参数.md#commonResponseParameters)。

## 示例 {#Samples .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=RedeployInstance
&InstanceId=i-instance1
&<公共请求参数>
```

**返回示例**

**XML 格式**

```
<RedeployInstanceResponse>
    <RequestId>1C488B66-B819-4D14-8711-C4EAAA13AC01</RequestId>
</RedeployInstanceResponse>
```

**JSON 格式**

```
{
    "RequestId": "1C488B66-B819-4D14-8711-C4EAAA13AC01"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问[API错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|DiskError|IncorrectDiskStatus|403|实例挂载的磁盘处于异常状态。|
|IncorrectInstanceStatus|The current status of the resource does not support this operation|403|目标实例必须处于运行中或者已停止状态。|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons|403|实例目前被安全锁定，不支持重新部署。|
|InvalidOperation.RedeployInstance|There are no maintenance events found on the instance|403|实例没有发生系统事件，禁止重新部署。|
|InvalidOperation.RedeployInstance|Can not redeploy vm on dedicated host|403|无法重新部署专有宿主机上的实例。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist|404|指定的 InstanceId 不存在。|
|InternalError|The request processing has failed due to some unknown error|500|内部错误，请重试。 如果多次尝试失败，请 [提交工单](https://selfservice.console.aliyun.com/ticket/createIndex.htm) 联系阿里云。

|

