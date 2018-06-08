# ModifyLaunchTemplateDefaultVersion {#ModifyLaunchTemplateDefaultVersion .reference}

Sets a specified version of this template as the default version. If you do not specify a template version number when creating an instance \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\), default version is used.

## Request parameters {#RequestParameter .section}

|Name |Type |Required|Description|
|:----|:----|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyLaunchTemplateDefaultVersion.|
|RegionId |String |Yes|Region ID of the template. To view the latest list of Alibaba Cloud regions, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#).|
|DefaultVersionNumber|Long|Yes|Sets the default version number for the instance launch template.|
|LaunchTemplateId|String|No|Instance launch template ID. You must specify the `LaunchTemplateId` or  `LaunchTemplateName` to determine the template.|
|LaunchTemplateName|String |No |Instance launch template name. You must specify the `LaunchTemplateId` or `LaunchTemplateName` to determine the template.|

## Response parameters {#ResponseParameter .section}

All are public response parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyLaunchTemplateDefaultVersion
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&DefaultVersionNumber=2
&<Common Request Parameters>
```

**Response example ** 

**XML format**

```
<ModifyLaunchTemplateDefaultVersionResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</ModifyLaunchTemplateDefaultVersionResponse>
```

 **JSON format** 

```

    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",

```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidLaunchTemplate.NotFound|The specified LaunchTemplateId “\{0\}” LaunchTemplateName “\{1\}” is not found.|400|The specified `LaunchTemplateId`  or `LaunchTemplateName` does not exist.|
|InvalidLaunchTemplateVersion.NotFound|The specified LaunchTemplateId “\{0\}” Version “\{1\}” is not found.|400|The specified `DefaultVersionNumber` does not exist.|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|A required parameter is missing.|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|The specified parameter is invalid.|
|InnerServiceFailed|call inner service failed|403|Internal server error.|

