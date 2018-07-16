# ConvertNatPublicIpToEip {#ConvertNatPublicIpToEip .reference}

将一台网络类型为 [专有网络 VPC](../../../../cn.zh-CN/产品简介/什么是专有网络.md#) 的 ECS 实例的公网 IP（NatPublicIp）转化为 [弹性公网 IP（EIP）](../../../../cn.zh-CN/产品简介/什么是弹性公网IP.md#)。

## 描述 {#section_o52_y3n_ydb .section}

调用该接口时，您需要注意：

-   仅支持 VPC 网络类型的 ECS 实例。

-   仅支持状态为 **已停止**（`Stopped`）或者 **运行中**（`Running`）的 ECS 实例。

-   不支持公网带宽为 0 Mbps 的 ECS 实例，即该 ECS 实例没有分配公网 IP（`NatPublicIp`）。

-   不支持已经绑定了 EIP 的 ECS 实例。

-   不支持有未生效的变更配置任务 ECS 实例。

-   不支持即将在 24 小时内到期的 ECS 实例。

-   公网 IP（`NatPublicIp`）转换为 EIP 后，EIP 将单独计费，EIP 的计费方式参阅文档 [EIP 计费说明](../../../../cn.zh-CN/产品定价/预付费.md#)。

-   不支持 [公网带宽](../../../../cn.zh-CN/产品定价/公网带宽计费.md#) 为 **按固定带宽计费** 的 [包年包月](../../../../cn.zh-CN/产品定价/包年包月.md#) ECS 实例。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：ConvertNatPublicIpToEip|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API 参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|InstanceId|String|是|需要转化公网 IP 的 ECS 实例 ID。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求 ID|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=ConvertNatPublicIpToEip
&RegionId=cn-hangzhou
&InstanceId=i-test
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<ConvertNatPublicIpToEipResponse>
    <RequestId>B154D309-F3E1-4AB7-BA94-FEFCA8B89001</RequestId>
</ConvertNatPublicIpToEipResponse>
```

 **JSON 格式** 

```
{
   "RequestId":"B154D309-F3E1-4AB7-BA94-FEFCA8B89001"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidRegionId.Malformed|The specified RegionId is invalid.|400|指定的 `RegionId` 不存在或者未授权。|
|InvalidEndTime.Malformed|The specified instance is about to expire within 24 hours.|403|实例即将在 24 小时内到期，不能变更公网 IP。|
|InvalidInstanceId.PlanedChange|The instance has uncompleted changes.|403|实例有未生效的变更配置任务。|
|InvalidInstanceStatus.Released|The specified instance has been released.|403|指定的实例已经被释放。|
|IncorrectInstanceStatus|The instance status does not support this operation. The instance may be expired, upgrading, starting, or locked.|404|仅支持 **已停止**（`Stopped`）和 **运行中**（`Running`）的 ECS 实例。|
|InstanceTypeNotSupported|The specified instance is a subscription instance with a specified bandwidth.|404|指定的实例是包年包月固定带宽类型的实例。|
|InvalidInstance.ZeroBandwidth|The public network bandwidth for the specified instance is zero. That is, this instance does not have a public IP.|404|实例公网带宽为 0 Mbps，即，该实例无公网 IP。|
|InvalidInstanceId.NotFound|The specified instance does not exist, or does not belong to you.|404|指定的实例不存在或者归属不正确。|
|OperationDenied|The network type of the specified instance is not VPC.|404|指定的实例的网络类型不是 VPC。|

