# ReleaseDedicatedHost {#doc_api_Ecs_ReleaseDedicatedHost .reference}

调用ReleaseDedicatedHost释放一台按量付费专有宿主机。

## 接口说明 {#description .section}

释放按量付费专有宿主机之前，请确保该宿主机上不存在任何ECS实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=ReleaseDedicatedHost&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DedicatedHostId|String|是|dh-xxxxxxxxxxxxxxxxx|专有宿主机ID。

 |
|RegionId|String|是|cn-hangzhou|专有宿主机所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|ReleaseDedicatedHost|系统规定参数。取值：ReleaseDedicatedHost

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A1B15AC8-E6F6-49A4-8985-8C07104B9199|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://ecs.aliyuncs.com/?Action=ReleaseDedicatedHost
&DedicatedHostId=dh-xxxxxxxxxxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ReleaseDedicatedHostResponse>
    <RequestId>A1B15AC8-E6F6-49A4-8985-8C07104B9199</RequestId>
</ReleaseDedicatedHostResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A1B15AC8-E6F6-49A4-8985-8C07104B9199"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|InstanceExist|Instance exists on the dedicated host.|还有实例在宿主机上，不支持释放。|
|400|ChargeTypeViolation|The operation is not permitted due to charge type of the dedicated host.|当前宿主机付费类型不支持释放操作。|
|400|IncorrectHostStatus.Initializing|The specified dedicatedHost status is not support this operation|当前宿主机状态不支持当前操作。|
|404|InvalidDedicatedHostId.NotFound|The specified DedicatedHostId does not exist.|指定的专有宿主机ID不存在。|
|500|InternalError|The request processing has failed due to some unknown error.|内部错误，请重试。如果多次尝试失败，请提交工单。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

