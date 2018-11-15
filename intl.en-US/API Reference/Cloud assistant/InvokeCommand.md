# InvokeCommand {#InvokeCommand .reference}

Performs a specified command on one or more ECS instances.

## Description {#section_amn_fm4_ydb .section}

When you call this interface, consider the following:

-   The network type of the specified instances must be VPC.
-   The target ECS instance must be in the **Running** \(`Running`\) status.
-   The target ECS instance must have the [cloud assistant client](../reseller.en-US/User Guide/Cloud Assistant Client.md#) installed in advance.
-   To perform a PowerShell command, make sure that the target Windows ECS instance has been configured with the PowerShell module.
-   For one-time invocation \(`Timed=False`\), the command is performed only once.
-   For periodical invocation \(`Timed=True`\), the first invocation task starts at the time specified in the `Frequency` parameter. Subsequent invocations follow the frequency specified in the `Frequency` parameter. The result of last invocation does not affect the next invocation.
-   The scheduled time for periodical invocation is in UTC +08:00, and based on the system time of ECS instances. Make sure that the time on your ECS instances are consistent with your expectation.
-   You can specify multiple ECS instances in the InstanceIds. When one of these instances does not comply with the invocation conditions, you can try again by specifying other instances.
-   Command invocation may fail because of target instance status exception, network exception or cloud assistant client exception. No invocation information is generated for invocation failures.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: InvokeCommand.|
|RegionId|String|Yes|The region ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceIds|Array|Yes|List of instances for command invocation. The parameter value is a formatted JSON array in the format of \[`InstanceId1`, `instanceId2`, …\]. You can specify a maximum of 100 instance IDs separated by commas \(,\).|
|CommandId|String|Yes.|Command ID. You can call the [DescribeCommands](reseller.en-US/API Reference/Cloud assistant/DescribeCommands.md#) API to check all the available `CommandId`.|
|Timed|Boolean|No|Whether the command is periodically performed or not. Optional values:-   True: Periodical invocation.
-   False: Non-periodical invocation.

Default value: False|
|Frequency|String|No|The invocation period of a periodical task. When the [`Timed`](#Timed) parameter value is `True`, the `Frequency` parameter is required.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InvokeId|String|Command invocation ID.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=InvokeCommand
&RegionId=cn-hangzhou
&InstanceIds=i-bp185dy2o3o6nxxxxxxx
&CommandId=c-e996287206324975b5fbe1dxxxxxxxxx
&Timed=true
&Frequency=0 0-5 14 * * ?
&<Common Request Parameters>
```

**Success response example** 

**XML format**

```
<InvokeCommandResponse>
    <RequestId>540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx</RequestId>
    <InvokeId>t-1fad2a8876de47068cc734d5xxxxxxxxx</InvokeId>
</InvokeCommandResponse>
```

**JSON format**

```
{
    "RequestId":"540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx",
    "InvokeId":"t-1fad2a8876de47068cc734d5xxxxxxxxx"
|
```

**Error response example** 

**XML format**

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.CommandId</Code>
    <Message>The input parameter “CommandId” that is mandatory for processing this request is not supplied.</Message>
</Error>
```

**JSON format**

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.CommandId"
    "Message": "The input parameter “CommandId” that is mandatory for processing this request is not supplied."
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|InvalidInstance.NoClient|The specified instances have no cloud assistant client installed.|400|The target ECS instance must have the cloud assistant client installed in advance. For more information, see [Cloud assistant client](../reseller.en-US/User Guide/Cloud Assistant Client.md#).|
|InvalidInstance.NotVpc|The specified instances must be VPC instances.|400|The network type of the specified `InstanceIds` must be VPC.|
|InvalidInstanceStatus|The specified instance’s status can not execute this operation|400|The specified instance must be in the Running status. Or the specified instance has abnormal network connection.|
|MissingParameter.CommandId|The input parameter “CommandId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `CommandId`.|
|MissingParameter.InstanceIds|The input parameter “InstanceIds” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `InstanceIds`.|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `RegionId`. Or you cannot use the resources in the specified `RegionId`.|
|MissingParameter.Frequency|The frequency parameter must exist when create a timed Invocation.|400|When the `Timed` parameter value is `True`, the `Frequency` parameter is required.|
|InvalidCmdId.NotFound|The specified commandId does not exist.|404|The specified `CommandId` does not exist.|
|InvalidInstance.NotFound|The specified instances does not exist.|404|The specified `InstanceId` does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId` does not exist.|
|InternalError.Dispatch|An internal error occurred when dispatching your request.|500|Internal error. Please try again later.|

