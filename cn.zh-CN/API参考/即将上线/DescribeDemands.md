# DescribeDemands {#doc_api_1063470 .reference}

查询报备资源的交付及使用状态。您可通过该接口查询客户经理为您报备的资源详情，包括报备资源类型、资源的交付情况、资源的消费情况。

## 接口说明 {#description .section}

仅支持查询I/O优化ECS实例的报备资源。网络类型必须是VPC。

**说明：** 该接口正在内测调整中，尚未正式上线，暂时不建议使用，请您耐心等待。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeDemands)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|目标地域 ID。您可以调用 [DescribeRegions](https://help.aliyun.com/document_detail/25609.html?spm=a2c4g.11186623.2.14.5044431dYU5SoJ) 查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeDemands|接口名称。取值：DescribeDemands

 |
|DemandStatus.N|RepeatList|否|Active|报备单状态。取值范围：

 -   Creating：报备单创建中
-   Active：供应中
-   Expired：截止可用时间前未消费完毕
-   Finished：消费完毕
-   Cancelled：报备取消

 |
|DryRun|Boolean|否|false|是否只预检此次请求。

 -   true：发送检查请求，不会查询报备单状况。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码DryRunOperation。
-   false（默认值）：发送正常请求，通过检查后返回2XX HTTP状态码并直接查询报备单状况。

 |
|InstanceChargeType|String|否|PostPaid|实例的计费方式。取值范围：

 -   PostPaid：按量付费
-   PrePaid：包年包月

 |
|InstanceType|String|否|ecs.g5.large|报备实例的规格。

 |
|InstanceTypeFamily|String|否|ecs.g5|报备实例的规格族。

 |
|PageNumber|Integer|否|1|报备单列表的页码。起始值：1

 默认值：1

 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。最大值：100

 默认值：10

 |
|Tag.N.Key|String|否|FinanceDept|标签键。n的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持64个字符，不能以aliyun、acs:、http:// 或者 https:// 开头。

 |
|Tag.N.Value|String|否|FinanceDeptJoshua|标签值。n的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持128个字符，不能以aliyun、acs:、http:// 或者 https:// 开头。

 |
|ZoneId|String|否|cn-hangzhou-g|可用区ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Demands| | |指定地域符合过滤条件的报备单

 |
|└AvailableAmount|Integer|10|报备资源当前可使用实例数量

 |
|└DeliveringAmount|Integer|20| 

 报备资源中待交付实例数量

 |
|└DemandStatus|String|Active|报备单的状态。可能值：

 -   Creating：创建中
-   Active：供应中
-   Expired：过期。报备时期望购买时间已到期；过期后报备资源会释放，交付状态无效
-   Finished：完成。报备资源已消费完毕
-   Cancelled：已取消。报备取消后，资源交付状态无效

 |
|└DemandTime|String|2019-02-26T12:00Z|报备单创建时间。按照ISO8601标准表示，并需要使用UTC时间，格式为yyyy-MM-ddTHH:mmZ

 |
|└EndTime|String|2019-03-03T15:00Z|报备资源预期截止购买时间。按照ISO8601标准表示，并需要使用UTC时间，格式为yyyy-MM-ddTHH:mmZ

 |
|└InstanceChargeType|String|Prepaid|报备资源的计费方式。可能值：

 -   Prepaid
-   Postpaid

 |
|└InstanceType|String|ecs.g5.xlarge|报备的实例规格

 |
|└InstanceTypeFamily|String|ecs.g5|报备实例所属的规格族

 |
|└Period|Integer|3|报备资源的使用时长

 |
|└PeriodUnit|String|Month|报备资源的使用时长计费单位。可能值：

 -   Hour
-   Day
-   Week
-   Month

 |
|└StartTime|String|2019-02-27T12:00Z|报备资源预期开始购买时间。按照ISO8601标准表示，并需要使用UTC时间，格式为yyyy-MM-ddTHH:mmZ

 |
|└SupplyInfos| | |报备资源的交付状态

 |
|└Amount|Integer|30|本次交付的实例数量

 |
|└SupplyEndTime|String|2019-03-03T15:00Z|资源交付可用的截止时间。按照ISO8601标准表示，并需要使用UTC时间，格式为yyyy-MM-ddTHH:mmZ

 |
|└SupplyStartTime|String|2019-03-01T14:00Z|资源交付可用的开始时间。按照ISO8601标准表示，并需要使用UTC时间，格式为yyyy-MM-ddTHH:mmZ

 |
|└SupplyStatus|String|Delivering|资源交付状态。可能值：

 -   Delivered ：已交付，资源可用
-   Delivering：交付中

 |
|└TotalAmount|Integer|50|报备的实例数

 |
|└UsedAmount|Integer|20|已经消耗的实例数

 |
|└ZoneId|String|cn-hangzhou-g|报备资源所在的可用区

 |
|PageNumber|Integer|1|报备单列表的页码。

 |
|PageSize|Integer|10|输入时设置的每页行数

 |
|RegionId|String|cn-hangzhou|查询的地域

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID

 |
|TotalCount|Integer|6|查询到的报备单数量

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DescribeDemands
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDemandsResponse>
  <Demands>
    <AvailableAmount>0</AvailableAmount>
    <DeliveringAmount>50</DeliveringAmount>
    <DemandStatus>Expired</DemandStatus>
    <DemandTime>2019-02-26T12:00Z</DemandTime>
    <EndTime>2019-03-03T15:00Z</EndTime>
    <InstanceChargeType>PrePaid</InstanceChargeType>
    <InstanceType>ecs.g5.4xlarge</InstanceType>
    <InstanceTypeFamily>ecs.g5</InstanceTypeFamily>
    <Period>3</Period>
    <PeriodUnit>Month</PeriodUnit>
    <StartTime>2019-02-27T12:00Z</StartTime>
    <SupplyInfos>
      <Amount>50</Amount>
      <SupplyEndTime>2019-03-03T15:00Z</SupplyEndTime>
      <SupplyStartTime>2019-03-01T14:00Z</SupplyStartTime>
      <SupplyStatus>Delivering</SupplyStatus>
    </SupplyInfos>
    <TotalAmount>50</TotalAmount>
    <UsedAmount>0</UsedAmount>
    <ZoneId>cn-hangzhou-g</ZoneId>
  </Demands>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RegionId>cn-hangzhou</RegionId>
  <RequestId>04066112-BF3A-4FCD-ABBD-B4B5EDAE9DXX</RequestId>
  <TotalCount>1</TotalCount>
</DescribeDemandsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"Demands":[
		{
			"Period":3,
			"DemandTime":"2019-02-26T12:00Z",
			"InstanceTypeFamily":"ecs.g5",
			"AvailableAmount":0,
			"ZoneId":"cn-hangzhou-g",
			"UsedAmount":0,
			"DeliveringAmount":50,
			"InstanceType":"ecs.g5.4xlarge",
			"DemandStatus":"Expired",
			"EndTime":"2019-03-03T15:00Z",
			"TotalAmount":50,
			"StartTime":"2019-02-27T12:00Z",
			"SupplyInfos":[
				{
					"Amount":"50",
					"SupplyStartTime":"2019-03-01T14:00Z",
					"SupplyEndTime":"2019-03-03T15:00Z",
					"SupplyStatus":"Delivering"
				}
			],
			"InstanceChargeType":"PrePaid",
			"PeriodUnit":"Month"
		}
	],
	"RequestId":"04066112-BF3A-4FCD-ABBD-B4B5EDAE9DXX",
	"RegionId":"cn-hangzhou"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|指定的实例升降配规格不存在。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

-   缺失RegionId时会报错400-MissingParamter.RegionId-The regionId should not be null.
-   计费方式取值错误时会报错404-InvalidInstanceChargeType.NotFound-The InstanceChargeType does not exist in our records
-   DemandStatus取值错误时会报错-404-InvalidStatus.ValueNotSupported-The DemandStatus does not exist in our records
-   阿里云地域ID取值错误时会报错-400-InvalidRegion.NotFound-The RegionId provided does not exist in our records.
-   可用区ID取值错误时会报错-404-InvalidZone.NotFound-The ZoneId provided does not exist in our records.
-   实例规格取值错误时会报错-404-InvalidInstanceType.NotFound-The InstanceType provided does not exist in our records.
-   实例规格与规格族不匹配时会报错-404-InvalidInstanceType.NotMatch-The InstanceType provided does match the InstanceTypeFamily in our records.

