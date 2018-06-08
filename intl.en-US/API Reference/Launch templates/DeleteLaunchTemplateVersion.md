# DeleteLaunchTemplateVersion {#DeleteLaunchTemplateVersion .reference}

Deletes a specified instance launch template version. However, if the instance launch template version you intend to delete is the default version, you must use the [DeleteLaunchTemplate](intl.en-US/API Reference/Launch templates/DeleteLaunchTemplate.md#) API to delete the entire instance launch template. 

## Request parameters  {#RequestParameter .section}

|Name  |Type |Required|Description |
|:-----|:----|:-------|:-----------|
|Action |String |Yes |The name of this interface.  Value: DeleteLaunchTemplateVersion. |
|RegionId |String|Yes|Region ID of the template.  For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to view the latest list of Alibaba Cloud regions. |
|DeleteVersion.n |Long |Yes|Template version number. Value range of \`n\`: \[1,29\]. For more information, call [DescribeLaunchTemplateVersions](intl.en-US/API Reference/Launch templates/DescribeLaunchTemplateVersions.md#) to query the template version list.|
|LaunchTemplateId|String |No |Template ID.  Either the `LaunchTemplateId` or the `LaunchTemplateName` must be specified to determine the template.|
|LaunchTemplateName|String |No |Template name.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteLaunchTemplateVersion
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&DeleteVersion. 1=1
&<Common Request Parameters>
```

**Response example ** 

**XML format **

```
<DeleteLaunchTemplateVersionResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DeleteLaunchTemplateVersionResponse>
```

 **JSON format ** 

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
|InvalidOperation.DeleteDefaultVersion|Delete default version from template is not allowed. |403 |You cannot delete the default template version directly.|

