# DescribeAvailableResource {#DescribeAvailableResource .reference}

This method retrieves a list of the resources available in a certain zone. For example, you can retrieve the resource list in a zone before creating an ECS instance in the zone.

## Description {#section_av1_byg_ydb .section}

When you call this interface, consider the following:

-   If you do not specify the `ZondId`parameter, the system returns resources that match the other criteria in all zones in the \(`RegionId`\) region.
-   You can specify the `DestinationResource` parameter to retrieve different types of resource lists, and specify other parameters to refine your search. Options for the `DestinationResource` parameter have dependencies. When you select an option, the options to the left of the option in the chain are also required.
    -   Sequence: \(`Zone`\) \> `IoOptimized` \> `InstanceType` \> `SystemDisk` \> `DataDisk`
    -   **Samples of parameter values in the sequence**:
        -   If you set `DestinationResource` to `SystemDisk`, you must specify the `IoOptimized` and  `InstanceType`.
        -   If you set `DestinationResource` to `InstanceType`, you must specify the `IoOptimized`.
        -   If you set `DestinationResource` to `DataDisk`, you must specify the `IoOptimized`, `InstanceType`, and `SystemDiskCategory`.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeAvailableResource.|
|RegionId|String|Yes|ID of the target region. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|DestinationResource|String|Yes|Resource type to query.  Optional values:-   Zone: Zone
-   IoOptimized: Whether the instance is I/O optimized or not.
-   InstanceType: Instance type.
-   SystemDisk: System disk of an instance.
-   DataDisk: Data disk of an instance.
-   Network: Network type of an instance.

|
|ZoneId|String|No| Zone ID. If you do not specify ZoneId, the system returns resources that match the other criteria in all zones in the current region.|
|InstanceChargeType|String|No|Billing method of resources. For more information, see [pricing overview](../../../../intl.en-US/Pricing/Pricing overview.md#). Optional values:-   PrePaid: Subscription
-   PostPaid: Pay-As-You-Go

Default value: PostPaid.|
|SpotStrategy|String|No|Specifies whether a Pay-As-You-Go instance is a spot instance or not. Optional values:-   NoSpot: The instance is not a spot instance.
-   SpotWithPriceLimit: The instance is a spot instance and spot priced.
-   SpotAsPriceGo: The instance is a spot instance and market priced.

Default: NoSpot.  If SpotStrategy is specified, the `SpotStrategy` must be set to PostPaid.|
|IoOptimized|String|No|Specifies whether the instance is an I/O optimized instance. Optional values:-   none: Non-I/O optimized instance.
-   optimized: I/O optimized instance.

If you set `DestinationResource` to  `InstanceType`, `SystemDisk`, or `DataDisk`, you must specify `IoOptimized`. .|
|InstanceType|String|No|Instance type. For more information, see [Instance generations and type families](../../../../intl.en-US/Product Introduction/Instance type families.md#), or call [DescribeInstanceTypes](intl.en-US/API Reference/Instances/DescribeInstanceTypes.md#) to obtain the latest type list. If you set  `DestinationResource` to `SystemDisk` or `DataDisk`, you must specify the `InstanceType`.|
|SystemDiskCategory|String|No|System disk category. Optional values:-   cloud: Basic cloud disk
-   cloud\_efficiency: Ultra SSD disk
-   cloud\_ssd: Cloud SSD
-   ephemeral\_ssd: Ephemeral SSD

|
|DataDiskCategory|String|No|Data disk category. Optional values:-   cloud: Basic cloud disk
-   cloud\_efficiency: Ultra SSD disk
-   cloud\_ssd: Cloud SSD
-   ephemeral\_ssd: Ephemeral SSD

|
|NetworkCategory|String|No|Network type of an ECS instance. Optional values:-   Vpc: Virtual Private Cloud
-   Classic: Classic network

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|AvailableZones|Array of [AvailableZone](#AvailableZoneType)|A collection of zone types|

**AvailableZoneType**

|Name|Type|Description|
|:---|:---|:----------|
|RegionId|String|Region ID.|
|ZoneId|String|Zone ID.|
|Status|String|Resource status. Optional values:-   Available: Resources are available.
-   SoldOut: Resources are unavailable.

|
|AvailableResources|Array of [AvailableResources](#AvailableResourcesType)|A collection of available resource types.|

**AvailableResourcesType**

|Name|Type|Description|
|:---|:---|:----------|
|Type|String|Resource type. Optional values:-   Zone: Zone
-   IoOptimized: Whether the instance is I/O optimized or not.
-   InstanceType: Instance type.
-   SystemDisk: System disk.
-   DataDisk: Data disk.
-   Network: Network type of an instance.

|
|SupportedResources|Array of [\\SupportedResources](#SupportedResourcesType)|A collection of supported available resource types.|

**SupportedResourcesType**

|Name|Type|Description|
|:---|:---|:----------|
|Value|String|Name of the Resource.|
|Status|String|Resource status. Optional values:-   Available: Resources are available.
-   SoldOut: Resources are unavailable.

|
|Min|Integer|Minimum limit of a resource type. No value is returned if the parameter is null.|
|Max|Integer|Maximum limit of a resource type. No value is returned if the parameter is null.|
|Unit|Integer|Resource type unit. No value is returned if the parameter is null.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeAvailableResource
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeAvailableResourceResponse>
    <AvailableZones>
        <AvailableZone>
            <ZoneId>cn-hangzhou-d</ZoneId>
            <RegionId>cn-hangzhou</RegionId>
            <Status>Available</Status>
            <AvailableResources>
                <AvailableResource>
                    <Type>instanceType</Type>
                    <SupportedResources>
                        <SupportedResource>
                            <Value>ecs.d1ne.xlarge</Value>
                            <Status>Available</Status>
                        </SupportedResource>
                        <SupportedResource>
                            <Value>ecs.d1ne. 2xlarge</Value>
                            <Status>Available</Status>
                        </SupportedResource>
                    </SupportedResources>
                </AvailableResource>
            </AvailableResources>
        </AvailableZone>
        <AvailableZone>
            <ZoneId>cn-hangzhou-e</ZoneId>
            <RegionId>cn-hangzhou</RegionId>
            <Status>Available</Status>
            <AvailableResources>
                <AvailableResource>
                    <Type>instanceType</Type>
                    <SupportedResources>
                        <SupportedResource>
                            <Value>ecs.d1ne.xlarge</Value>
                            <Status>Available</Status>
                        </SupportedResource>
                         <SupportedResource>
                            <Value>ecs.d1ne. 2xlarge</Value>
                            <Status>Available</Status>
                        </SupportedResource>
                    </SupportedResources>
                </AvailableResource>
            </AvailableResources>
        </AvailableZone>
    </AvailableZones>
    <RequestId>6DB97BCC-92BA-424D-A7C8-3F6486612BAE</RequestId>
</DescribeAvailableResourceResponse>
```

 **JSON format** 

```
{
    "RequestId": "D0233A65-7F00-4B50-8023-101427229D4F",
    "AvailableZones": {
        "AvailableZone": [
            {
                "Status": "available",
                "RegionId": "cn-hangzhou",
                "AvailableResources": {
                    "AvailableResource": [
                        {
                            "Type": "instanceType",
                            "SupportedResources": {
                                "SupportedResource": [
                                    {
                                        "Status": "available",
                                        "Value": "ecs.sn1ne.xlarge"
                                    },
                                    {
                                        "Status": "available",
                                        "Value": "ecs.sn2ne.xlarge"
                                    }
                                ]
                            }
                        }
                    ]
                },
                "ZoneId": "cn-hangzhou-e",
            }
        ]
    }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|Invalid.Param|The input parameter DestinationResource that is mandatory for processing this request is not supplied.|400|You must specify the `DestinationResource`.|
|Invalid.InstanceChargeType|The specified InstanceChargeType is not valid.|400|The specified  `InstanceChargeType` does not exist.|
|Invalid.IoOptimized|The specified IoOptimized is not valid.|404| The specified parameter `IoOptimized` is invalid.|
|Invalid.NetworkCategory|The specified NetworkCategory is not valid.|404|The specified NetworkCategory is invalid.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|Unavailable.Regions|The available regions does not exists.|404|You are not allowed to access the specified `RegionId`.|

