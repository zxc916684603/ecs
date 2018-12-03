# ModifyDeploymentSetAttributes {#ModifyDeploymentSetAttributes .reference}

Modifies the name and description of a deployment set.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String |Yes|The action that you want to perform. Value: ModifyDeploymentSetAttributes.|
|RegionId|String|Yes|The region ID to which the deployment set belongs.For more information, call [DescribeRegions](../intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|DeploymentSetId|String|Yes|Deployment Set ID.|
|DeploymentSetName|String|No|New name for the deployment set.The name is a string of 2 to 128 characters. It must begin with an English or a Chinese character. It can contain A-Z, a-z, Chinese characters, numbers, periods \(.\), colons \(:\), underscores \(\_\), and hyphens \(-\).|
|Description|String|No|New description for the deployment set.It cannot begin with http:// or https://.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [Common response parameters](../intl.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples {#section_g4q_shf_2fb .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=ModifyDeploymentSetAttributes
&RegionId=cn-hangzhou
&Strategy=Availability
&DeploymentSetId=ds-bp1frxuzdg87zh4pzqkc
&DeploymentSetName=AvailMySet
&<Common Request Parameters>
```

**Response examples**

**XML format**

```
<ModifyDeploymentSetAttributesResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyDeploymentSetAttributesResponse>
```

**JSON format**

```
{
	"RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidDescription.Malformed|The specified parameter “Description” is not valid.|400|The specified Description is invalid.|
|InvalidParameter.Strategy|The specified parameter Strategy is not valid|400|The specified deployment strategy is invalid.|
|MissingParameter|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the RegionId parameter. You are not authorized to use the resources of the specified region.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|The specified RegionId does not exist.|

