# DescribeEniMonitorData {#DescribeEniMonitorData .reference}

Queries data connection information about a secondary ENI over a specific period.

## Description {#BestPractice .section}

The queriable traffic data on the secondary ENI traffic data includes intranet inbound and outbound traffic, the number of packets sent and received by the secondary ENI, and the number of packets discarded by the secondary ENI. If some content in the returned information is missing, it is possible that the system did not obtain the corresponding information. For example, the traffic data on the secondary ENI cannot be queried if the instance is in the **Stopped** status \(`Stopped`\). Data also cannot be queried if the secondary ENI is not mounted to an instance and in the **Available** status\(`Available`\). When you use this operation, consider the following:

-   Each query can return up to 400 entries of monitoring data. If \(EndTime - StartTime\)/Period \> 400, an error is returned.
-   You can use a single query to search for monitoring data in the last 30 days. If the value of the StartTime parameter is more than 30 days, an error is returned.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: DescribeEniMonitorData.|
|InstanceId|String |Yes|Instance ID that is bound to the secondary ENI.|
|Enild|String|No|Secondary ENI ID. All secondary ENIs that are bound to the instance are queried by default.|
|StartTime|String|Required|The start time of the monitoring data to be retrieved. The time format follows the [ISO8601](../intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.If the specified number of seconds \(`ss`\) is not `00`, the time will be automatically rounded up to the next minute.|
|EndTime|String|Yes|The end time of the monitoring data. The time format follows the [ISO8601](../intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.If the specified number of seconds \(`ss`\) is not `00`, the time will be automatically rounded up to the next minute.|
|Period|Integer|Optional|Period of the retrieved monitoring data. Unit: second. Value range: 60 | 600 | 3600Default value: 60.

|

## Response parameters {#ResponseParameter .section}

|Name |Type|Description|
|:----|:---|:----------|
|MonitorData|[EniMonitorDataType](https://lark.alipay.com/docs/share/983c4182-3f3f-48d5-9615-6a214f9568e2)|The set of monitoring data EniMonitorDataTypefor a secondary ENI.|

**Data type of EniMonitorDataType**

|Name|Type|Description|
|:---|:---|:----------|
|Enild|String|Secondary ENI ID.|
|TimeStamp|String|Traffic query timestamp.The time format follows the [ISO8601](../intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|PacketTX|String|Number of intranet data packets sent by the secondary ENI.|
|PacketRX|String|Number of intranet data packets received by the secondary ENI.|
|IntranetTX|String|Intranet data traffic sent by the secondary ENI, in kbits.|
|IntranetRX|String|Intranet data traffic received by the secondary ENI, in kbits.|
|DropPacketTX|String|Number of discarded intranet data packets sent by the secondary ENI.|
|DropPacketRX|String|Number of discarded intranet data packets received by the secondary ENI.|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=DescribeEniMonitorData
&amp;EniId=eni-myENI
&amp;InstanceId=myInstance
&amp;StartTime=2018-05-21T12:19:00Z
&amp;EndTime=2018-05-21T12:22:00Z
&amp;&lt;Common Request Parameters>
```

**Response examples**

**XML format**

```
&lt;DescribeEniMonitorDataResponse>
 &lt;RequestId>5A03C2BA-3BCE-4A87-8076-7DC1629&lt;/RequestId>
 &lt;TotalCount>4&lt;/TotalCount>
 &lt;MonitorData>
     &lt;EniMonitorData>
         &lt;PacketTx>0&lt;/PacketTx>
         &lt;TimeStamp>2018-05-21T03:22:00Z&lt;/TimeStamp>
         &lt;IntranetOut>0&lt;/IntranetOut>
         &lt;DropPacketRx>0&lt;/DropPacketRx>
         &lt;IntranetIn>0&lt;/IntranetIn>
         &lt;EniId>eni-myENI&lt;/EniId>
         &lt;DropPacketTx>0&lt;/DropPacketTx>
         &lt;PacketRx>0&lt;/PacketRx>
     &lt;/EniMonitorData>
     &lt;EniMonitorData>
         &lt;PacketTx>0&lt;/PacketTx>
         &lt;TimeStamp>2018-05-21T03:21:00Z&lt;/TimeStamp>
         &lt;IntranetOut>0&lt;/IntranetOut>
         &lt;DropPacketRx>0&lt;/DropPacketRx>
         &lt;IntranetIn>0&lt;/IntranetIn>
         &lt;EniId>eni-myENI&lt;/EniId>
         &lt;DropPacketTx>0&lt;/DropPacketTx>
         &lt;PacketRx>0&lt;/PacketRx>
     &lt;/EniMonitorData>
     &lt;EniMonitorData>
         &lt;PacketTx>52240&lt;/PacketTx>
         &lt;TimeStamp>2018-05-21T03:19:00Z&lt;/TimeStamp>
         &lt;IntranetOut>73344&lt;/IntranetOut>
         &lt;DropPacketRx>0&lt;/DropPacketRx>
         &lt;IntranetIn>467&lt;/IntranetIn>
         &lt;EniId>eni-myENI&lt;/EniId>
         &lt;DropPacketTx>0&lt;/DropPacketTx>
         &lt;PacketRx>6603&lt;/PacketRx>
     &lt;/EniMonitorData>
     &lt;EniMonitorData>
         &lt;PacketTx>34925&lt;/PacketTx>
         &lt;TimeStamp>2018-05-21T03:20:00Z&lt;/TimeStamp>
         &lt;IntranetOut>48871&lt;/IntranetOut>
         &lt;DropPacketRx>0&lt;/DropPacketRx>
         &lt;IntranetIn>350&lt;/IntranetIn>
         &lt;EniId>eni-myENI&lt;/EniId>
         &lt;DropPacketTx>0&lt;/DropPacketTx>
         &lt;PacketRx>4888&lt;/PacketRx>
     &lt;/EniMonitorData>
 &lt;/MonitorData>
&lt;/DescribeEniMonitorDataResponse>
```

**JSON format**

```
{
 "RequestId":"5A03C2BA-3BCE-4A87-8076-7DC1629",
 "MonitorData":{
     "EniMonitorData":[
         {
             "PacketTx":0,
             "TimeStamp":"2018-05-21T03:22:00Z",
             "IntranetOut":0,
             "DropPacketRx":0,
             "IntranetIn":0,
             "EniId":"eni-myENI",
             "DropPacketTx":0,
             "PacketRx":0
         },
         {
             "PacketTx":0,
             "TimeStamp":"2018-05-21T03:21:00Z",
             "IntranetOut":0,
             "DropPacketRx":0,
             "IntranetIn":0,
             "EniId":"eni-myENI",
             "DropPacketTx":0,
             "PacketRx":0
         },
         {
             "PacketTx":52240,
             "TimeStamp":"2018-05-21T03:19:00Z",
             "IntranetOut":73344,
             "DropPacketRx":0,
             "IntranetIn":467,
             "EniId":"eni-myENI",
             "DropPacketTx":0,
             "PacketRx":6603
         },
         {
             "PacketTx":34925,
             "TimeStamp":"2018-05-21T03:20:00Z",
             "IntranetOut":48871,
             "DropPacketRx":0,
             "IntranetIn":350,
             "EniId":"eni-myENI",
             "DropPacketTx":0,
             "PacketRx":4888
         }
     ]
 }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Description|
|:---------|:-------------|:---------------|:----------|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceId does not exist.|
|InvalidStartTime.Malformed|The specified parameter “StartTime” is not valid.|400|The specified parameter StartTime is invalid.|
|InvalidEndTime.Malformed|The specified parameter “EndTime” is not valid.|400|The specified parameter EndTime is invalid.|
|InvalidPeriod.ValueNotSupported|The specified parameter “Period” is not valid.|400|The specified parameter Period is invalid.|
|InvalidStartTime.TooEarly|The specified parameter “StartTime” is too early.|400|The specified StartTime must be within 30 days of the current day.|
|InvalidParameter.TooManyDataQueried|Too many data queried.|400|Attempted to query too much data. You can only query up to 400 entries of monitored data at a time.|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|Your request is denied due to request throttling. Try again later.|

