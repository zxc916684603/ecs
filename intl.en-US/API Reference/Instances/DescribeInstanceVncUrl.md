# DescribeInstanceVncUrl {#DescribeInstanceVncUrl .reference}

Queries the [management terminal URL](../../../../intl.en-US/User Guide/Connect/Terminal.md#) before connecting to an instance.

## Description {#section_nkr_mss_xdb .section}

When you call this interface, consider the following:

-   A management terminal URL is valid for 15 seconds. If a connection is not established within 15 seconds after a successful query, the URL expires and you must query it again.

-   The **KeepAlive** time of an individual management terminal connection is 60 seconds. If you do not interact with the management terminal window within 60 seconds, the connection is automatically closed.

-   If the connection is interrupted, you cannot reconnect for more than 30 times per minute.

-   At the end of the fixed URL [https://g.alicdn.com/aliyun/ecs-console-vnc/0.0.7/index.html?](https://g.alicdn.com/aliyun/ecs-console-vnc/0.0.7/index.html?), add `vncUrl=xxxx`, `instanceId=xxx`, `isWindows=True`, `isWindows=False` and `password=XXXXXX`, and use symbol `&` between the parameters. Wherein:

    -   Parameter `vncUrl`: The value of `VncUrl` is responded after calling the interface successfully.

    -   Parameter `instanceId`: The ID of your instance to which you are about to connect.

    -   Parameter `isWindows`: Whether the operating system of an instance is Windows or not. The value `true` indicates a Windows instance, and the value `false` indicates other operating system, for example, Linux.

    -   \(Optional\). Parameter `password`: The instance connection password in the Management Terminal. It consists of 6 numbers or uppercase/lowercase letters. This parameter eliminates the need to enter the password before the connection establishes.

          **Sample**:

        ```
        https://g.alicdn.com/aliyun/ecs-console-vnc/0.0.7/index.html?vncUrl=ws%3A%2F%xxx&instanceId=i-wz9hhwq5a6tmxxxxxxx&isWindows=true
        ```

        Or

        ```
        https://g.alicdn.com/aliyun/ecs-console-vnc/0.0.7/index.html?vncUrl=ws%3A%2F%xxx&instanceId=i-wz9hhwq5a6tmxxxxxxx&isWindows=true&Password=111111
        ```


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInstanceVncUrl|
|RegionId|String|Yes|The region ID of the instance. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|Yes|The ID of an instance.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|VncUrl|String|The management terminal URL|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceVncUrl
&RegionId=cn-qingdao
&InstanceId=AY121018033933eaxxxxxxx
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeInstanceVncUrlResponse>
    <RequestId>1450F2D7-5435-4420-BBC9-49C5xxxxxxxx</RequestId>
    <VncUrl>ws%3A%2F%2Fhz01-vncproxy.aliyun.com%2Fwebsockify%2F%3Fs%3DDvh%252FIA%252BYc73gWO48cBx2gBxUDVzaAnSKr74pq30mzqUYgeUMcB%252FbkNixDxdEA996</VncUrl>
</DescribeInstanceVncUrlResponse>
```

 **JSON format** 

```
{
    "RequestId": "1450F2D7-5435-4420-BBC9-49C514B0157E", 
    "VncUrl": "ws%3A%2F%2Fhz01-vncproxy.aliyun.com%2Fwebsockify%2F%3Fs%3DDvh%252FIA%252BYc73gWO48cBx2gBxUDVzaAnSKr74pq30mzqUYgeUMcB%252FbkNixDxdEA996"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The specified instance must be in the **Running**  status.|
|InstanceNotReady|The specified instance is not ready for use|403|The specified instance is being created. Please try again later.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

