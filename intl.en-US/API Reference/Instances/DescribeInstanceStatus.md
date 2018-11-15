# DescribeInstanceStatus {#DescribeInstanceStatus .reference}

Obtains the list of all your instances in batches with status information.

## Description {#section_yfq_yps_xdb .section}

-   See [Instance status table](intl.en-US/API Reference/Appendix/Instance status table.md#) for the possibly queried instance status.
-   You can use this API to get a list of instances.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|Operation interface name, required parameter. Value: DescribeInstanceStatus.|
|RegionId|String|Yes|The Region ID of instance. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ZoneId|String|No|ID of the zone to which an instance belongs.|
|PageNumber|Integer|No|Page number of the instance status list. The start value is 1.The default value is 1.

|
|PageSize|Integer|No|Sets the number of lines per page for queries per page. The maximum value is 50.The default value is 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of instances.|
|PageNumber|Integer|The page number of the instance list.|
|PageSize|Integer|The number of lines per page set during input.|
|InstanceStatuses|Array|An array format composed of InstanceStatusItemType. It returns the status information of an instance.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceStatus
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
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
                <InstanceId>i-ae4r89pp</InstanceId>
                <Status>Stopped</Status>
        </InstanceStatus>
    </InstanceStatuses>
</DescribeInstanceStatusResponse>
```

 **JSON format** 

```

"RequestId": "6EF60BEC-0242-43AF-BB20-270359FB54A7",
"TotalCount": 2,
"Pagenumber": 1,
"PageSize": 10,
"InstanceStatuses": {
    "InstanceStatus": [{
        "InstanceId": "i-instance1",
            "Status": "Running"
        
        
            "InstanceId": "i-ae4r89pp",
            "Status": "Stopped"
        
    }

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Description|
|:---------|:-------------|:---------------|:----------|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|RegionId value missing.|
|InvalidZoneId.NotFound|The ZoneId provided does not exist in our records.|404|ZoneId value missing.|

