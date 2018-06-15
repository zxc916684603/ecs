# CancelTask {#CancelTask .reference}

Cancels a specified active task. Currently, you can cancel the importing image action \([ImportImage](intl.en-US/API Reference/Images/ImportImage.md#)\) and the exporting image action \([ExportImage](intl.en-US/API Reference/Images/ExportImage.md#)\).

## Request parameters {#section_mzx_3yg_ydb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CancelTask.|
|RegionId|String|Yes|The region ID. For more information, see Regions and zones, or call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|TaskId|String|Yes|The task ID. You can call [DescribeTasks](intl.en-US/API Reference/Others/DescribeTasks.md#) to obtain the list of task IDs.|

## Response parameters {#section_f54_lk5_xdb .section}

For more information about all the common response parameters, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CancelTask
&RegionId=cn-hangzhou
&TaskId=t-23ym6mvro
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<CancelTaskResponse>
    <RequestId>4BE2C7FE-C7A4-4675-A153-174E032AABFB</RequestId>
</CancelTaskResponse>
```

 **JSON format** 

```

    "RequestId": "4BE2C7FE-C7A4-4675-A153-174E032AABFB"

```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface.  For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter|An input parameter “RegionId” that is mandatory for processing the request is not supplied.|400|You must specify the `RegionId` parameter.|
|MissingParameter|An input parameter “TaskId” that is mandatory for processing the request is not supplied.|400|You must specify the `TaskId` parameter.|
|InvalidRegionId.NotFound|The specified region not found.|400|The specified `RegionId` does not exist.|
|InvalidTaskId.NotFound|The specified “TaskId” is not found.|400|The specified `TaskId` does not exist.|
|CancelTaskFailed|The task is failed to cancel, Please contact the administrator.|403|Failed to cancel the task. Please [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to contact us.|
|InvalidTaskId.IncorrectTaskStatus|The specified task status is not invalid.|403|The specified task must be in the **Running** status.|
|InvalidTaskId.TaskActionNotSupport|The specified task action not support.|403|You cannot cancel the specified task.|

