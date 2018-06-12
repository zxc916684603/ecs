# DescribeInstanceTypeFamilies {#DescribeInstanceTypeFamilies .reference}

Describes the resources list of instance type families provided by Alibaba Cloud ECS. For more information, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#).

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInstanceTypeFamilies|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|Generation|String|No|The generation of the instance type families. Optional values:-   ecs-1: Generation I, which consists of the earliest and cost-effective instance types.
-   ecs-2: Generation II, which is available later than the first generation of type families.
-   ecs-3: Generation III which consists of the latest and high performance instance type families.

|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceTypeFamilies|[InstanceTypeFamilyItemType](intl.en-US/API Reference/Data type/InstanceTypeFamilyItemType.md#)|A collection composed of InstanceTypeFamilyItemType.|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceTypeFamilies
&RegionId=cn-hangzhou
&<Common request parameters>
```

**Response sample** 

**XML format**

```
<DescribeInstanceTypeFamiliesResponse>
    <InstanceTypeFamilies>
        <InstanceTypeFamily>
            <InstanceTypeFamilyId>ecs.t1</InstanceTypeFamilyId>
            <Generation>ecs-1</Generation>
        </InstanceTypeFamily>
        <InstanceTypeFamily>
            <InstanceTypeFamilyId>ecs.s2</InstanceTypeFamilyId>
            <Generation>ecs-1</Generation>
        </InstanceTypeFamily>
        <InstanceTypeFamily>
            <InstanceTypeFamilyId>ecs.s3</InstanceTypeFamilyId>
            <Generation>ecs-1</Generation>
        </InstanceTypeFamily>
    </InstanceTypeFamilies>
    <RequestId>6B187E0A-C075-4D08-8B6F-6213950E8733</RequestId>
</DescribeInstanceTypeFamiliesResponse>
```

 **JSON format** 

```
{
    "InstanceTypeFamilies":{
        "InstanceTypeFamily":[
            {
                "InstanceTypeFamilyId":"ecs.t1",
                "Generation":"ecs-1"
            },
            {
                "InstanceTypeFamilyId":"ecs.s2",
                "Generation":"ecs-1"
            },
            {
                "InstanceTypeFamilyId":"ecs.s3",
                "Generation":"ecs-1"
            }
        ]
    },
    "RequestId":"6B187E0A-C075-4D08-8B6F-6213950E8733"
}
```

## Error codes {#ErrorCode .section}

All are common error codes. For more error codes, see the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

