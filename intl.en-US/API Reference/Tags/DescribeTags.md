# DescribeTags {#DescribeTags .reference}

Describes one or more of your available tags. You can set criteria to match tags, such as by specifying the ECS resource types, resource IDs, tag keys, or tag values. We use the AND \(&&\) operator for your conditions and return a specific list of results from your operation.

## Description {#section_zxn_2ph_ydb .section}

In particular, if a tag key \(`Tag.n.Key`\) is specified, but no tag value \(`Tag.n.Value`\) is specified, all tags related to the tag-key are queried. If the tag key-value is specified, tag that exactly matches the queried key-value.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeTags|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ResourceType|String|Yes|The type of the ECS resource. Value range:-   disk
-   instance
-   image
-   securitygroup
-   snapshot

Values are case-sensitive.|
|ResourceId|String|No|The resource ID. For example, if you set the `ResourceType` to `instance`, the ResourceId the ResourceId can be interpreted as InstanceId.|
|Tag.n.Key|String|No|The tag key where `n` ranges from 1 to 5.|
|Tag.n.Value|String|No|The tag value where `n` ranges from 1 to 5.|
|PageNumber|Integer|No| Displays the tags on several pages. 

 Initial value: 1.

 Default value: 1.

 |
|PageSize|Integer|No| The maximum entries on a page.

 Maximum: 100

 Default: 50

 |

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|Tags|[TagSetItem](intl.en-US/API Reference/Data type/TagSetItem.md#)|Returns a specific list of tags.|
|TotalCount|Integer|The total number of tags.|
|PageSize|Integer|The maximum entries on a page.|
|PageNumber|Integer|Displays the tags on several pages.|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeTags
&ResourceType=snapshot
&ResourceId=s-946ntx4wr
&RegionId=cn-hangzhou
&Tag. 1. Key=test
&Tag. 1. Value=api
&<Common Request Parameters>
```

**Response sample** 

**XML format**

```
<DescribeTagsResponse>
    <RequestId>B04B8CF3-4489-432D-83BA-6F128E4F2295</RequestId>
    <PageNumber>1</PageNumber>
    <PageSize>50</PageSize>
    <Tags>
        <Tag>
            <TagKey>test</TagKey>
            <TagValue>api</TagValue>
        </Tag>
    </Tags>
    <TotalCount>1</TotalCount>
</DescribeTagsResponse>
```

 **JSON format** 

```
{
  "PageNumber": 1,
  "PageSize": 50,
  "RequestId": "B04B8CF3-4489-432D-83BA-6F128E4F2295",
  "Tags": {
    "Tag": [
      {
        "TagKey": "test",
        "TagValue": "api"
      }
    ]
  },
  "TotalCount": 1
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Meaning|
|:---------|:------------|:----------------|:------|
|invalidTagKey.Malformed|The parameter Tag.n.Key is illegal.|400|The specified `Tag.n.Key` is invalid.|
|InvalidTagValue.Malformed|The parameter Tag.n.Value is illegal.|400|The specified `Tag.n.Value` is invalid.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|The specified `RegionId` does not exist.|
|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|404|The specified `ResourceType` does not exist.|

