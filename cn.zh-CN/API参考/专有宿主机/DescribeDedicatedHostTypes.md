# DescribeDedicatedHostTypes {#doc_api_Ecs_DescribeDedicatedHostTypes .reference}

调用DescribeDedicatedHostTypes查询指定地域下支持的专有宿主机规格详细参数，或者查询专有宿主机支持的ECS实例规格族。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeDedicatedHostTypes&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|专有宿主机所在地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeDedicatedHostTypes|系统规定参数。取值：DescribeDedicatedHostTypes

 |
|DedicatedHostType|String|否|ddh.sn1ne|专有宿主机规格。更多详情，请参见[宿主机规格](~~68564~~)。

 |
|SupportedInstanceTypeFamily|String|否|ecs.sn1ne|专有宿主机规格支持的ECS实例规格族。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DedicatedHostTypes| | |返回专有宿主机规格的信息。

 |
|Cores|Integer|2|单个物理CPU的核数。

 |
|DedicatedHostType|String|ddh.sn1ne|专有宿主机规格类型。如果您需要使用更多专有宿主机规格，可以提交工单联系阿里云。

 |
|LocalStorageAmount|Integer|0|专有宿主机上的本地盘数量。

 |
|LocalStorageCapacity|Long|0|一块本地盘容量，单位：GiB。

 |
|LocalStorageCategory|String|local|本地盘类型。

 |
|MemorySize|Float|112.0|内存容量，单位：GiB。

 |
|SupportedInstanceTypeFamilies| |ecs.sn1ne|专有宿主机规格支持的ECS实例的规格族。

 |
|SupportedInstanceTypesList| |ecs.sn1ne|专有宿主机规格支持的ECS实例规格族。

 |
|TotalVcpus|Integer|56|虚拟CPU总核数。

 |
|RequestId|String|5FE5FF06-3A33-4658-8495-6445FC54E327|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DescribeDedicatedHostTypes
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDedicatedHostTypesResponse>
    <DedicatedHostTypes>
        <DedicatedHostType>
            <LocalStorageAmount>0</LocalStorageAmount>
            <Sockets>2</Sockets>
            <DedicatedHostType>ddh.sn1ne</DedicatedHostType>
            <LocalStorageCapacity>0</LocalStorageCapacity>
            <SupportedInstanceTypeFamilies>
                <SupportedInstanceTypeFamily>ecs.sn1ne</SupportedInstanceTypeFamily>
            </SupportedInstanceTypeFamilies>
            <MemorySize>112.0</MemorySize>
            <Cores>32</Cores>
            <TotalVcpus>56</TotalVcpus>
            <LocalStorageCategory></LocalStorageCategory>
        </DedicatedHostType>
        <DedicatedHostType>
            <LocalStorageAmount>0</LocalStorageAmount>
            <Sockets>2</Sockets>
            <DedicatedHostType>ddh.sn2ne</DedicatedHostType>
            <LocalStorageCapacity>0</LocalStorageCapacity>
            <SupportedInstanceTypeFamilies>
                <SupportedInstanceTypeFamily>ecs.sn2ne</SupportedInstanceTypeFamily>
            </SupportedInstanceTypeFamilies>
            <MemorySize>224.0</MemorySize>
            <Cores>32</Cores>
            <TotalVcpus>56</TotalVcpus>
            <LocalStorageCategory></LocalStorageCategory>
        </DedicatedHostType>
    </DedicatedHostTypes>
    <RequestId>5FE5FF06-3A33-4658-8495-6445FC54E327</RequestId>
</DescribeDedicatedHostTypesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DedicatedHostTypes":{
		"DedicatedHostType":[
			{
				"LocalStorageAmount":0,
				"Sockets":2,
				"Cores":32,
				"DedicatedHostType":"ddh.sn1ne",
				"LocalStorageCapacity":0,
				"MemorySize":112,
				"TotalVcpus":56,
				"SupportedInstanceTypeFamilies":{
					"SupportedInstanceTypeFamily":[
						"ecs.sn1ne"
					]
				},
				"LocalStorageCategory":""
			},
			{
				"LocalStorageAmount":0,
				"Sockets":2,
				"Cores":32,
				"DedicatedHostType":"dh.c60m83.n1",
				"LocalStorageCapacity":0,
				"MemorySize":84,
				"TotalVcpus":40,
				"SupportedInstanceTypeFamilies":{
					"SupportedInstanceTypeFamily":[
						"ecs.n1"
					]
				},
				"LocalStorageCategory":""
			}
		]
	},
	"RequestId":"9A0FE8A2-720C-45AE-B2D9-813060FCBBF5"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

