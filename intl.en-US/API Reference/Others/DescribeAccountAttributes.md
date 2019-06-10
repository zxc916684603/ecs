# DescribeAccountAttributes {#doc_api_1006119 .reference}

Queries the upper limit of ECS resources that you can create in a region. You can call this operation to query the numbers of security groups, ENIs, Pay-As-You-Go vCPU cores, preemptible instance vCPU cores, and dedicated hosts. You can also obtain the information such as the local network type and whether an account has passed real name authentication.

## Description {#description .section}

After [registering](https://account.alibabacloud.com/register/intl_register.htm) for an Alibaba Cloud account, you can create a certain number of ECS resources in different regions. For more information, see [Limits](~~25412~~).

You can also [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to raise the resource usage limit.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeAccountAttributes) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The ID of the region. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|Action|String|No|DescribeAccountAttributes| The operation that you want to perform. Set the value to DescribeAccountAttributes.

 |
|AttributeName.N|RepeatList|No|max-security-groups| The types of resources. Valid values of N: 1 to 8. Valid values:

 -   instance-network-type: available network types in the current region
-   max-security-groups: the number of security groups
-   max-elastic-network-interfaces: the number of ENIs in the current region
-   max-postpaid-instance-vcpu-count: the number of Pay-As-You-Go instance vCPU cores in the current region
-   max-spot-instance-vcpu-count: the number of preemptible instance vCPU cores in the current region
-   max-delicated-hosts: the number of dedicated hosts in the current region
-   supported-postpaid-instance-types: Pay-As-You-Go I/O optimization instance types in the current region
-   real-name-authentication: Whether the account has passed real name authentication.

**Note:** Complete the real-name authentication before creating ECS instances.


 Default value: null.

 |
|ZoneId|String|No|cn-hangzhou-b| The ID of the zone.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|AccountAttributeItems| | | A collection of information about account privileges in a specified region.

 |
|└AttributeName|String|max-security-groups| The types of resources. Valid values:

 -   instance-network-type: available network types in the current region
-   max-security-groups: the number of security groups
-   max-elastic-network-interfaces: the number of ENIs in the current region
-   max-postpaid-instance-vcpu-count: the number of Pay-As-You-Go instance vCPU cores in the current region
-   max-spot-instance-vcpu-count: the number of preemptive instance vCPU cores in the current region
-   max-delicated-hosts: the number of dedicated hosts in the current region
-   supported-postpay-instance-types: the Pay-As-You-Go I/O optimization instance types in the current region
-   real-name-authentication: Whether the account has passed real name authentication.

 |
|└AttributeValues| | | The value of the resource usage.

 |
|└Count|Integer|3| The number of resource types.

 |
|└InstanceChargeType|String|PrePaid| The billing method.

 |
|└InstanceType|String|\["ecs.g5.large"\]| The type of the instance.

 |
|└Value|String|800| |
|└ZoneId|String|cn-hangzhou-b| The ID of the zone.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeAccountAttributes
&RegionId=cn-hangzhou 
&ZoneId=cn-hangzhou-b
&AttributeName. 1=max-security-groups
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeAccountAttributesResponse> 
    <AccountAttributeItems> 
        <AccountAttributeItem> 
            <AttributeName>max-security-groups</AttributeName> 
            <AttributeValues> 
                <ValueItem> 
                    <Value>800</Value>
                <ValueItem> 
            </AttributeValues> 
        </AccountAttributeItem> 
          <AccountAttributeItem> 
            <AttributeName>instance-network-type</AttributeName> 
            <AttributeValues> 
                <ValueItem> 
                    <Value>vpc</Value>
                    <Value>classic</Value>
                <ValueItem> 
            </AttributeValues> 
        </AccountAttributeItem> 
     </AccountAttributeItems> 
    <RequestId>675B6D89-A3EB-4987-BAF3-610591E0D019</RequestId> 
</DescribeAccountAttributesResponse> 
```

`JSON` format

``` {#json_return_success_demo}
{
	"AccountAttributeItems":{
		"AccountAttributeItem":[
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"100"
						}
					]
				},
				"AttributeName":"max-security-groups"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"2"
						}
					]
				},
				"AttributeName":"max-dedicated-hosts"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"1000"
						}
					]
				},
				"AttributeName":"max-postpaid-instance-vcpu-count"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"1000"
						}
					]
				},
				"AttributeName":"max-spot-instance-vcpu-count"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"5000"
						}
					]
				},
				"AttributeName":"max-elastic-network-interfaces"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"yes"
						}
					]
				},
				"AttributeName":"real-name-authentication"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"vpc"
						}
					]
				},
				"AttributeName":"instance-network-type"
			},
			{
				"AttributeValues":{
					"ValueItem":[
						{
							"Value":"ecs.f3-c16f1.4xlarge"
						},
						{
							"Value":"ecs.g5.2xlarge"
						}
					]
				},
				"AttributeName":"supported-postpaid-instance-types"
			}
		]
	},
	"RequestId":"8CE45CD5-31FB-47C2-959D-CA8144CE9F42"
}
```

## Error codes {#section_cbs_nmh_iac .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Invalid.Parameter|The required parameter regionId must be not null.|The error message returned when the required parameter is not specified.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

