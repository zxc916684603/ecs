# AttachInstanceRamRole {#AttachInstanceRamRole .reference}

为一台或多台 ECS 实例授予 [实例 RAM 角色](../intl.zh-CN/用户指南/实例/实例RAM角色.md#)。如果实例已有 RAM 角色，则报错提示您不能附加新的角色。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：AttachInstanceRamRole|
|RegionId|String|是|地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|InstanceIds|Array|是|实例 ID 的集合，最多 100 台实例，\[“instanceId1”, “instanceId2”, “instanceId3”…\]。|
|RamRoleName|String|是|实例 RAM 角色名称。您可以使用 *RAM* API [ListRoles](../../intl.zh-CN/API参考/API 参考（RAM）/角色管理接口/ListRoles.md#) 查询实例RAM角色名称。参考相关 API [CreateRole](../../intl.zh-CN/API参考/API 参考（RAM）/角色管理接口/CreateRole.md#) 和 [ListRoles](../../intl.zh-CN/API参考/API 参考（RAM）/角色管理接口/ListRoles.md#) 。|

## 返回参数 {#ResponseParameter .section}

全是公共返回参数。详见[公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#commonResponseParameters)

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=AttachInstanceRamRole
&RegionId=cn-hangzhou
&RamRoleName=RamRoleTest
&InstanceIds=["i-instance1"]
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<AttachInstanceRamRoleResponse>
    <RequestId>E6352369-5C2B-41CD-AB50-471550C8F674</RequestId>
    <AttachInstanceRamRoleResults>
        <AttachInstanceRamRoleResult>
             <InstanceId>i-instance1</InstanceId>
             <Code>200</Code>
             <Message>success</Message>
        </AttachInstanceRamRoleResult>
    </AttachInstanceRamRoleResults>
    <TotalCount>1</TotalCount>
    <FailCount>0</FailCount>
    <RamRoleName>RamRoleTest</RamRoleName>
</AttachInstanceRamRoleResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "D9553E4C-6C3A-4D66-AE79-9835AF705639",
    "AttachInstanceRamRoleResults": {
        "AttachInstanceRamRoleResult": [
            {
                "Message": "success",
                "InstanceId": "i-instance1",
                "Code": "200"
            }
        ]
    },
    "TotalCount": 1,
    "FailCount": 0,
    "RamRoleName": "RamRoleTest"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidInstanceIds.Malformed|The specified InstanceIds is not valid.|400|指定的 InstanceIds 不合法。|
|MissingParameter.InstanceIds|The input parameter InstanceIds that is mandatory for processing this request is missing.|400|缺少必需参数 InstanceIds。|
|MissingParameter.RamRoleName|The input parameter RamRoleName that is mandatory for processing this request is missing.|400|缺少必填参数 RamRoleName。|
|MissingParameter.RegionId|The input parameter RegionId that is mandatory for processing this request is missing.|400|缺少必填参数 RegionId。|
|InvalidNetworkType.MismatchRamRole|Ram role cannot be attached to instances of Classic network type.|403|实例 RAM 角色功能不能被用于经典网络实例。|
|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a role.|403|您使用的 RAM 用户账号暂不具有 PassRole 的权限，请联系主账号拥有者 [授权](../../intl.zh-CN/快速入门/为 RAM 用户授权.md#) PassRole 权限。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的实例 ID 不存在。|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|指定的 RamRoleName 不存在。|

