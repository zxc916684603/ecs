# DeleteDeploymentSet {#DeleteDeploymentSet .reference}

Deletes a deployment set.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Required|The name of this interface. Value: DeleteDeploymentSet.|
|RegionId|String|Required|The region ID to which the deployment set belongs.For more information, call [DescribeRegions](../intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|DeploymentSetId|String|Required|Deployment Set ID. If instances exist in the deployment set, you cannot delete the deployment set.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [Common response parameters](../intl.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteDeploymentSet
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1frxuzdg87zh4pzqkc
&<Common Request Parameters>
```

```
https://ecs.example.com/?Action=DeleteDeploymentSet
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1frxuzdg87zh4pzqkc
&<Common Request Parameters>
```

**Response examples**

**XML format**

```
<DeleteDeploymentSetResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteDeploymentSetResponse>
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
|MissingParameter|The input parameter “DeploymentSetId” that is mandatory for processing this request is not supplied.|400|You need to specify the value of DeploymentSetId.|
|DependencyViolation.NotEmpty|There are still instance\(s\) in the specified DeploymentSetId.|403|The specified deployment set cannot have any instance.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|The specified RegionId does not exist.|

