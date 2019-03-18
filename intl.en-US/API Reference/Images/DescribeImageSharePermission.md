# DescribeImageSharePermission {#DescribeImageSharePermission .reference}

Queries all the authorized users to whom one of your custom image is shared. The responded information can be displayed on several pages. By default, 10 entries of record are displayed on each page.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeImageSharePermission.|
|RegionId|String|Yes|ID of the region to where the custom image belongs. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|ID of your custom image.|
|PageNumber|Integer|No|The page number of the responded information. Initial value: 1.Default value: 1.

|
|PageSize|Integer|No|The number of entries on each page for the responded information. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|ImageId|String|ID of the custom image.|
|RegionId|String|Region ID of the custom image.|
|ShareGroups|[ShareGroupType](reseller.en-US/API Reference/Data type/ShareGroupType.md#)|Type of the shared group.|
|Accounts|[AccountType](reseller.en-US/API Reference/Data type/AccountType.md#)|Type of the Alibaba Cloud user account.|
|TotalCount|Integer|Total number of entries.|
|PageNumber|Integer|Page number.|
|PageSize|Integer|Maximum number of entries on each page.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeImageSharePermission
&RegionId=cn-qingdao
&ImageId=m-282dzntc7
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeImageSharePermissionResponse>
    <ImageId>m-282dzntc7</ImageId>
    <PageNumber>1</PageNumber>
    <PageSize>10</PageSize>
    <RegionId>cn-qingdao</RegionId>
    <TotalCount>1</TotalCount>
    <RequestId>441CF898-42FF-47CF-9348-3C3BFF557278</RequestId>
    <ShareGroups>
        <ShareGroup>
            <Group>all</Group>
        </ShareGroup>
    </ShareGroups>
    <Accounts>
        <Account>
            <AliyunId>18865085298XXXXXX</AliyunId>
        </Account>
    </Accounts>
</DescribeImageSharePermissionResponse>
```

 **JSON format** 

```
{
    "ShareGroups": {
        "ShareGroup": [
            {
                "Group": "all"
            }
        ]
    },
    "Accounts": {
        "Account": [
            {
                "AliyunId": "18865085298XXXXXX"
            }
        ]
    },
    "ImageId": "m-282dzntc7",
    "PageNumber": 1,
    "PageSize": 10,
    "RegionId": "cn-qingdao",
    "TotalCount": 1,
    "RequestId": "9AD96F49-0BE5-4868-A66A-224352549CEC"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message |HTTP status code |Meaning|
|:---------|:-------------|:----------------|:------|
|MissingParameter|The input parameter “RegionId “ that is mandatory for processing this request is not supplied.|400|You must specify the `RegionId`. |
|MissingParameter|The input parameter “ImageId “ that is mandatory for processing this request is not supplied.|400|You must specify the `ImageId`.|
|InvalidRegionId.NotFound|The specified region does not exist.|404|The specified `RegionId` does not exist.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|404|The specified ImageId does not exist.|

