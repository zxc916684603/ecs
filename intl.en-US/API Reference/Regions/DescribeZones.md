# DescribeZones {#doc_api_1006049 .reference}

Views the zones in a specified region.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeZones) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The region ID of the zone. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|Action|String|No|DescribeZones| The operation that you want to perform. Set the value to DescribeZones.

 |
|InstanceChargeType|String|No|PostPaid| The billing method supported in the zone. For more information, see [Pricing overview](~~25398~~). Valid values:

 -   PrePaid: Subscription.
-   PostPaid: Pay-As-You-Go. This is the default value.

 |
|SpotStrategy|String|No|NoSpot| The bidding policy for the Pay-As-You-Go instance. Specify this parameter when the InstanceChargeType parameter is set to PostPaid. For more information, see [Preemptible instances](~~52088~~). Valid values:

 -   NoSpot \(Default\): Pay-As-You-Go instance
-   SpotWithPriceLimit: preemptible instance with the maximum price
-   SpotAsPriceGo: price automatically provided by the system with the Pay-As-You-Go price as its maximum value

 |
|Verbose|Boolean|No|false| **Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |
|Zones| | | An array that consists of ZoneType data.

 |
|└AvailableDedicatedHostTypes| |Compute type| The types of supported dedicated hosts.

 |
|└AvailableDiskCategories| |cloud| An array of supported disk categories.

 |
|└AvailableInstanceTypes| |c5| The types of the instances that can be created.

 |
|└AvailableResourceCreation| |DedicatedHost| An array of the types of resources that can be created.

 |
|└AvailableResources| | | The resources that can be created. This parameter is an array of AvailableResourcesType data.

 |
|└DataDiskCategories| |cloud\_ssd| The category of the data disk. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: SSD
-   ephemeral\_ssd: local SSD

 |
|└InstanceGenerations| |I| The generation number of the instance type family.

 |
|└InstanceTypeFamilies| |\["d1", "d1ne"\]| A array that consists of InstanceTypeFamilyItemType data.

 |
|└InstanceTypes| |\["ecs.g5.large"\]| The type of the instance.

 |
|└IoOptimized|Boolean|true| Indicates whether the instance is I/O optimized. Valid values:

 -   none
-   optimized

 When the InstanceType parameter is [Phased-out instance type](~~55263~~), the default value is null.

 For instance types other than Generation I, the default value is optimized.

 |
|└NetworkTypes| |VPC| The type of the network. Valid values:

 -   VPC
-   Classic

 |
|└SystemDiskCategories| |cloud\_ssd| The category of the system disk. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: SSD
-   ephemeral\_ssd: local SSD

 |
|└AvailableVolumeCategories| |san\_ssd| Available shared storage category.

 |
|└DedicatedHostGenerations| |I| The generation number of dedicated hosts.

 |
|└LocalName|String|Hangzhou Zone G| The name of the zone in local language.

 |
|└ZoneId|String|cn-hangzhou-b| The ID of the zone.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeZones
&RegionId=cn-hangzhou
&InstanceChargeType=PostPaid 
&SpotStrategy=NoSpot 
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeZonesResponse>
  <Zones>
    <Zone>
      <AvailableResourceCreation> 
        <ResourceTypes>Instance</ResourceTypes>
        <ResourceTypes>Disk</ResourceTypes>
      </AvailableResourceCreation> 
      <LocalName/>
      <ZoneId>cn-hangzhou-d</ZoneId>
      <AvailableDiskCategories>
        <DiskCategories>cloud</DiskCategories>
      </AvailableDiskCategories>
    </Zone> 
    <Zone> 
      <AvailableResourceCreation>
        <ResourceTypes>Instance</ResourceTypes>
        <ResourceTypes>Disk</ResourceTypes>
      </AvailableResourceCreation>
      <LocalName/>
      <ZoneId>cn-hangzhou-b</ZoneId>
      <AvailableDiskCategories>
        <DiskCategories>cloud</DiskCategories>
      </AvailableDiskCategories>
    </Zone> 
  </Zones> 
  <RequestId>6DB97BCC-92BA-424D-A7C8-3F6486612BAE</RequestId>
</DescribeZonesResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"A347EF0E-BBCC-4EFA-BD79-27AA3ACFD1BF",
	"Zones":{
		"Zone":[
			{
				"AvailableResourceCreation":{
					"ResourceTypes":[
						"Instance",
						"Disk"
					]
				},
				"ZoneId":"cn-hangzhou-d",
				"LocalName":"",
				"AvailableDiskCategories":{
					"DiskCategories":[
						"cloud"
					]
				}
			},
			{
				"AvailableResourceCreation":{
					"ResourceTypes":[
						"Instance",
						"Disk"
					]
				},
				"ZoneId":"cn-hangzhou-b",
				"LocalName":"",
				"AvailableDiskCategories":{
					"DiskCategories":[
						"cloud"
					]
				}
			}
		]
	}
}
```

## Error codes {#section_un2_jo1_gsz .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned when the specified Region ID does not exist. Check whether the service is available in this region.|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|The error message returned when the specified instance type does not exist.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

