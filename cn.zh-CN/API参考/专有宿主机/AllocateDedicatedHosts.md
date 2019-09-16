# AllocateDedicatedHosts {#doc_api_Ecs_AllocateDedicatedHosts .reference}

调用AllocateDedicatedHosts创建一台或多台包年包月专有宿主机。专有宿主机DDH是由单租户独享的物理机资源，您可以在专有宿主机上自行创建ECS实例和获取物理服务器属性信息等。

## 接口说明 {#description .section}

创建专有宿主机前，您可以调用[DescribeAvailableResource](~~66186~~)查看指定地域或者可用区内的资源供给情况。

创建专有宿主机前会涉及到资源计费，建议您提前了解计费方式。更多详情，请参见[计费概述](~~68978~~)。

-   单次最多能创建100台包年包月专有宿主机。
-   创建成功后，会返回专有宿主机ID列表。您可通过该列表和[DescribeDedicatedHosts](~~93284~~)查询新建专有宿主机状态。
-   当新建专有宿主机状态为可用（Available）后，您可以在宿主机上开始创建ECS实例。关于专有宿主机的生命周期状态，请参见[生命周期](~~68981~~)。
-   提交创建任务后，参数不合规或者专有宿主机库存不足的情况下会报错。具体的报错原因，请参见错误码。
-   创建专有宿主机后，您可以通过[ModifyInstanceDeployment](~~91677~~)将ECS实例从共享宿主机迁移到专有宿主机，也可以在两台专有宿主机上调整实例部署。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=AllocateDedicatedHosts&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DedicatedHostType|String|是|ddh.c5|专有宿主机的规格。您可以调用[DescribeDedicatedHostTypes](~~93285~~)接口获得最新的专有宿主机规格表 。

 |
|RegionId|String|是|cn-hangzhou|专有宿主机所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|AllocateDedicatedHosts|系统规定参数。取值 ：AllocateDedicatedHosts

 |
|ActionOnMaintenance|String|否|Migrate|当专有宿主机发生故障或者在线修复时，为其所宿实例设置迁移方案。取值范围：

 -   Migrate：迁移实例到其他物理机并重新启动实例。

默认值：Migrate（当专有宿主机上挂载云盘存储时）

-   Stop：在当前专有宿主机上停止实例，确认无法修复专有宿主机后，迁移实例到其他物理机并重新启动实例。

默认值：Stop（当专有宿主机上挂载本地盘存储时）


 |
|AutoPlacement|String|否|off|专有宿主机是否加入自动部署资源池。当您在专有宿主机上创建实例，却不指定**DedicatedHostId**时，阿里云将自动从加入资源池的专有宿主机中，为您选取适合的宿主机部署实例，详情请参见[自动部署功能介绍](~~118938~~)。取值范围：

 -   on：加入自动部署资源池。
-   off：不加入自动部署资源池。

 默认值： on

 **说明：** 创建专有宿主机时：

 -   若您不设置该参数，则默认为专有宿主机加入自动部署资源池。
-   若您不希望专有宿主机加入自动部署资源池，请将该参数设置为off。

 |
|AutoReleaseTime|String|否|2019-08-21T12:30:24Z|专有宿主机自动释放时间。需按照ISO8601标准表示，并使用UTC+0时间。格式：yyyy-MM-ddTHH:mm:ssZ

 **说明：** 

 -   最短设置为当前时间之后半小时。
-   最长不能超过当前时间之后三年。
-   若参数值中的秒（ss）不是00，则自动取为00。

 |
|AutoRenew|Boolean|否|false|是否自动续费包年包月专有宿主机。

 **说明：** 当参数**ChargeType**取值PrePaid时， **AutoRenew**参数方可生效。

 默认值：false

 |
|AutoRenewPeriod|Integer|否|1|单次自动续费的周期，单位：月。取值范围：1 | 2 | 3 | 6 | 12

 **说明：** 当参数**AutoRenew**为true时，**AutoRenewPeriod**参数方可生效并为必填参数。

 |
|ChargeType|String|否|PrePaid|专有宿主机的计费方式。取值范围：PrePaid（包年包月）

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。只支持ASCII字符，且不能超过64个字符。更多详情，请参见[如何保证幂等性](~~25693~~)。

 |
|DedicatedHostName|String|否|myDDH|专有宿主机的名称。长度为2~128个英文或中文字符。必须以大小字母或中文开头，不能以http://和https://开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|Description|String|否|This-is-my-DDH|专有宿主机的描述。长度为2~256个英文或中文字符，不能以http://和https://开头。

 |
|NetworkAttributes.SlbUdpTimeout|Integer|否|60|负载均衡连接的UDP会话超时时间，单位：秒。取值范围：15~310

 |
|NetworkAttributes.UdpTimeout|Integer|否|60|为专有宿主机上运行的云服务设置用户访问的UDP会话超时时间，单位：秒。取值范围：15~310

 |
|Period|Integer|否|6|购买专有宿主机的包年包月时长。当参数**ChargeType**取值为PrePaid时， **Period**参数方可生效并为必填参数。

 使用中国站账号调用该API时，参数**Period**的取值范围如下：

 -   `PeriodUnit=Week`时，取值范围：\{1,2,3\}
-   `PeriodUnit=Month`时，取值范围：\{1,2,3,4,5,6,7,8,9\}
-   `PeriodUnit=Year`时，取值范围：\{1,2,3,4,5\}

 使用国际站账号调用该API时，参数**Period**的取值范围如下：

 -   `PeriodUnit=Month`时，取值范围：\{1,2,3,6\}
-   `PeriodUnit=Year`时，取值范围：\{1\}

 |
|PeriodUnit|String|否|Month|购买专有宿主机的时长。取值范围：Week | Month（默认）| Year

 |
|Quantity|Integer|否|1|本次创建的专有宿主机的数量。取值范围：1~100

 默认值：1

 |
|ResourceGroupId|String|否|myResourceGroupID|专有宿主机要加入的资源组ID。

 |
|Tag.N.Key|String|否|Environment|专有宿主机的标签键。n的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持64个字符，不能以aliyun、acs:、http://或者https://开头。

 |
|Tag.N.Value|String|否|Production|专有宿主机的标签值。n的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持128个字符，不能以aliyun、acs:、http://或者https://开头。

 |
|ZoneId|String|否|cn-hangzhou-f|专有宿主机所属的可用区编号。

 默认值：空，表示由系统选择。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DedicatedHostIdSets| |"DedicatedHostIdSets":\{ "DedicatedHostId":\[ "dh-dedicatedhost1", "dh-dedicatedhost2" \]|专有宿主机ID（DedicatedHostId）组成的列表。

 |
|DedicatedHostId| | |专有宿主机ID（DedicatedHostId）组成的列表。

 |
|RequestId|String|E2A664A6-2933-4C64-88AE-5033D003EADF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=AllocateDedicatedHosts
&RegionId=cn-hangzhou
&DedicatedHostType=ddh.sn1ne
&Quantity=2
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AllocateDedicatedHostsResponse>
    <RequestId>E2A664A6-2933-4C64-88AE-5033D003EADF</RequestId>
    <DedicatedHostIdSets>
        <DedicatedHostId>dh-dedicatedhost1</DedicatedHostId>
        <DedicatedHostId>dh-dedicatedhost2</DedicatedHostId>
    </DedicatedHostIdSets>
</AllocateDedicatedHostsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E2A664A6-2933-4C64-88AE-5033D003EADF",
	"DedicatedHostIdSets":{
		"DedicatedHostId":[
			"dh-dedicatedhost1",
			"dh-dedicatedhost2"
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|指定的实例规格未授权使用。|
|400|InvalidDescription.Malformed|The specified parameter "Description" is not valid.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|403|OperationDenied|The creation of Host to the specified Zone is not allowed.|无法在指定可用区创建专用宿主机。|
|403|OperationDenied.NoStock|The requested resource is sold out in the specified zone; try other types of resources or other regions and zones.|库存不足。|
|500|InternalError|The request processing has failed due to some unknown error.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|403|OperationDenied|Sales of this resource are temporarily suspended in the specified region; please try again later.|指定地域关闭。|
|400|InvalidParameter.Conflict|The specified region and cluster do not match.|指定的地域与指定的集群不匹配。|
|403|NodeControllerUnavailable|The Node Controller is temporarily unavailable.|节点控制器暂不可用。|
|404|OperationDenied|Another Host has been creating|宿主机已经在创建中。|
|403|OperationDenied|The resource is out of usage.|该实例不在运行状态，请您启动实例或检查操作是否合理。|
|404|PaymentMethodNotFound|No payment method has been registered on the account.|账户尚未注册支付方式。|
|404|InvalidDedicatedHostName.Malformed|The specified parameter DedicatedHostName is not valid.|DedicatedHostName参数无效。|
|403|InvalidParameter.ResourceOwnerAccount|ResourceOwnerAccount is Invalid.|指定的 ResourceOwnerAccount 不合法。|
|403|InvalidUserData.Forbidden|User not authorized to input the parameter "UserData", please apply for permission "UserData"|您未被授权设置UserDat。|
|403|Zone.NotOpen|The specified zone is not granted to you to buy resources yet.|用户未被授权购买指定的可用区的资源。|
|403|Zone.NotOnSale|The specified zone is not available for purchase.|指定可用区已经售罄，请您更换实例规格或者更换地域创建。|
|403|InvalidResourceType.NotSupported|This resource type is not supported; please try other resource types.|指定的资源搭配不存在（没有库存）。|
|403|InvalidDedicatedHostType.ValueNotSupported|The specified DedicatedHostType does not exist or beyond the permitted range.|指定的宿主机规格不存在。|
|403|InvalidDedicatedHostType.ZoneNotSupported|The specified zone does not support this dedicatedHostType.|指定可用区不支持指定宿主机规格。|
|400|InvalidAutoRenewPeriod.ValueNotSupported|The specified autoRenewPeriod is not valid.|指定的参数 AutoReleaseTime 不合法。|
|403|InvalidUserData.Base64FormatInvalid|The specified UserData is not valid|指定的 UaseData 不合法。|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|指定的标签键不合法。|
|400|InvalidDedicatedHostType.ValueNotSupported|%s|不支持指定的宿主机规格。|
|400|RegionUnauthorized|%s|指定地域不支持。|
|500|InternalError|%s|内部错误。|
|400|Zone.NotOnSale|%s|可用区关闭。|
|400|OperationDenied|The specified DedicatedHostType or Zone is not available or not authorized.|指定宿主机规格或者可用区不可用。|
|400|InvalidPeriodUnit.ValueNotSupported|The specified parameter PeriodUnit is not valid.|市场单位不支持。|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|指定的标签值不合法。|
|403|InvalidParameter.NotMatch|%s|参数冲突。|
|403|Account.Arrearage|Your account has been in arrears.|账户余额不足，请先充值再操作。|
|400|QuotaExceed.AfterpayDedicatedHost|The maximum number of Pay-As-You-Go DedicatedHosts is exceeded: %s|按量的宿主机的数量已满额。|
|400|InvalidChargeType.ValueNotSupported|ChargeType is not valid|付费类型无效。|
|400|InvalidParameter.SlbUdpTimeout|The specified value is invalid.|SlbUdpTimeout参数无效。|
|400|InvalidParameter.UdpTimeout|The specified value is invalid.|UdpTimeout参数无效。|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|标签键中存在重复的键。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

