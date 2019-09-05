# DescribeInstanceStatus {#doc_api_Ecs_DescribeInstanceStatus .reference}

调用DescribeInstanceStatus获取一台或多台ECS实例的状态信息。

## 接口说明 {#description .section}

-   ECS实例的生命周期状态请参见[实例状态表](~~25687~~)。
-   该接口同时可用于获取实例列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeInstanceStatus&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|实例所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeInstanceStatus|系统规定参数。对于您自行拼凑HTTP/HTTPS URL发起的API请求，`Action`为必选参数。取值：DescribeInstanceStatus

 |
|ClusterId|String|否|cls-clusterid1|实例所属的集群ID。

 |
|PageNumber|Integer|否|1|实例状态列表的页码。起始值：1。

 默认值：1。

 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。取值范围：1~50

 默认值：10。

 |
|ZoneId|String|否|cn-hangzhou-d|实例所属可用区。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|InstanceStatuses| | |实例状态集类型（InstanceStatusSetType） 。

 |
|InstanceStatus| | |实例状态集类型（InstanceStatusSetType） 。

 |
|InstanceId|String|i-instance1|实例ID。

 |
|Status|String|Running|实例状态。

 |
|PageNumber|Integer|1|实例列表的页码。

 |
|PageSize|Integer|10|输入时设置的每页行数。

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |
|TotalCount|Integer|2|实例总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeInstanceStatus
&RegionId=cn-hangzhou
&ZoneId=cn-hangzhou-d
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeInstanceStatusResponse>
      <RequestId>6EF60BEC-0242-43AF-BB20-270359FB54A7</RequestId>
      <TotalCount>2</TotalCount>
      <PageNumber>1</PageNumber>
      <PageSize>10</PageSize>
      <InstanceStatuses>
            <InstanceStatus>
                  <InstanceId>i-instance1</InstanceId>
                      <Status>Running</Status>
                </InstanceStatus>
                <InstanceStatus>
                      <InstanceId>i-ae4r89**</InstanceId>
                      <Status>Stopped</Status>
            </InstanceStatus>
      </InstanceStatuses>
</DescribeInstanceStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"InstanceStatuses":{
		"InstanceStatus":[
			{
				"Status":"Running",
				"InstanceId":"i-instance1"
			},
			{
				"Status":"Stopped",
				"InstanceId":"i-ae4r89**"
			}
		]
	},
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"6EF60BEC-0242-43AF-BB20-270359FB54A7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

