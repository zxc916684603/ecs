# DescribeBandwidthLimitation {#DescribeBandwidthLimitation .reference}

Describes a list of bandwidth resources.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeBandwidthLimitation|
|RegionId|String|Yes|ID of the target region. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceType|String|Yes|Instance type. For more information, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#), or call [DescribeInstanceTypes](intl.en-US/API Reference/Instances/DescribeInstanceTypes.md#) to obtain the latest type list.|
|InstanceChargeType|String|No|Billing method of the instances. Optional values: [Subscription](../../../../intl.en-US/Pricing/Pricing overview.md#). Value range:-   PrePaid: Subscription
-   PostPaid: Pay-As-You-Go

Default value: PostPaid.|
|SpotStrategy|String|No|Specifies whether a Pay-As-You-Go instance is a spot instance or not. Value range:-   NoSpot: The instance is not a spot instance.
-   SpotWithPriceLimit: The instance is a spot instance and its price is a spot price.
-   SpotAsPriceGo: The instance is a spot instance and its price is the market price.

Default: NoSpot. If `InstanceChargeType` is set to `PostPaid`, `SpotStrategy` can be valid.|
|OperationType|String|No|Specifies operation limits of the bandwidth.  Optional values:-   Upgrade: Upgrade bandwidth
-   Downgrade: Downgrade bandwidth
-   Create: Create bandwidth

Default: Create.|
|ResourceId|String|No| Resource ID.  If you set `OperationType`  to  `Upgrade` or `Downgrade` ,  you must specify the ResourceId.|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Bandwidths|Array of [`BandwidthType`](#BandwidthType)|A collection of bandwidth types|

 **BandwidthType** 

|Name|Type|Description|
|:---|:---|:----------|
|InternetChargeType|String|Network billing method. Values: Value range-   Paybytraffic: The bandwidth fees is charged on an hourly basis according to actual traffic usage. 

|
|Min|Integer|Minimum limit of the bandwidth. No value is returned if the parameter is null.|
|Max|Integer|Maximum limit of the bandwidth. No value is returned if the parameter is null.|
|Unit|Integer|Resource type unit. No value is returned if the parameter is null.|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeBandwidthLimitation
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response sample** 

**XML format**

```
<DescribeBandwidthLimitationResponse>
    <Bandwidths>
          <Bandwidth>
            <InternetChargeType>PayByTraffic</InternetChargeType>
            <Max>100</Max>
            <Min>0</Min>
            <Unit>Mbps</Unit>
        </Bandwidth>
          <Bandwidth>
            <InternetChargeType>PayByTraffic</InternetChargeType>
            <Max>100</Max>
            <Min>0</Min>
            <Unit>Mbps</Unit>
        </Bandwidth>
     </Bandwidths>
    <RequestId>675B6D89-A3EB-4987-BAF3-610591E0D019</RequestId>
</DescribeBandwidthLimitationResponse>
```

 **JSON format** 

```
{
    " Bandwidths": {
        " Bandwidth": [
        {
            "InternetChargeType": "PayByTraffic",
            "Max": 100,
            "Min": 0,
            "Unit": "Mbps"
        },
        {
            "InternetChargeType": "PayByTraffic",
            "Max": 100,
            "Min": 0,
            "Unit": "Mbps"
        }]
    },
    "RequestId": "675B6D89-A3EB-4987-BAF3-610591E0D019",
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Description|
|:---------|:------------|:----------------|:----------|
|Invalid.InstanceChargeType|The specified InstanceChargeType is not valid.|400|The specified `InstanceChargeType` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|Unavailable.Regions|The available regions does not exists.|404|The specified `RegionId` does not have permission.|

