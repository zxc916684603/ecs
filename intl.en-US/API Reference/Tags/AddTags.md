# AddTags {#AddTags .reference}

Adds or overwrites one or more tags to your ECS resource. You can add tags to ECS resources such as instances, disks, snapshots, images, and security groups for easier and customizable operation and management.

## Description {#section_av1_byg_ydb .section}

When you call this interface, consider the following:

-   Up to 10 tags can be added to each ECS resource.
-   The key \(`Tag.n.Key`\) and value \(`Tag.n.Value`\) of the tag must be key-value matched.

-   If the key \(`Tag.n.Key`\) is already added for the specified resource, the former value \(`Tag.n.Value`\) is overwritten with the new one.


## Request parameters {#section_mzx_3yg_ydb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AddTags|
|RegionId|String|Yes|The ID of the region to which the ECS resource belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ResourceType|String|Yes| The type of the ECS resource. Value range:-   disk
-   instance
-   image
-   securitygroup
-   snapshot

All values must be lowercase.|
|ResourceId|String|Yes|The resource ID.  For example, if you set the `ResourceType` to `instance`, the ResourceId can be interpreted as InstanceId.|
|Tag.n.Key|String|Yes|The tag key where `n` ranges from 1 to 5. Tag names can be up to 64 characters in length. Cannot begin with aliyun, acs, http:// or https://. Cannot be a null string.|
|Tag.n.Value|String|Yes|The tag value where `n` ranges from 1 to 5. Tag names can be up to 128 characters in length. Cannot begin with aliyun, acs, http:// or https://. Can be a null string.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AddTags
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
<AddTagsResponse>
    <RequestId>C46FF5A8-C5F0-4024-8262-B16B639225A0</RequestId>
</AddTagsResponse>
```

 **JSON format** 

```
{
  "RequestId": "C46FF5A8-C5F0-4024-8262-B16B639225A0"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error codes|Error message|HTTP status code|Description|
|:----------|:------------|:---------------|:----------|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|The key \(`Tag.n.Key`\) and value \(`Tag.n.Value`\) of the tag must match key values.|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|You can specify a maximum of five tags.|
|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|400|The specified `Tag.n.Key` is invalid.|
|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|400|The specified `Tag.n.Value` is invalid.|
|OperationDenied.QuotaExceed|The quota of tags on resource is beyond permitted range.|400|Up to 10 tags can be added to each ECS resource.|
|InvalidResourceId.NotSupported|The specified ResourceId does not support tagging.|403|You cannot add tags to the specified ECS resource.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|The specified `RegionId` does not exist.|
|InvalidResourceId.NotFound|The specified ResourceId is not found in our records.|404|The specified `ResourceId` does not exist.|
|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|404|The specified `ResourceType` does not exist.|

