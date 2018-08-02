# DescribeTasks {#DescribeTasks .reference}

Queries the progress of a specified asynchronous task.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeTasks.|
|RegionId|String|Yes|Region ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|TaskAction|String|Yes|The specified action to be queried. Optional values:-   ImportImage: Query the task of \([ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)\).
-   ExportImage: Query the task of \([ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)\).

|
|TaskIds|String|No|Task ID. Up to 100 task IDs are supported, and they are separated by comma \(`,`\).|
|TaskStatus|String|No|Task status. Optional values:-   Finished
-   Processing
-   Waiting
-   Deleted
-   Paused

Default value: null.Currently, you can query the task in the `Finished` and `Processing` status, and other value is ignored in the request.

|
|StartTime|String|No|Query by creation time, start time of the creation time period. The time is displayed in the format specified in the ISO8601 standard, and the UTC time is used. Format: YYYY-MM-DDThh:mmZ.|
|EndTime|String|No|Query by creation time, start time of the creation time period. The time is displayed in the format specified in the ISO8601 standard, and the UTC time is used. It is in the format of YYYY-MM-DDThh:mmZ.|
|PageNumber|Integer|No|Page number of the query result. Initial value: 1, default value: 1.|
|PageSize|Integer|No|Number of lines on each page, set for pagination query. Maximum value: 100, default value: 10.|

## Response parameters {#section_ay2_4yg_ydb .section}

|Name|Type|Description|
|:---|:---|:----------|
|TaskSet|[TaskType](intl.en-US/API Reference/Data type/TaskType.md#)|TaskSet|
|RegionId|String|Regional ID.|
|TotalCount|Integer|Number of items in the list.|
|PageNumber|Integer|Current page number.|
|PageSize|Integer|Number of items included in the current page.|

## Examples {#section_mv1_byg_ydb .section}

**Request example**

```

https://ecs.aliyuncs.com/?Action=DescribeTasks
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example**

**XML format**

```
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
      <TaskId>t-23mo8zf9w</TaskId>
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

**JSON format**

```
{
    "PageNumber": 1,
    "TotalCount": 2,
    "PageSize": 2,
    "RegionId": "cn-hangzhou",
    "RequestId": "F746C690-D9EA-4F87-AF31-8E1910FAB541"，
    "TaskSet": {
        "Task": [
            {
                "CreationTime": "2015-11-24T12:50Z",
                "FinishedTime": "2015-11-24T12:50Z",
                "SupportCancel": true,
                "TaskAction": "ImportImage",
                "TaskStatus": "Finished",
                "TaskId": "t-23mo8zf9w"
            },
            {
                "CreationTime": "2015-11-23T15:10Z",
                "FinishedTime": "2015-11-23T15:16Z",
                "SupportCancel": true,
                "TaskAction": "ImportImage",
                "TaskStatus": "Finished",
                "TaskId": "t-23sgu0dyj"
            }
        ]
    }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter|An input parameter “RegionId” that is mandatory for processing the request is not supplied.|400|The required parameter `RegionId` is missing.|
|InvalidRegionId.NotFound|The specified region not found.|400|The specified `RegionId` does not exist.|

