# DescribeRegions {#DescribeRegions .reference}

Describes the latest Alibaba Cloud regions that are available to you.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeRegions.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Regions|[RegionType](reseller.en-US/API Reference/Data type/RegionType.md#)|A collection that includes region information.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeRegions
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeRegionsResponse>
    <RequestId>611CB80C-B6A9-43DB-9E38-0B0AC3D9B58F</RequestId>
    <Regions>
        <Region>
            <RegionId>cn-hangzhou </RegionId>
        </Region>
        <Region>
            <RegionId>cn-qingdao</RegionId>
        </Region>
    </Regions>
</DescribeRegionsResponse>
```

 **JSON format** 

```
{
    "RequestId": "611CB80C-B6A9-43DB-9E38-0B0AC3D9B58F",
    "Regions": {
        "Region": [{
            "RegionId": "cn-hangzhou "
        },
        {
            "RegionId": "cn-qingdao"
        }]
    }
}e
```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [Common error codes](reseller.en-US/API Reference/Getting started/Response results.md#commonErrorCodes).

