# StopInvocation {#StopInvocation .reference}

Stops cloud assistant command processes that are in **Running** \(`Running`\) status on ECS instances. When you call this interface, consider the following:

## Description {#section_ult_wm4_ydb .section}

-   After you stop a command process on one-time invocation, the invocation operations that have been started on instances proceed, and those that have not been started cease.
-   After you stop a command process on periodical invocation, the invocation operations that have been started on instances proceed, but the invocation does not proceed to the next period.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: StopInvocation.|
|RegionId|String|Yes|The region ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InvokeId|String|Yes|Invocation ID of a command process. You can call [DescribeInvocations](reseller.en-US/API Reference/Cloud assistant/DescribeInvocations.md#) to obtain the latest `InvokeId`.|
|InstanceIds|Array|No|List of instances for stopping command invocation. The parameter value is a formatted JSON array in the format of \[`InstanceId1`, `InstanceId2`, …\]. You can specify a maximum of 100 instance IDs separated by commas \(,\).|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. See [Common response parameters](../reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=StopInvocation
&RegionId=cn-hangzhou
&InvokeId=t-1fad2a8876de47068cc734d57703aa76
&<Common Request Parameters>
```

**Success response example** 

**XML format**

```
<StopInvocationResponse>
    <RequestId>540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx</RequestId>
</StopInvocationResponse>
```

 **JSON format** 

```
{
    "RequestId":"540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx",
}
```

**Error response example** 

** XML format** 

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>InvalidInstance.NoClient</Code>
    <Message>The specified instances have no cloud assistant client installed.</Message>
</Error>
```

 **JSON format** 

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com",
    "Code": "InvalidInstance.NoClient",
    "Message": "The specified instances have no cloud assistant client installed."
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidInvokeId.NotFound|The specified ImageId does not exist.|400|The specified `InvokeId`does not exist.|
|MissingParameter.InstanceId|The input parameter “InstanceIds” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter of InstanceIds.|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter of `RegionId`. Or you cannot use the resources in the specified region.|
|MissingParameter.InvokeId|The input parameter “InvokeId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `InvokeId`.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId`does not exist.|
|InternalError.Dispatch|An internal error occurred when dispath the request|500|Internal error, please try later.|

