# DescribeDeploymentSets {#DescribeDeploymentSets .reference}

Queries a list of properties of one or more deployment sets.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|Name of this interface. Value: DescribeDeploymentSets.|
|RegionId|String|Yes|The region ID to which the deployment set belongs.For more information, call [DescribeRegions](../intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|DeploymentSetIds|String|No|List of deployment set IDs. This value can be a JSON array composed of multiple deployment set IDs. The format is \["ds-xxxxxxxxx", "ds-yyyyyyyyy", … "ds-zzzzzzzzz"\]. The JSON array supports up to 100 IDs, separated by commas \(`,`\).|
|DeploymentSetName|String|No|Deployment set name.|
|Strategy|String|No|Deployment strategy. Value: Availability.Default value: Null.

|
|PageNumber|Integer|No|The page number of the deployment set lists. Starts from: 1.Default: 1.

|
|PageSize|Integer|No|The number of lines per page set for paging query. Maximum: 100.Default: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of queried deployment sets.|
|PageNumber|Integer|The number of deployment set pages.|
|PageSize|Integer  |Sets the number of deployment set on each page.|
|DeploymentSetList|Array of [DeploymentSetType](#)|An array composed of DeploymentSet sets. Returns deployment set details.|

**Deployment set type** 

|Name|Type|Description|
|:---|:---|:----------|
|DeploymentSetId|String|Deployment Set ID.|
|DeploymentStrategy|String|Deployment strategy.|
|DeploymentSetName|String|Deployment set name.|
|Description|String|Deployment set description.|
|InstanceIds|Array of InstanceId|The instances contained in the deployment set.|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=DescribeDeploymentSets
&RegionId=cn-hangzhou
&DeploymentSetsIds=["ds-bp13v7bjnj9gisnlo1"]
&<Common Request Parameters>
```

**Reponse examples**

**XML format**

```
<DescribeDeploymentSetsResponse>
	<PageSize>10</PageSize>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<RequestId>1CB9A584-9E43-408D-B5A8-DB42CDECE03B</RequestId>
	<DeploymentSets>
		<DeploymentSet>
			<DeploymentSetDescription>default</DeploymentSetDescription>
			<DeploymentSetId>ds-bp13v7bjnj9gisnlo1ow</DeploymentSetId>
			<DeploymentStrategy>Availability</DeploymentStrategy>
			<DeploymentSetName>test default</DeploymentSetName>
			<InstanceIds>
				<InstanceId>i-sdfkjsdfk</InstanceId>
				<InstanceId>i-kiiwsch</InstanceId>
			</InstanceIds>
		</DeploymentSet>
	</DeploymentSets>
</DescribeDeploymentSetsResponse>
```

**JSON format**

```
{
	"PageSize": 10,
	"TotalCount": 1,
	"PageNumber": 1,
	"RequestId": "1CB9A584-9E43-408D-B5A8-DB42CDECE03B",
	"DeploymentSets":
		{
			"DeploymentSet":
				[
					{
						"DeploymentSetDescription": "default",
						"DeploymentSetId": "ds-bp13v7bjnj9gisnlo1ow",
						"DeploymentStrategy": "Availability",
						"DeploymentSetName": "test default",
						"InstanceIds":
							{
								"InstanceId": ["i-sdfkjsdfk", "i-kiiwsch"]
							}
					}
				]
		}
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

