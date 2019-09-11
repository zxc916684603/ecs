# DescribeRecommendInstanceType {#doc_api_Ecs_DescribeRecommendInstanceType .reference}

（Beta）调用DescribeRecommendInstanceType根据一个指定的的实例规格，查找一个或多个备选的实例规格。针对已经或者即将停售的实例规格，DescribeRecommendInstanceType会罗列出作为替补的所有实例规格。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeRecommendInstanceType&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|NetworkType|String|是|vpc|ECS实例的网络类型。取值范围：

 -   classic：经典网络。
-   vpc（默认）：专有网络VPC。

 |
|RegionId|String|是|cn-hangzhou|地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeRecommendInstanceType|系统规定参数。取值：DescribeRecommendInstanceType

 |
|InstanceType|String|否|ecs.s1.large|指定的实例规格。更多详情，请参见[实例规格族](~~25378~~)，也可以调用[DescribeInstanceTypes](~~25620~~)接口获得最新的规格表。

 **说明：** 如果您指定了`InstanceType`，则无法指定`Cores`或者`Memory`。

 |
|Memory|Float|否|8.0|ECS实例内存大小，单位为GiB。

 **说明：** 同时指定`Cores`参数和`Memory`参数会匹配所有满足vCPU核数和内存大小的实例规格。

 |
|Cores|Integer|否|2|ECS实例vCPU核数。

 **说明：** 同时指定`Cores`参数和`Memory`参数会匹配所有满足vCPU核数和内存大小的实例规格。

 |
|InstanceChargeType|String|否|PostPaid|ECS实例的计费方式。更多详情，请参见[计费概述](~~25398~~)。取值范围：

 -   PrePaid：包年包月。
-   PostPaid（默认）：按量付费。

 |
|SpotStrategy|String|否|NoSpot|抢占式实例的竞价策略。取值范围：

 -   NoSpot（默认）：正常按量付费实例。
-   SpotWithPriceLimit：设置上限价格的抢占式实例。
-   SpotAsPriceGo：系统自动出价，最高按量付费价格。

 使用`SpotStrategy`时，`InstanceChargerType`必须设置为`PostPaid`。

 |
|MaxPrice|Float|否|10.0|按量付费实例或者抢占式实例可接受的每小时最高价格。

 **说明：** 设置抢占式实例的最高单价时，`SpotStrategy`必须设置为`SpotWithPriceLimit`。

 |
|InstanceTypeFamily.N|RepeatList|否|ecs.g5|过滤不采纳的实例规格族集合，N的取值范围为1~10。规格族取值请参见[实例规格族](~~25378~~)。您也可以调用[DescribeInstanceTypeFamilys](~~25620~~)查询规格族列表。

 |
|PriorityStrategy|String|否|PriceFirst|优先推荐策略。取值范围：

 -   InventoryFirst（默认）：库存优先。
-   PriceFirst：价格优先，按每小时vCPU单价从低到高排序。
-   NewProductFirst：最新产品优先。

 |
|IoOptimized|String|否|optimized|是否为I/O优化实例。实例规格只支持非I/O优化时，不能设置IoOptimized参数。取值范围：

 -   optimized：I/O优化。
-   none：非IO优化。

 默认值：optimized。

 如果您设置的是已停售实例规格，默认为none。

 |
|ZoneId|String|否|cn-hangzhou-f|可用区ID。您可以调用[DescribeZones](~~25610~~)查看最新的阿里云可用区列表。

 |
|SystemDiskCategory|String|否|cloud\_ssd|系统盘的云盘种类。取值范围:

 -   cloud\_efficiency：高效云盘。
-   cloud\_ssd：SSD云盘。
-   cloud\_essd：ESSD云盘。
-   cloud：普通云盘。

 非I/O优化实例的默认值为：cloud。

 I/O优化实例的默认值为：cloud\_efficiency。

 |
|Scene|String|否|CREATE|在哪种场景下推荐实例规格。取值范围：

 -   UPGRADE：升级或降低实例规格。
-   CREATE（默认）：创建实例。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |推荐的实例规格集合。

 |
|RecommendInstanceType| | |推荐的实例规格集合。

 |
|CommodityCode|String|ecs|实例规格的商品编码。

 |
|InstanceChargeType|String|PostPaid|实例的计费方式。

 |
|InstanceType| | |实例规格名称。

 |
|Cores|Integer|1|实例规格的vCPU核数。

 |
|Generation|String|ecs-1|实例规格族系列。

 |
|InstanceType|String|ecs.s1.large|实例规格名称。

 |
|InstanceTypeFamily|String|ecs.s1|实例规格族。

 |
|Memory|Integer|8192|实例规格的内存大小，单位为MiB。

 |
|SupportIoOptimized|String|none|实例规格是否支持I/O优化。

 |
|Priority|Integer|2|排序优先级。

 |
|RegionId|String|cn-hangzhou|实例所在的地域ID。

 |
|Scene|String|CREATE|在哪种场景下推荐实例规格。

 |
|SpotStrategy|String|NoSpot|抢占式实例的竞价策略。

 |
|Zones| | |实例规格所在的可用区集合。

 |
|zone| | |实例规格所在的可用区集合。

 |
|NetworkTypes| |vpc|实例规格的网络类型集合。

 |
|NetworkType| | |实例规格的网络类型集合。

 |
|ZoneNo|String|cn-hangzhou-f|实例规格所在的可用区名称。

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http://ecs.aliyuncs.com/?Action=DescribeRecommendInstanceType
&NetworkType=vpc
&RegionId=us-west-1
&InstanceType=ecs.s1.large
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRecommendInstanceTypeResponse>
     <Data>
             <InstanceChargeType>PostPaid</InstanceChargeType>
             <InstanceType>
                  <Cores>2</Cores>
                  <Generation>ecs-2</Generation>
                  <InsanceType>ecs.sn1.medium</InsanceType>
                  <InstanceTypeFamily>ecs.sn1</InstanceTypeFamily>
                  <Memory>4096</Memory>
                  <SupportIoOptimized>optimized</SupportIoOptimized>
             </InstanceType>
             <Priority>1</Priority>
             <RegionId>cn-hangzhou</RegionId>
             <Scene>CREATE</Scene>
             <SpotStrategy>SpotWithPriceLimit</SpotStrategy>
             <Zones>
                     <NetworkTypes>vpc</NetworkTypes>
                     <ZoneNo>cn-hangzhou-f</ZoneNo>
             </Zones>
     </Data>
     <Data>
             <InstanceChargeType>PostPaid</InstanceChargeType>
             <InstanceType>
                  <Cores>2</Cores>
                  <Generation>ecs-3</Generation>
                  <InsanceType>ecs.sn1ne.large</InsanceType>
                  <InstanceTypeFamily>ecs.sn1ne</InstanceTypeFamily>
                  <Memory>4096</Memory>
                  <SupportIoOptimized>optimized</SupportIoOptimized>
             </InstanceType>
             <Priority>2</Priority>
             <RegionId>cn-hangzhou</RegionId>
             <Scene>CREATE</Scene>
             <SpotStrategy>SpotWithPriceLimit</SpotStrategy>
             <Zones>
                     <NetworkTypes>vpc</NetworkTypes>
                     <ZoneNo>cn-hangzhou-f</ZoneNo>
             </Zones>
     </Data>
     <Data>
             <InstanceChargeType>PostPaid</InstanceChargeType>
             <InstanceType>
                  <Cores>2</Cores>
                  <Generation>ecs-4</Generation>
                  <InsanceType>ecs.hfc5.large</InsanceType>
                  <InstanceTypeFamily>ecs.hfc5</InstanceTypeFamily>
                  <Memory>4096</Memory>
                  <SupportIoOptimized>optimized</SupportIoOptimized>
             </InstanceType>
             <Priority>3</Priority>
             <RegionId>cn-hangzhou</RegionId>
             <Scene>CREATE</Scene>
             <SpotStrategy>SpotWithPriceLimit</SpotStrategy>
             <Zones>
                     <NetworkTypes>vpc</NetworkTypes>
                     <ZoneNo>cn-hangzhou-f</ZoneNo>
             </Zones>
     </Data>
     <Data>
             <RegionId>cn-hangzhou</RegionId>
             <InstanceChargeType>PostPaid</InstanceChargeType>
             <InstanceType>
                  <Cores>2</Cores>
                  <Generation>ecs-2</Generation>
                  <InsanceType>ecs.n1.medium</InsanceType>
                  <InstanceTypeFamily>ecs.n1</InstanceTypeFamily>
                  <Memory>4096</Memory>
                  <SupportIoOptimized>optimized</SupportIoOptimized>
             </InstanceType>
             <Priority>4</Priority>
             <RegionId>cn-hangzhou</RegionId>
             <Scene>CREATE</Scene>
             <SpotStrategy>SpotWithPriceLimit</SpotStrategy>
             <Zones>
                     <NetworkTypes>vpc</NetworkTypes>
                     <ZoneNo>cn-hangzhou-f</ZoneNo>
             </Zones>
     </Data>
     <RequestId>D6AA691D-1250-43E0-9FEC-F18001F034B3</RequestId>
</DescribeRecommendInstanceTypeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":[
		{
			"RegionId":"cn-hangzhou",
			"Scene":"CREATE",
			"InstanceChargeType":"PostPaid",
			"Zones":[
				{
					"ZoneNo":"cn-hangzhou-f",
					"NetworkTypes":[
						"vpc"
					]
				}
			],
			"SpotStrategy":"SpotWithPriceLimit",
			"Priority":1,
			"InstanceType":{
				"Memory":4096,
				"InstanceTypeFamily":"ecs.sn1",
				"Cores":2,
				"SupportIoOptimized":"optimized",
				"Generation":"ecs-2",
				"InsanceType":"ecs.sn1.medium"
			}
		},
		{
			"RegionId":"cn-hangzhou",
			"Scene":"CREATE",
			"InstanceChargeType":"PostPaid",
			"Zones":[
				{
					"ZoneNo":"cn-hangzhou-f",
					"NetworkTypes":[
						"vpc"
					]
				}
			],
			"SpotStrategy":"SpotWithPriceLimit",
			"Priority":2,
			"InstanceType":{
				"Memory":4096,
				"InstanceTypeFamily":"ecs.sn1ne",
				"Cores":2,
				"SupportIoOptimized":"optimized",
				"Generation":"ecs-3",
				"InsanceType":"ecs.sn1ne.large"
			}
		},
		{
			"RegionId":"cn-hangzhou",
			"Scene":"CREATE",
			"InstanceChargeType":"PostPaid",
			"Zones":[
				{
					"ZoneNo":"cn-hangzhou-f",
					"NetworkTypes":[
						"vpc"
					]
				}
			],
			"SpotStrategy":"SpotWithPriceLimit",
			"Priority":3,
			"InstanceType":{
				"Memory":4096,
				"InstanceTypeFamily":"ecs.hfc5",
				"Cores":2,
				"SupportIoOptimized":"optimized",
				"Generation":"ecs-4",
				"InsanceType":"ecs.hfc5.large"
			}
		},
		{
			"RegionId":"cn-hangzhou",
			"Scene":"CREATE",
			"InstanceChargeType":"PostPaid",
			"Zones":[
				{
					"ZoneNo":"cn-hangzhou-f",
					"NetworkTypes":[
						"vpc"
					]
				}
			],
			"SpotStrategy":"SpotWithPriceLimit",
			"Priority":4,
			"InstanceType":{
				"Memory":4096,
				"InstanceTypeFamily":"ecs.n1",
				"Cores":2,
				"SupportIoOptimized":"optimized",
				"Generation":"ecs-2",
				"InsanceType":"ecs.n1.medium"
			}
		}
	],
	"RequestId":"D6AA691D-1250-43E0-9FEC-F18001F034B3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidNetworkType.ValueNotSupported|The specified parameter NetworkType is not valid.|指定的网络类型不合法|
|400|InvalidPriorityStrategy.ValueNotSupported|The specified PriorityStrategy is not supported.|指定的排序策略不支持|
|400|InvalidRegionId.MalFormed|The specified parameter RegionId is not valid.|指定的 RegionId 不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

