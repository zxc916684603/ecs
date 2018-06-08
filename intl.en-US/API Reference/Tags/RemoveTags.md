# RemoveTags {#RemoveTags .reference}

Removes one or more tags from the specified ECS resource, such as instances, disks, snapshots, images, and security groups.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: RemoveTags.|
|RegionId|String|Yes|The ID of the region to which the ECS resource belongs. For more information, see Regions and zones, or call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ResourceType|String|Yes|Indicates the type of resource when you bind a tag to it. Optional values:-   disk
-   instance
-   image
-   securitygroup
-   snapshot

All values are in lowercase.|
|ResourceId|String|Yes|Resource ID. For example, if you set the `ResourceType` to `instance`, the resource ID can be interpreted as the instance ID.|
|Tag.n.Key|String|No|The tag key where `n` ranges from 1 to 5. You can call [DescribeTags](intl.en-US/API Reference/Tags/DescribeTags.md#) to view your available tags.|
|Tag.n.Value|String|No|The tag value where `n`  ranges from 1 to 5. If you do not use this parameter, the tag that is specified by the `Tag.n.Key` is removed from the specified resource.|

## Response parameters {#section_f54_lk5_xdb .section}

For more information about all the common response parameters, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=RemoveTags
&ResourceId=s-946ntx4wr
&ResourceType=snapshot
&RegionId=cn-shenzhen
&Tag. 1. Key=test
&Tag. 1. Value=api
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<RemoveTagsResponse>
    <RequestId>6A2C8AB5-E15D-478C-B56A-CF3DAF060028</RequestId>
</RemoveTagsResponse>
```

 **JSON format** 

```

  "RequestId": "6A2C8AB5-E15D-478C-B56A-CF3DAF060028"

```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|You can remove up to five tags from specified ECS resource in this query request.|
|InvalidResourceId.NotSupported|The specified ResourceId does not support tagging.|403| You cannot remove tags from the specified ECS resource.|
|InvalidResourceId.NotFound|The specified ResourceId is not found in our records.|404|The specified `ResourceId` does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|The specified `RegionId` does not exist.|
|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|404|The specified `ResourceType` does not exist.|

