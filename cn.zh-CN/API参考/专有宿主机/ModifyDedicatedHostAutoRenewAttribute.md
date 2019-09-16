# ModifyDedicatedHostAutoRenewAttribute {#doc_api_Ecs_ModifyDedicatedHostAutoRenewAttribute .reference}

调用ModifyDedicatedHostAutoRenewAttribute为一台或多台包年包月专有宿主机设置自动续费，也可以取消已设定的自动续费。

## 接口说明 {#description .section}

包年包月专有宿主机到期前九天自动续费，扣费在08:00:00（UTC +8）时间点自动执行。如果前一日扣费失败，次日继续定时执行。扣费成功或者九天之后专有宿主机到期被锁定后停止自动扣费。期间，您需要保证自己的支付方式使用额度充足即可。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=ModifyDedicatedHostAutoRenewAttribute&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DedicatedHostIds|String|是|ddh-xxxxxxxxxxxxxxxxx|专有宿主机ID。最多可以输入100个包年包月专有宿主机ID，ID之间用半角逗号（,）隔开。

 |
|RegionId|String|是|cn-hangzhou|专有宿主机所属的地域ID。

 |
|Action|String|否|ModifyDedicatedHostAutoRenewAttribute|系统规定参数。取值：ModifyDedicatedHostAutoRenewAttribute

 |
|AutoRenew|Boolean|否|false|是否自动续费包年包月专有宿主机。取值范围：

 -   true：自动续费包年包月专有宿主机。
-   false（默认）：不自动续费包年包月专有宿主机。

 |
|Duration|Integer|否|1|续费周期。取值范围：请参见**PeriodUnit**参数的描述部分。

 |
|PeriodUnit|String|否|Month|续费时长单位。取值范围：

 -   Week：周。此时，参数**Duration**取值范围为 \{1, 2, 3\}。
-   Month（默认）：月。此时，参数**Duration**的取值范围为 \{ 1, 2, 3, 6, 12\}。

 |
|RenewalStatus|String|否|Normal|是否自动续费包年包月专有宿主机，参数**RenewalStatus**的优先级高于**AutoRenew**。取值范围：

 -   AutoRenewal：自动续费。
-   Normal：待续费。
-   NotRenewal：不续费，也不发送到期提醒。到期前第三天我们会发送不续费提醒。不续费的专有宿主机可以设置成待续费（Normal），再自行续费（[RenewDedicatedHosts](~~93287~~)）或设置为自动续费（AutoRenewal）。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2A4EA075-CB5B-41B7-B0EB-70D339F64DE7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://ecs.aliyuncs.com/?Action=ModifyDedicatedHostAutoRenewAttribute
&DedicatedHostIds=ddh-xxxxxxxxxxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyDedicatedHostAutoRenewAttributeResponse>
    <RequestId>2A4EA075-CB5B-41B7-B0EB-70D339F64DE7</RequestId>
</ModifyDedicatedHostAutoRenewAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"2A4EA075-CB5B-41B7-B0EB-70D339F64DE7"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|MissingParameter.DedicatedHostId|DedicatedHostId should not be null.|宿主机ID不能为空。|
|403|InvalidParameter.ToManyDedicatedHostIds|DedicatedHostId should be less than 100.|DedicatedHostIds最多支持100个宿主机。|
|403|InvalidParameter.InvalidDedicatedHostId|%s|DedicatedHostId参数无效。|
|403|IncorrectHostStatus|The current status of the resource does not support this operation.|当前宿主机状态不支持当前操作。|
|403|ChargeTypeViolation|Pay-As-You-Go dedicated host do not support this operation.|按量的宿主机不支持当前操作。|
|403|InvalidParameter.Duration|%s|Duration参数无效。|
|403|InvalidParameter.RenewalStatus|%s|RenewalStatus参数无效。|
|403|InvalidPeriodUnit.ValueNotSupported|The specified parameter PeriodUnit is not valid.|市场单位不支持。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

