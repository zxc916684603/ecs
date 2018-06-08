# DescribeInstanceMonitorData {#DescribeInstanceMonitorData .reference}

Queries all the ECS-related monitoring data. The monitoring data includes the CPU usage of the ECS, data traffic received by the ECS, data traffic sent by the ECS, ECS network traffic, and ECS average bandwidth. You can only query the monitoring data of an ECS that is not in the `Stopped` status.

## Description {#section_dwp_4w4_ydb .section}

When you call this interface, consider the following:

-   You can only query up to 400 entries of monitoring data each time. If the specified \(`EndTime` `StartTime`\)/`Peroid` \> 400, an error is returned.

-   You can only query the monitoring data that is 30 days later than the current time. If the specified `StartTime` is earlier than 30 days, an error is returned.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInstanceMonitorData.|
|InstanceId|String|Yes|ID of the target instance.|
|StartTime|String|Yes|The start time of the monitoring data, which is represented according to [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC is required. Valid format: YYYY-MM-DDThh:mm:ssZ. If the specified `ss` is not 00, it is auto set to start of the next minute.|
|EndTime|String|Yes|The end time of the retrieved data, which is represented according to ISO8601, and UTC is required. Valid format: YYYY-MM-DDThh:mm:ssZ.  If the specified `ss` is not 00, it is auto set to start of the next minute.|
|Period|Integer|No|The interval of the retrieved monitoring data, unit: second.  Optional values:-   60
-   600
-   3600

Default value: 60.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|MonitorData|[InstanceMonitorDataType](intl.en-US/API Reference/Data type/InstanceMonitorDataType.md#)|A collection composed of instance monitoring data InstanceMonitorDataType.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceMonitorData
&InstanceId=i-instnace1
&StartTime=2014-10-29T23:00:00Z
&EndTime=2014-10-30T08:00:00Z
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeInstanceMonitorDataResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
    <MonitorData>
        <InstanceMonitorData>
            <InstanceId>Bc0102-23xYm09</InstanceId>
            <CPU>2</CPU>
            <IntranetRX>122</IntranetRX>
            <IntranetTX>343</IntranetTX>
            <IntranetFlow>675</IntranetFlow>
            <IntranetBandwidth>10</IntranetBandwidth>
            <InternetRX>122</InternetRX>
            <InternetTX>343</InternetTX>
            <InternetFlow>675</InternetFlow>
            <InternetBandwidth>10</InternetBandwidth>
            <IOPSRead>1000</IOPSRead>
            <IOPSWrite>200</IOPSWrite>
            <BPSRead>1000</BPSRead>
            <BPSWrite>200</BPSWrite>
            <TimeStamp>2010-01-21T09:50:23Z</TimeStamp>
        </InstanceMonitorData>
    </MonitorData>
</DescribeInstanceMonitorDataResponse>
```

 **JSON format** 

```

    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9",
    "Monitoring Data ":{
        "InstanceMonitorData": [{
            "InstanceId": "Bc0102-23xYm09",
            "CPU": 0,
            "IntranetRX": 122,
            "IntranetTX": 343,
            "IntranetFlow": 675,
            "IntranetBandwidth": 10,
            "InternetRX": 122,
            "InternetTX": 343,
            "InternetFlow": 675,
            "InternetBandwidth": 10,
            "IOPSRead": 1000,
            "IOPSWrite": 200,
            "BPSRead": 1000,
            "BPSWrite": 200,
            "TimeStamp": "2010-01-21T09:50:23Z"
        
    }

```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|
|InvalidStartTime.Malformed|The specified parameter “StartTime” is not valid.|400|The specified format of the `StartTime` format is incorrect.|
|InvalidEndTime.Malformed|The specified parameter “EndTime” is not valid.|400|The specified `EndTime`  is invalid.|
|InvalidPeriod.ValueNotSupported|The specified parameter “Period” is not valid.|400|The specified `Period`  is invalid.|
|InvalidStartTime.TooEarly|The specified parameter “StartTime” is too early.|400|The indicated `StartTime` must be 30 days later than the current time.|
|InvalidParameter.TooManyDataQueried|Too many data queried.|400|You can only query up to 400 entries of monitoring data each time.|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|Your request is denied due to request throttling. Please try again later.|

