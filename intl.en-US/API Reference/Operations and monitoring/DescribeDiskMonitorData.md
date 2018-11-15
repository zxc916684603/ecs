# DescribeDiskMonitorData {#DescribeDiskMonitorData .reference}

Queries the monitoring data of a specified disk. The monitoring data includes the operational behaviors such as the measured read IOPS, write IOPS, read bandwidth \(Bps\), write bandwidth \(Bps\), read latency \(ms\), and write latency \(ms\) of a disk. Because we cannot obtain the data if the disk is not in the In\_Use status, some data may be missing from the returned result.

## Description {#section_esm_5t4_ydb .section}

When you call this interface, consider the following:

-   You can only query monitoring information for the disks that are in the In\_use status. For more information, see Basic cloud disk status.

-   Returns at most 400 at a time. Up to 400 monitoring entries can be returned for one request. If the specified \(EndTime-StartTime\)/Period is greater than 400, an error is returned.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeDiskMonitorData.|
|DiskId|String|Yes|The disk ID.|
|StartTime|String|Yes|The start time. In UTC format. It is represented according to ISO8601, for example YYYY-MM-DDThh:mm:ssZ. If the seconds \(ss\) is not 00, it is set to start from the next minute.|
|EndTime|String|Yes|The end time, in UTC format. It is represented according to ISO8601, for example YYYY-MM-DDThh:mm:ssZ. If the seconds \(ss\) is not 00, it is set to end with the next minute.|
|Period|Integer|No|The granularity of the retrieved monitoring data. Unit of measurement: second.  Optional values:-   60
-   600
-   3600

Default value: 60.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of disk monitoring data entries.|
|MonitorData|[DiskMonitorDataType](reseller.en-US/API Reference/Data type/DiskMonitorDataType.md#)|A collection composed of disk monitoring data DiskMonitorDataType.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeDiskMonitorData
&DiskId=d-mydisk001
&StartTime=2014-07-23T12:07:00Z
&EndTime=2014-07-23T12:09:00Z
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeDiskMonitorDataResponse>
        <MonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>0</BPSTotal>
                        <BPSWrite>0</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:07:00Z</TimeStamp>
                </DiskMonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>204</BPSTotal>
                        <BPSWrite>204</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:08:00Z</TimeStamp>
                </DiskMonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>819</BPSTotal>
                        <BPSWrite>819</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:09:00Z</TimeStamp>
                </DiskMonitorData>
        </MonitorData>
        <RequestId>BF666447-B171-4076-BCBA-48437C18FD76</RequestId>
        <TotalCount>3</TotalCount>
</DescribeDiskMonitorDataResponse>
```

 **JSON format** 

```
{
  "MonitorData": {
    "DiskMonitorData": [
      {
        "BPSRead": 0,
        "BPSTotal": 0,
        "BPSWrite": 0,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:07:00Z"
      },
      {
        "BPSRead": 0,
        "BPSTotal": 204,
        "BPSWrite": 204,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:08:00Z"
      },
      {
        "BPSRead": 0,
        "BPSTotal": 819,
        "BPSWrite": 819,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:09:00Z"
      }
    ]
  }, 
  "RequestId": "A48A0A77-34F5-4C33-9066-9E8D2DA0D8E2",
  "TotalCount": 3
}
```

## Error codes {#ErrorCode .section}

|Error code|Error information|HTTP status code|Description|
|:---------|:----------------|:---------------|:----------|
|InvalidEndTime.Malformed|The specified parameter “SignatureMethod” is not valid.|400|The specified `EndTime`  is invalid.|
|InvalidParameter.TooManyDataQueried|Too many data queried.|400|At most 400 data can be returned at a time,  the specified \(`EndTime`–`StartTime`\)/`Peroid` needs to be less than equal 400.|
|InvalidPeriod.ValueNotSupported|The specified parameter “SignatureMethod” is not valid.|400|The specified `Period` is not invalid.|
|InvalidStartTime.TooEarly|The specified parameter “StartTime” is too early.|400|The specified `StartTime` is too early.|
|InvalidStartTime.Malformed|The specified parameter “SignatureMethod” is not valid.|400|The specified `StartTime` is not legal.|
|InvalidDiskId.NotFound|The DiskId provided does not exist.|404|The specified `DiskId`  does not exist.|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|During system streaming, please try again later.|

