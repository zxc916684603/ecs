# DescribeAvailableResource {#doc_api_1105040 .reference}

Views the resources available in a zone. For example, you can view the resource list before creating an ECS instance \(RunInstances\) in a zone.

## Description {#description .section}

When you call this operation, note that:

-   When the ZoneId parameter is not specified, the system returns resources that match the other criteria of all zones within the region.
-   You can specify the DestinationResource parameter to retrieve different types of resources, and specify other parameters to refine your search. Options for the DestinationResource parameter have dependencies. When you select an option, the options to the left of the option in the chain are also required.
    -   Sequence: \(Zone\) \> IoOptimized \> InstanceType \> SystemDisk \> DataDisk
    -   Samples of parameter values in the sequence:
        -   If you set the DestinationResource parameter to SystemDisk, you must specify the IoOptimized and InstanceType parameters.
        -   If you set the DestinationResource parameter to InstanceType, you must specify the IoOptimized parameter.
        -   If you set the DestinationResource parameter to DataDisk, you must specify the IoOptimized, InstanceType, and SystemDiskCategory parameters.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeAvailableResource) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|DestinationResource|String|Yes|InstanceType| The resource types to query. Valid values:

 -   Zone
-   IoOptimized
-   InstanceType
-   SystemDisk
-   DataDisk
-   Network

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the target region. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|Action|String|No|DescribeAvailableResource| The operation that you want to perform. Set the value to DescribeAvailableResource.

 |
|Cores|Integer|No|2| The number of vCPU cores of the instance type. For more information, see [Instance type families](~~25378~~). The Cores parameter is valid only when the DestinationResource parameter is set to InstanceType.

 |
|DataDiskCategory|String|No|cloud\_ssd| The category of the data disk. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: SSD
-   ephemeral\_ssd: local SSD

 |
|DedicatedHostId|String|No|dh-dedicatedhostid| The ID of the DDH.

 |
|InstanceChargeType|String|No|PrePaid| The billing method of resources. For more information, see Pricing overview. Valid values:

 -   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go

 Default value: PostPaid.

 |
|InstanceType|String|No|ecs.g5.large| The type of the instance. For more information, see [Instance type families](~~25378~~), or call [DescribeInstanceTypes](~~25620~~) to query the latest instance types. When the DestinationResource parameter is set to SystemDisk or DataDisk, you must specify the InstanceType parameter as well.

 |
|IoOptimized|String|No|optimized| Indicates whether the instance is I/O optimized. Valid values:

 -   none
-   optimized

 When the DestinationResource parameter is set to InstanceType, SystemDisk, or DataDisk, you must specify the IoOptimized parameter as well.

 |
|Memory|Float|No|8.0| The memory size of the instance type. Unit: GiB. For more information, see [Instance type families](~~25378~~). The Memory parameter is valid only when the DestinationResource parameter is set to InstanceType.

 |
|NetworkCategory|String|No|vpc| The type of the network. Valid values:

 -   vpc
-   classic

 |
|ResourceType|String|No|Instance| The type of the resource.

 |
|SpotStrategy|String|No|NoSpot| The bidding policy for the Pay-As-You-Go instance. Valid values:

 -   NoSpot: a normal Pay-As-You-Go instance
-   SpotWithPriceLimit: a preemptible instance with a maximum hourly price
-   SpotAsPriceGo: an instance that is billed based on the market price. The maximum price of this instance is the price of a Pay-As-You-Go instance.

 Default value: NoSpot. The SpotStrategy parameter is valid only when the InstanceChargeType parameter is set to PostPaid.

 |
|SystemDiskCategory|String|No|cloud\_ssd| The category of the system disk. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: SSD
-   ephemeral\_ssd: local SSD

 |
|ZoneId|String|No|cn-hangzhou-e| The ID of the zone. When the ZoneId parameter is not specified, the system returns resources that match the other criteria of all zones within the region.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|AvailableZones| | | An array of zone types.

 |
|└AvailableResources| | | An array of available resource types.

 |
|└SupportedResources| | | An array of supported resource types.

 |
|└Max|Integer|2| The maximum value of a resource type. No value is returned when this parameter is null.

 |
|└Min|Integer|1| The minimum value of a resource type. No value is returned when the parameter is null.

 |
|└Status|String|Available| The type of the resource. Valid values:

 -   Available
-   SoldOut

 |
|└StatusCategory|String|WithStock| The resource category based on the stock. Valid values:

 -   WithStock: sufficient stock
-   ClosedWithStock: insufficient stock
-   WithoutStock: running out of stock

 |
|└Unit|String|null| The unit of the resource type. No value is returned when the parameter is null.

 |
|└Value|String|ecs.d1ne.xlarge| The value of the resource.

 |
|└Type|String|InstanceType| The type of the resource. Valid values:

 -   Zone
-   IoOptimized
-   InstanceType
-   SystemDisk
-   DataDisk
-   Network

 |
|└RegionId|String|cn-hangzhou| The ID of the region.

 |
|└Status|String|Available| The type of the resource. Valid values:

 -   Available
-   SoldOut

 |
|└StatusCategory|String|WithStock| The resource category based on the stock. Valid values:

 -   WithStock: sufficient stock
-   ClosedWithStock: insufficient stock
-   WithoutStock: running out of stock

 |
|└ZoneId|String|cn-hangzhou-e| The ID of the zone.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeAvailableResource
&DestinationResource=InstanceType 
&RegionId=cn-hangzhou
&InstanceChargeType=PrePaid 
&SpotStrategy=NoSpot 
&ZoneId=cn-hangzhou-e
&IoOptimized=optimized 
&DedicatedHostId=dh-dedicatedhostid 
&InstanceType=["ecs.g5.large"] 
&SystemDiskCategory=cloud_ssd 
&DataDiskCategory=cloud_ssd 
&NetworkCategory=vpc 
&Cores=2 
&Memory=8.0
&ResourceType=Instance 
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeAvailableResourceResponse> 
  <RequestId>5272B7D8-F366-4781-AF7B-63E735FBC09A</RequestId> 
  <AvailableZones> 
    <AvailableZone> 
      <Status>Available</Status>
      <RegionId>cn-hangzhou</RegionId>
      <ZoneId>cn-hangzhou-h</ZoneId> 
    </AvailableZone> 
    <AvailableZone> 
      <Status>Available</Status>
      <RegionId>cn-hangzhou</RegionId>
      <ZoneId>cn-hangzhou-g</ZoneId>
    </AvailableZone> 
    <AvailableZone> 
      <Status>Available</Status>
      <RegionId>cn-hangzhou</RegionId> 
      <ZoneId>cn-hangzhou-f</ZoneId> 
    </AvailableZone>
    <AvailableZone> 
      <Status>Available</Status>
      <RegionId>cn-hangzhou</RegionId>
      <ZoneId>cn-hangzhou-b</ZoneId> 
    </AvailableZone> 
    <AvailableZone> 
      <Status>Available</Status>
      <RegionId>cn-hangzhou</RegionId>
      <ZoneId>cn-hangzhou-e</ZoneId> 
    </AvailableZone>
  </AvailableZones>
</DescribeAvailableResourceResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"5272B7D8-F366-4781-AF7B-63E735FBC09A",
	"AvailableZones":{
		"AvailableZone":[
			{
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-h"
			},
			{
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-g"
			},
			{
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-f"
			},
			{
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-b"
			},
			{
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-e"
			}
		]
	}
}
```

## Error codes {#section_jvt_32n_sga .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|Invalid.RegionId|The specified RegionId does not exist.|The error message returned when the RegionId parameter is invalid.|
|400|Invalid.InstanceChargeType|The specified InstanceChargeType is not valid.|The error message returned when the InstanceChargeType parameter is invalid.|
|400|Invalid.Param|The input parameter DestinationResource that is mandatory for processing this request is not supplied.|The error message returned when the DestinationResource parameter is invalid.|
|404|Invalid.ResourceType|The ResourceType provided does not exist in our records.|The error message returned when the ResourceType parameter is invalid.|
|404|Invalid.DestinationResource|The specified DestinationResource is not valid.|The error message returned when the DestinationResource parameter is invalid.|
|404|Invalid.IoOptimized|The specified IoOptimized is not valid.|The error message returned when the IoOptimized parameter is invalid.|
|404|Invalid.NetworkCategory|The specified NetworkCategory is not valid.|The error message returned when the NetworkCategory parameter is invalid.|
|404|Invalid.SpotStrategy|The specified SpotStrategy is not valid.|The error message returned when the SpotStrategy parameter is invalid.|
|403|InvalidDedicatedHostId.NotFound|The specified DedicatedHostId does not exist.|The error message returned when the specified DDH ID does not exist.|
|404|Invalid.NetworkType|The specified NetworkType is not valid.|The error message returned when the NetworkType parameter is invalid.|
|404|InvalidResourceId.NotFound|The specified ResourceId is not found in our records|The error message returned when the specified ResourceId does not exist.|
|403|InvalidParam.TypeAndCpuMem.Conflict|The specified 'InstanceType' and 'Cores','Memory' are not blank at the same time.|The error message returned when the specified ResourceId does not exist.|
|403|InvalidParam.Cores|The specified parameter 'Cores' should be empty|The error message returned when the Memory parameter is invalid.|
|403|InvalidParam.Memory|The specified parameter 'Memory' should be empty|The error message returned when the resource in the current region does not exist or has been released.|
|400|InvalidRegionId.MalFormed|The specified parameter RegionId is not valid.|The error message returned when the specified RegionId parameter is invalid.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

