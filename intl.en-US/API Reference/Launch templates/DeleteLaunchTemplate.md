# DeleteLaunchTemplate {#DeleteLaunchTemplate .reference}

Deletes an instance launch template.

## Request parameters {#RequestParameter .section}

|Name |Type |Required|Description |
|:----|:----|:-------|:-----------|
|Action |String |Yes |The name of this interface. Value: DeleteLaunchTemplate.|
|RegionId |String |Yes|Region ID of an instance launch template. To view the latest list of Alibaba Cloud regions, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#). |
|LaunchTemplateId|String |No |Instance launch template ID. For more information, call [DescribeLaunchTemplates](intl.en-US/API Reference/Launch templates/DescribeLaunchTemplates.md#). Either the `LaunchTemplateId`  or the `LaunchTemplateName` must be specified to determine the template.|
|LaunchTemplateName |String |No |Instance launch template name.|

## Response parameters {#ResponseParameters .section}

All are common response parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example ** 

```
https://ecs.aliyuncs.com/?Action=DeleteLaunchTemplate
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DeleteLaunchTemplateResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DeleteLaunchTemplateResponse>
```

 **JSON format** 

```

    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",

```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface.  For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code |Error message|HTTP status code |Description |
|:----------|:------------|:----------------|:-----------|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|A required parameter is missing.|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400 |The specified parameter is invalid.|
|InnerServiceFailed|call inner service failed|403 |Internal server error.|

