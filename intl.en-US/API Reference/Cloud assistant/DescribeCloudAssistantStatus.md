# DescribeCloudAssistantStatus {#DescribeCloudAssistantStatus .reference}

Checks whether the cloud assistant client is installed or not on one or more instances.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: DescribeCloudAssistantStatus.|
|RegionId|String|Yes|The ID of the region where the ECS instance is located. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to view the latest region list.|
|InstanceIds|Array|Yes|The list of instance IDs. For example, if Python SDK is used, you can set the value to \[InstanceID1, InstanceID2, InstanceID3…\]. A single request supports up to 100 instances.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceCloudAssitantStatus|[InstanceCloudAssitantStatusSet](intl.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md#InstanceCloudAssitantStatusSet)|A set of installation statuses of the cloud assistant in the instance.|

**InstanceCloudAssitantStatusSet**

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|A set of installation statuses of the cloud assistant in the instance.|
|CloudAssitantStatus|Boolean|Indicates whether the cloud assistant is installed on the instance.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeCloudAssistantStatus
&RegionId=cn-hangzhou
&InstanceIds=["i-bp11f7trr4hbi1xxxxxx", "i-bp1iudwa5b1tqaxxxxxx"]
&<Common Request Parameters>
```

**Response examples** 

**XML format**

```
<DescribeCloudAssistantStatusResponse>
	<InstanceCloudAssitantStatus>
		<InstanceCloudAssitantStatusSet>
			<InstanceId>i-bp11f7trr4hbi1xxxxxx</InstanceId>
			<CloudAssitantStatus>True</CloudAssitantStatus>
		</InstanceCloudAssitantStatusSet>
		<InstanceCloudAssitantStatusSet>
			<InstanceId>i-bp1iudwa5b1tqaxxxxxx</InstanceId>
			<CloudAssitantStatus>True</CloudAssitantStatus>
		</InstanceCloudAssitantStatusSet>
	</InstanceCloudAssitantStatus>
</DescribeCloudAssistantStatusResponse>
```

**JSON format**

```
{
  "InstanceCloudAssitantStatus": {
    "InstanceCloudAssitantStatusSet": [
      {
        "InstanceId": "i-bp11f7trr4hbi1xxxxxx",
        "CloudAssitantStatus": "True"
      },
      {
        "InstanceId": "i-bp1iudwa5b1tqaxxxxxx",
        "CloudAssitantStatus": "True"
      }
    ]
  }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|MissingParameter.InstanceIds|The input parameter "InstanceIds" that is mandatory for processing this request is not supplied.|400|The error message returned when `InstanceIds` is required.|
|MissingParameter.RegionId|The input parameter "RegionId" that is mandatory for processing this request is not supplied.|400|The error message returned when `RegionId` is required, or you cannot use resources in that region.|
|InvalidInstance.NotFound|The specified instances do not exist.|404|The error message returned when the specified `InstanceId` does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The error message returned when the specified `RegionId` does not exist.|

