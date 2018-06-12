# CreateSecurityGroup {#CreateSecurityGroup .reference}

新建一个安全组。新建的安全组，默认只允许安全组内实例互相访问，安全组外的一切通信请求会被拒绝。若您想允许其他安全组实例的通信请求，或者来自互联网的访问请求，需要授权安全组权限（[AuthorizeSecurityGroup](intl.zh-CN/API参考/安全组/AuthorizeSecurityGroup.md#)）。

## 描述 {#section_w5n_p21_ydb .section}

调用该接口时，您需要注意：

-   您最多可创建 100 个安全组。

-   创建专有网络 VPC 类型的安全组时，您必须指定参数 `VpcId`。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：CreateSecurityGroup|
|RegionId|String|是|安全组所属地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|SecurityGroupName|String|否|安全组名称。-   长度为 \[2, 128\] 个字符，必须以大小字母或中文开头，可以包含数字、点号（.）、下划线（\_）或者连字符（-）。
-   不能以 http:// 和 https:// 开头。

默认值：空。|
|Description|String|否|安全组描述信息。-   长度为 \[2, 256\] 个英文或中文字符。
-   不能以 http:// 和 https:// 开头。

默认值：空。|
|VpcId|String|否|安全组所属 VPC ID。|
|ClientToken|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一。只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](intl.zh-CN/API参考/附录/如何保证幂等性.md#)。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|SecurityGroupId|String|安全组 ID|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=CreateSecurityGroup
&RegionId=cn-hangzhou
&Description=for_demo
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<CreateSecurityGroupResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    <SecurityGroupId>sg-F876FF7BA</SecurityGroupId>
</CreateSecurityGroupResponse>
```

 **JSON 格式** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
    "SecurityGroupId":"sg-F876FF7BA"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|IncorrectVpcStatus|Current VPC status does not support this operation.|400|指定的 VPC 正在被创建、编辑或者删除，请稍后再试。|
|InvalidDescription.Malformed|The specified parameter “Description” is not valid.|400|指定的 `Description`不合法。|
|InvalidSecurityGroupDiscription.Malformed|Specified security group description is not valid.|400|指定的 `Description`不合法。|
|InvalidSecurityGroupName.Malformed|Specified security group name is not valid.|400|指定的 `SecurityGroupName`不合法。|
|InvalidVpcId.NotFound|vpc id must not empty when only support vpc vm.|403|参数 `VpcId` 不能为空。|
|QuotaExceed.SecurityGroup|The maximum number of security groups is reached.|403|您最多可以创建 100 个安全组。|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|指定的 `RegionId` 不存在。|
|InvalidVpcId.NotFound|Specified VPC does not exist.|404|指定的 VPC 不存在。|

