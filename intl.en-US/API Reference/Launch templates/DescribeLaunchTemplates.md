# DescribeLaunchTemplates {#DescribeLaunchTemplates .reference}

Queries available instance launch templates.

## Request parameters {#RequestParameter .section}

|Name|Type|Required |Description |
|:---|:---|:--------|:-----------|
|Action |String |Yes |The name of this interface Value: DescribeLaunchTemplates.|
|RegionId|String |Yes|Region ID of an instance launch template. To view the latest list of Alibaba Cloud regions, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#).|
|LaunchTemplateId|String|No|Instance launch template ID. You must specify the `LaunchTemplateId`   or `LaunchTemplateName` to determine the template.|
|LaunchTemplateName|String |No |Instance launch template name.|
|PageNumber |Integer |No |Page number of the instance launch template list. Start value: 1.Default value: 1.

|
|PageSize|Integer|No |Number of rows per page when querying by page. Maximum Value: 50. Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|TotalCount|Integer |Total number of instance launch templates.|
|PageNumber|Integer |Current page number. |
|PageSize |Integer  |Number of rows per page when querying by page.|
|LaunchTemplateSet|[LaunchTemplateSet](#LaunchTemplateSet)|The instance launch template information set.|

**LaunchTemplateSet** 

|Name |Type |Description |
|:----|:----|:-----------|
|CreateTime |String |The creation time of an instance launch template.|
|ModifiedTime|String |Time of last modification.|
|LaunchTemplateId|String |Template ID.|
|LaunchTemplateName|String |Template name.|
|DefaultVersionNumber|Long |The default template version number. |
|LatestVersionNumber|Long|The latest template version number.|
|CreatedBy|String |Creator of the template.template.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeLaunchTemplates
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeLaunchTemplatesResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<PageSize>10</PageSize>
	<LaunchTemplateSets>
		<LaunchTemplateSet>
			<CreateTime>2018-05-14T14:18:00Z</CreateTime>
			<ModifiedTime>2018-05-14T14:18:00Z</ModifiedTime>
			<LaunchTemplateid>lt-m5e3ofjr1zn1aw7xxxx</LaunchTemplateid>
			<LaunchTemplateName>wd-1526307480xxx</LaunchTemplateName>
			<DefaultVersionNumber>1</DefaultVersionNumber>
			<LatestVersionNumber>1</LatestVersionNumber>
			<CreatedBy>1942111349714xxx</CreatedBy>
		</LaunchTemplateSet>
	</LaunchTemplateSets>
</DescribeLaunchTemplatesResponse>
```

 **JSON format ** 

```

	"RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
	"TotalCount":1,
	"PageNumber":1,
	"PageSize":10,
	"LaunchTemplateSets":{
		"LaunchTemplateSet":[{
			"LaunchTemplateName":"wd-1526307480xxx",
			"CreatedBy":"1942111349714xxx",
			"ModifiedTime":"2018-05-14T14:18:00Z",
			"LatestVersionNumber":1,
			"CreateTime":"2018-05-14T14:18:00Z",
			"LaunchTemplateId":"lt-m5e3ofjr1zn1aw7qdxxx",
			"DefaultVersionNumber":1
		
	}

```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code |Error message|HTTP status code |Description |
|:----------|:------------|:----------------|:-----------|
|MissingParameter |The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400 |A required parameter is missing.|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400 |The specified parameter is invalid.|
|InnerServiceFailed|call inner service failed|403 |Internal server error.|

