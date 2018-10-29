# DescribeTaskAttribute {#DescribeTaskAttribute .reference}

Describes the details about one or more tasks. Currently, the tasks that can be queried are the importing image action and the exporting image action.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeTaskAttribute.|
|RegionId|String|Yes|The region ID. Call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|TaskId|String|No|Task ID. You can call [DescribeTasks](reseller.en-US/API Reference/Others/DescribeTasks.md#) to obtain the list of task IDs.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|askId|String|The task ID.|
|TaskAction|String|The specified action.|
|RegionId|String|The region ID.|
|TaskStatus|String|The task status.|
|Progress|String|The task progress.|
|SupportCancel|Boolean| Whether the task can be canceled \([CancelTask](reseller.en-US/API Reference/Others/CancelTask.md#)\) or not. Possible values:-   True
-   False

|
|SuccessCount|Integer|The number of tasks that were completed.|
|FailedCount|Integer|The number of failed tasks.|
|CreationTime|String|Task creation time. The time is displayed in the format specified in the [ISO8601](reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. Format: YYYY-MM-DDThh:mm:ssZ.|
|FinishedTime|String|Task completion time. The time is displayed in the format specified in the ISO8601 standard, and the UTC time is used. Format: YYYY-MM-DDThh:mm:ssZ.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeTaskAttribute
&RegionId=cn-hangzhou
&TaskId=t-23ym6mvro
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<DescribeTaskAttributeResponse>
  2018-03-06T07:33:51Z
  <OperationProgressSet>
    <OperationProgress>
      <RelatedItemSet>
        <RelatedItem>
          <Name>OSSBucket</Name>
          <Value>image-temp</Value>
        </RelatedItem>
        <RelatedItem>
          <Name>OSSObject</Name>
          <Value>MYOSSPRE_m-23f8tcp8y_t-23ym6mvro.vhd</Value>
        </RelatedItem>
        <RelatedItem>
          <Name>ImageFormat</Name>
          <Value>vhd</Value>
        </RelatedItem>
      </RelatedItemSet>
      <ErrorMsg/>
      <ErrorCode/>
      <OperationStatus>Success</OperationStatus>
    </OperationProgress>
  </OperationProgressSet>
  <FinishedTime>2015-11-23T02:19Z</FinishedTime>
  <FailedCount>0</FailedCount>
  <SupportCancel>true</SupportCancel>
  <TotalCount>1</TotalCount>
  <SuccessCount>1</SuccessCount>
  <RequestId>EF0C5969-279B-49C8-AD83-BACCC74DD38C</RequestId>
  <RegionId>cn-hangzhou</RegionId>
  <TaskAction>ExportImage</TaskAction>
  <TaskStatus>Finished</TaskStatus>
  <TaskProcess>100%</TaskProcess>
  <TaskId>t-23ym6mvro</TaskId>
</DescribeTaskAttributeResponse>
```

 **JSON format** 

```
{
    "CreationTime": "2015-11-23T02:13Z",
    "OperationProgressSet": {
        "OperationProgress": [
            {
                "RelatedItemSet": {
                    "RelatedItem": [
                        {
                            "Name": "OSSBucket",
                            "Value": "image-temp"
                        },
                        {
                            "Name": "OSSObject",
                            "Value": "MYOSSPRE_m-23f8tcp8y_t-23ym6mvro.vhd"
                        },
                        {
                            "Name": "ImageFormat",
                            "Value": "vhd"
                        }
                    ]
                },
                "ErrorMsg": "",
                "ErrorCode": "",
                "OperationStatus": "Success"
            }
        ]
    },
    "FinishedTime": "2015-11-23T02:19Z",
    "FailedCount": 0,
    "SupportCancel": true,
    "TotalCount": 1,
    "SuccessCount": 1,
    "RequestId": "4BE2C7FE-C7A4-4675-A153-174E032AABFB",
    "RegionId": "cn-hangzhou",
    "TaskAction": "ExportImage",
    "TaskStatus": "Finished",
    "TaskProcess": "100%",
    "TaskId": "t-23ym6mvro"
}
```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [common error codes](reseller.en-US/API Reference/Getting started/Response results.md#commonErrorCodes).

