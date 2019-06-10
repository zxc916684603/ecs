# DescribeTasks {#doc_api_1063660 .reference}

Queries the progress of one or more asynchronous requests.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeTasks) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The ID of the region. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|Action|String|No|DescribeTasks| The operation that you want to perform. Set the value to DescribeTasks.

 |
|EndTime|String|No|2015-11-23T15:16:00Z| The start point of a time period. Tasks created during this period will be queried. The time follows the [ISO 8601](~~25696~~) standard and uses the UTC time. The format is yyyy-MM-ddTHH:mm:ssZ.

 |
|PageNumber|Integer|No|1| The page number. Starting value: 1. Default value: 1.

 |
|PageSize|Integer|No|2| The number of entries per page. Maximum value: 100. Default value: 10.

 |
|StartTime|String|No|2015-11-23T15:10:00Z| The end point of a time period. Tasks created during this period will be queried. The time follows the [ISO 8601](~~25696~~) standard and uses the UTC time. The format is yyyy-MM-ddTHH:mm:ssZ.

 |
|TaskAction|String|No|ImportImage| The operation name of the task. Valid values:

 -   ImportImage
-   ExportImage

 |
|TaskIds|String|No|\["t-bp10e8orkpqm0lc74o8x","t-bp10e8orkpqm0lc74o8y"\]| The ID of the task. You can specify up to 100 tasks at a time. Separate multiple tasks IDs with commas \(,\).

 |
|TaskStatus|String|No|Finished| The status of the task. Valid values:

 -   Finished
-   Processing
-   Waiting
-   Deleted
-   Paused
-   Failed

 Default value: null. The system retrieves tasks in the Finished, Processing, and Failed states. The request ignores other values.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|2| The number of entries per page.

 |
|RegionId|String|cn-hangzhou| The ID of the region.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |
|TaskSet| | | An array of tasks.

 |
|└ CreationTime|String|2015-11-24T12:50Z| The creation time.

 |
|└FinishedTime|String|2015-11-24T12:50Z| The end time.

 |
|└SupportCancel|String|true| Indicates whether a task can be canceled.

 |
|└TaskAction|String|IMPORT\_IMAGE| The name of the task.

 |
|└TaskId|String|t-bp10e8orkpqm0lc74o8X| The ID of the task.

 |
|└TaskStatus|String|Finished| The status of the task.

 |
|TotalCount|Integer|2| The number of items in the list.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeTasks
&RegionId=cn-hangzhou
&PageNumber=1 
&PageSize=2 
&TaskIds=t-bp10e8orkpqm0lc74o8X
&TaskAction=ImportImage
&TaskStatus=Finished
&StartTime=2015-11-23T15:10:00Z 
&EndTime=2015-11-23T15:16:00Z
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeTasksResponse> 
  <PageNumber>1</PageNumber>
  <TotalCount>2</TotalCount> 
  <PageSize>2</PageSize>
  <RegionId>cn-hangzhou</RegionId> 
  <RequestId>E5C82807-5588-4661-9A96-350B206A7623</RequestId> 
  <TaskSet> 
    <Task>
      <CreationTime>2015-11-24T12:50Z</CreationTime> 
      <FinishedTime>2015-11-24T12:50Z</FinishedTime> 
      <SupportCancel>true</SupportCancel> 
      <TaskAction>IMPORT_IMAGE</TaskAction> 
      <TaskStatus>Finished</TaskStatus> 
      <TaskId>t-bp10e8orkpqm0lc74o8X</TaskId> 
    </Task> 
    <Task> 
      <CreationTime>2015-11-23T15:10Z</CreationTime> 
      <FinishedTime>2015-11-23T15:16Z</FinishedTime> 
      <SupportCancel>true</SupportCancel> 
      <TaskAction>IMPORT_IMAGE</TaskAction> 
      <TaskStatus>Finished</TaskStatus> 
      <TaskId>t-23sgu0dyj</TaskId> 
    </Task> 
  </TaskSet> 
</DescribeTasksResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"TaskSet":[
		{
			"Task":[
				{
					"CreationTime":"2015-11-24T12:50Z",
					"FinishedTime":"2015-11-24T12:50Z",
					"SupportCancel":true,
					"TaskAction":"ImportImage",
					"TaskStatus":"Finished",
					"TaskId":"t-bp10e8orkpqm0lc74o8X"
				},
				{
					"CreationTime":"2015-11-23T15:10Z",
					"FinishedTime":"2015-11-23T15:16Z",
					"SupportCancel":true,
					"TaskAction":"ImportImage",
					"TaskStatus":"Finished",
					"TaskId":"t-23sgu0dyj"
				}
			]
		}
	],
	"PageSize":2,
	"RequestId":"F746C690-D9EA-4F87-AF31-8E1910FAB541",
	"RegionId":"cn-hangzhou"
}
```

## Error codes {#section_931_tw9_4w9 .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|MissingParameter|An input parameter "RegionId" that is mandatory for processing the request is not supplied.|The error message returned when the RegionId parameter is not specified.|
|400|InvalidRegionId.NotFound|The specified RegionId does not exist.|The error message returned when the specified Region ID does not exist. Check whether the service is available in this region.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

