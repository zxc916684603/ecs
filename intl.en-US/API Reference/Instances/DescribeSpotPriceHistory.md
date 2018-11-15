# DescribeSpotPriceHistory {#DescribeSpotPriceHistory .reference}

Queries the price history of ECS preemptible instances. The specified parameter EndTime minus StartTime must be less than or equal to 30.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSpotPriceHistory.|
|RegionId|String|Yes|The region ID of the instance. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ZoneId|String|Yes|Zone ID.|
|NetworkType| String|Yes|Network type of the bid instance. Optional values:-   classic: The preemptible instance is classic network-connected.
-   vpc: The preemptible instance is VPC-Connected.

|
|InstanceType|String|Yes|Instance type.|
|IoOptimized|String|No|Whether it is an I/O-optimized instance. Value range:-   optimized: The preemptible instance is I/O optimized.
-   none: indicates that the bid instance is not an I/O optimization instance

The default value of Series I instance types is none.

The default value of other instance types is optimized.

|
|StartTime|String|No|Query the start time of the historical price of the bid instance. The StartTime is based on [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) with a format of YYYY-MM-DDTHH:mm:ssZ. The default value is null, and null indicates three days earlier before the EndTime. The maximum value of StartTime cannot be 30 days earlier than the specified EndTime.|
|EndTime|String|No|Queries the end time of the price record of the preemptible instance. The EndTime is based on ISO8601 with a format of YYYY-MM-DDTHH:MM:SSZ, and the UTC time is required.It is null by default, and null indicates the current time.

|
|Offset|Integer|No|Queries the start line.Default: 0.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|NextOffset|Integer|The start line of the next page. Queries data for the next page. The specified value of the parameter Offset is the value.|
|SpotPrices |[SpotPriceType ](intl.en-US/API Reference/Data type/SpotPriceType.md#)|The price information of the preemptible instance.|

## Example  { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSpotHistory
&RegionId=cn-hangzhou
&ZoneId=cn-hanghzhou-c
&NetworkType=vpc
&InstanceType=ecs.t1.xsmall
&IoOptimized=none
&UtcStartTime=2017-08-22T08:45:08Z...
&<Common Request Parameters>
```

**Response example**

**XML format**

```
<DescribeSpotPriceHistoryResponse>
    <RequestId>xxxxxxxxxxxxxx</RequestId>
    <NextOffset>1000</NextOffset>
    <SpotPrices>
        <SpotPriceType>
            <IoOptimized>none</IoOptimized>
            <OriginPrice>0.028</OriginPrice>
            <NetworkType>classic</NetworkType>
            <Timestamp>2017-09-18T11:00:00Z</Timestamp>
            <ZoneId>cn-hangzhou-c</ZoneId>
            <SpotPrice>0.006</SpotPrice>
            <InstanceType>ecs.t1.xsmall</InstanceType>
        </SpotPriceType>
        <SpotPriceType>
            <IoOptimized>none</IoOptimized>
            <OriginPrice>0.028</OriginPrice>
            <NetworkType>classic</NetworkType>
            <Timestamp>2017-09-18T12:00:00Z</Timestamp>
            <ZoneId>cn-hangzhou-c</ZoneId>
            <SpotPrice>0.006</SpotPrice>
            <InstanceType>ecs.t1.xsmall</InstanceType>
    </SpotPriceType>
</SpotPrices>
</DescribeSpotPriceHistoryResponse>
```

 **JSON format** 

```
{
    "RequestId":"xxxxxxxxxxxxxx",
    "NextOffset":1000,
    "SpotPrices":
    {
        "SpotPriceType":[
        {
            "IoOptimized":"none",
            "OriginPrice":0.028,
            "NetworkType":"classic",
            "Timestamp":"2017-09-18T11:00:00Z",
            "ZoneId":"cn-hangzhou-c","SpotPrice":0.006,
            "InstanceType":"ecs.t1.xsmall"
            }
        ]
    }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidParams.EndTime|The format of the specified parameter EndTime is invalid.|400|The format of `EndTime` must abide by ISO8601.|
|InvalidParams.InstanceType| The specified parameter InstanceType is required.|400|You must specify the value of the parameter `InstanceType`.|
|InvalidParams.IoOptimized|The value of specified parameter IoOptimized is invalid.|400| The value of `IoOptimized` is invalid.|
|InvalidParams.NetworkType| The value of specified parameter NetworkType is invalid.|400|The value of `NetworkType` is invalid.|
|InvalidParams.RegionId|The specified parameter RegionId is required.|400|You must specify the value of the parameter `RegionId`.|
|InvalidParams.StartTime|The format of the specified parameter startup is invalid.|400|The format of `StartTime` must abide by ISO8601.|
|InvalidParams.ZoneId|The specified parameter ZoneId is required.|400|You must specify the value of the parameter `ZoneId`.|

