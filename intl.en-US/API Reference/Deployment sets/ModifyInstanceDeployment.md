# ModifyInstanceDeployment {#ModifyInstanceDeployment .reference}

Adds an instance to a deployment set or moves an instance from one deployment set to another.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String |Yes|Name of this interface. Value: ModifyInstanceDeployment.|
|RegionId|String|Yes|The region ID where the deployment set and the instance are located.For more information, call [DescribeRegions](../intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|DeploymentSetId|String|Yes|Deployment set ID.|
|InstanceId|String|Yes|Instance ID. The instance must be in a `Stopped` or `Running` status.|
|Force|Boolean|No|Whether to forcibly change the host where the instance is located or not.-   True: Allows an instance to move to a new host. Allows you to restart **Running** instances, **Stopped** Subscription instances, and **Stopped** Pay-As-You-Go instances with termination fees.
-   False \(default\): The host cannot be changed for the instance. The system only attaches the deployment sets to the current host. This may cause the replacement of the deployment set to fail.

|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [Common response parameters](../intl.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceDeployment
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp13v7bjnj9gisnlo1
&<Common Request Parameters>
```

**Response examples**

**XML format**

```
<ModifyInstanceDeploymentResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceDeploymentResponse>
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
|DeploymentSet.InvalidId|The specified Deployment Set id doesn't exist.|400|The specified DeploymentSetId does not exist.|
|DeploymentSet.InstanceLimitExceeded|The number of instances on the specified Deployment Set has reached the limit.|403|The number of instances in the specified deployment set has reached the maximum number.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The current status of the resource does not support this operation.|
|DeploymentSet.ModificationFailed|The modification of deployment set is currently impossible.|403|The deployment set cannot be adjusted.|

