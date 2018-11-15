# InstallCloudAssistant {#reference_k2y_51c_n2b .reference}

Installs the cloud assistant client on one or more instances. After you call InstallCloudAssistant and RebootInstance, the cloud assistant client takes effect.

## Request parameters {#RequestParameter .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: InstallCloudAssistant.|
|RegionId|String|Yes|The ID of the region where the ECS instance is located. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to view the latest region list.|
|InstanceIds|Array|Yes|The list of instance IDs. For example, if Python SDK is used, you can set the value to \[InstanceID1, InstanceID2, InstanceID3…\]. A single request supports up to 100 instances.|

## Response parameters {#ResponseParameter .section}

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=InstallCloudAssistant
&RegionId=cn-hangzhou
&InstanceIds=["i-bp11f7trr4hbi1xxxxxx", "i-bp1iudwa5b1tqaxxxxxx"]
&<Common Request Parameters>
```

**Response examples** 

**XML format**

```
<DeleteInstanceResponse>
    <RequestId>928E2273-5715-46B9-A730-238DC996A533</RequestId>
</DeleteInstanceResponse>
```

**JSON format** 

```
{
    "RequestId": "928E2273-5715-46B9-A730-238DC996A533"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|MissingParameter.RegionId|The input parameter "RegionId" that is mandatory for processing this request is not supplied.|400|The error message returned when `RegionId` is required, or you cannot use resources in that region.|
|MissingParameter.InstanceIds|The input parameter "InstanceIds" that is mandatory for processing this request is not supplied.|400|The error message returned when `InstanceIds` is required.|
|InvalidInstance.NotFound|The specified instances do not exist.|404|The error message returned when the specified `InstanceId` does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The error message returned when the specified `RegionId` does not exist.|

