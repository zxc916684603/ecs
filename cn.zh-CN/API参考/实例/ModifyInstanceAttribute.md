# ModifyInstanceAttribute {#ModifyInstanceAttribute .reference}

修改一台实例的部分信息，包括实例密码、名称、描述、主机名和自定义数据等。

## 描述 {#section_ufy_4pt_xdb .section}

调用该接口时，您需要注意：

-   实例状态为 **已释放**（`Deleted`）或 **启动中**（`Starting`）时，无法重置实例密码。

-   被 [安全控制](intl.zh-CN/API参考/附录/安全锁定时的 API 行为.md#) 的实例的 `OperationLocks` 中标记了 `"LockReason" : "security"` 时，无法重置实例密码。

-   重置密码后，您需要在控制台 [重启实例](../intl.zh-CN/用户指南/实例/重启实例.md#) 或者调用 [RebootInstance](intl.zh-CN/API参考/实例/RebootInstance.md#) 使更改生效，在实例内部重启将不会生效。

-   实例状态为 **已停止**（`Stopped`）且满足 [实例自定义数据](../intl.zh-CN/用户指南/实例/实例自定义/元数据/实例自定义数据.md) 使用限制时，支持修改自定义数据。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：ModifyInstanceAttribute|
|InstanceId|String|是|实例 ID。|
|InstanceName|String|否|实例名称。长度为 \[2, 128\] 英文或中文字符，必须以大小字母或中文开头，可包含数字，点号（.）、半角冒号（:）、下划线（\_）和连字符（-）。不能以 http:// 和 https:// 开头。|
|Description|String|否|实例描述。长度为 \[2, 256\] 个字符。不能以 http:// 和 https:// 开头。默认值：空。|
|Password|String|否|实例密码。长度为 \[8, 30\] 个字符，必须同时包含大小写字母、数字和特殊字符。特殊字符：\( \) \` ~ ! @ \# $ % ^ & \* - + = | \{ \} \[ \] : ; ‘ < < , . ? /如果传入 `Password` 参数，您需要使用 HTTPS 调用方式，避免密码泄露。

|
|HostName|String|否|操作系统内部的计算机名。点号（.）和连字符（-）不能作为主机名的首尾字符，也不能连续使用。-   **Windows 实例**：长度为 \[2, 15\] 个字符，支持字母、数字和连字符（-），不支持点号（.），不能全是数字。
-   **Unix 类实例**：长度为 \[2, 30\] 个字符，允许支持多个点号，点与点之间为一段，每段允许字母、数字和连字符（-）。

|
|UserData|String|否|实例自定义数据，需要以 Base64 编码。编码前，原始数据不能超过 16 KB。建议不要明文传入敏感信息，例如密码和私钥等。如果必须传入敏感信息，建议您加密后再以 Base64 编码传入，在实例内部以同样的方式反解密。|

## 返回参数 {#ResponseParameter .section}

全是公共返回参数。参阅 [公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#commonResponseParameters)

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceAttribute
&InstanceId=i-instance1
&Password=pwd
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<ModifyInstanceAttributeResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyInstanceAttributeResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidDescription.Malformed|The specified parameter “Description” is not valid.|400|指定的 `Description`格式不正确。|
|InvalidDescription.Malformed|The specified destination image description is wrongly formed.|400|指定的 `Description`不合法。|
|InvalidHostPassword.Malformed|The specified parameter “Password” is not valid.|400|指定的 `Password` 不合法。|
|InvalidInstanceName.Malformed|The specified parameter “InstanceName” is not valid.|400|指定的 `InstanceName`不合法。|
|InvalidHostName.Malformed|The specified parameter “HostName” is not valid.|400|指定的 `HostName` 不合法。|
|InvalidPassword.Malformed|The specified parameter “Password” is not valid.|400|指定的 `Password` 不合法。|
|InvalidUserData.SizeExceeded|The specified parameter “UserData” exceeds the size.|400|Base64 编码 `UserData` 前，原始数据不能超过 16 KB。|
|InvalidUserData.NotSupported|The specified parameter “UserData” only support the vpc and IoOptimized Instance.|400|`UserData` 只适用于 VPC 类型实例和 I/O 优化实例。|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|该资源目前的状态不支持此操作。|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|实例目前被安全锁定，拒绝操作。|
|OperationDenied|The Specified operation is denied as your instance is locked for security reasons.|403|实例已经被锁定。|
|OperationDenied|The current status of the resource does not support this operation.|403|实例状态不支持该操作。|
|HOSTNAME\_ILLEGAL|hostname is not valid.|404|指定的 `hostname` 不合法。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的 `InstanceId` 不存在。|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|指定的 `SecurityGroupId` 不存在。|

