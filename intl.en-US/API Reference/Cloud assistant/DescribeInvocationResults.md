# DescribeInvocationResults {#DescribeInvocationResults .reference}

Queries the invocation result of a cloud assistant command, that is, the actual `Output` information of a specified ECS instance.

## Description {#section_nlv_qq4_ydb .section}

After you use the [DescribeInvocations](reseller.en-US/API Reference/Cloud assistant/DescribeInvocations.md#) interface to check the command invocation status and the returned `InvokeStatus` is `Finished`, it indicates that the command process is Finished, but not necessarily is as effective as expected. You need to check the `Output` parameter in [DescribeInvocationResults](reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#) to get the specific invocation result. The actual output result is the valid version.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInvocationResults.|
|RegionId|String|Yes|The regional ID. For more information, see [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#).|
|CommandId|String|No|Command ID. For more information, call [DescribeRegions](../DNA0011839416/../DNA0011860945/reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|No|Instance ID.|
|InvokeId|String|No|Invocation ID of a command process. You can use the [DescribeInvocations](reseller.en-US/API Reference/Cloud assistant/DescribeInvocations.md#) API to check all the `InvokeId`.|
|InvokeRecordStatus|String|No|The status of the command process you want to query. Optional values:-   Running: The command process is running.
-   Failed: The command process invocation failed, the command process timed out, or encountered exceptions.
-   Finished: The invocation of the command process is completed.
-   Stopped: The command process is manually stopped.

|
|PageNumber|Integer|No|Current page number.Start value: 1.

|
|PageSize|Default value: 1.|No|The number of rows per page for multi-page display. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|Total number of commands.|
|Pagenumber|Integer|Page number of the query result.|
|Pagesize|Integer|The number of rows per page.|
|InvocationResults|Array|Command invocation result set \([`InvocationResultSetType`](#)\).|

**InvocationResultSetType**

|Name|Type|Description|
|:---|:---|:----------|
|Invocationresult|Array|Invocation result type on the instance \([`InvocationResultType`](#)\). Only one entry of result are returned for one-time invocation.|

**InvocationResultType**

|Name|Type|Description|
|:---|:---|:----------|
|CommandId|String|Command ID.|
|InvokeId|String|Invocation ID.|
|InstanceId|String|Instance ID.|
|FinishedTime|String|Time of command process completion. If a command process times out, the time of completion for the command process is based on [CreateCommand](reseller.en-US/API Reference/Cloud assistant/CreateCommand.md#) `TimedOut`.|
|Invokerecordstatus|String|Invocation status of the command process. Optional values:-   Running: The command process is running.
-   Failed: The command process invocation failed, the command process timed out, or encountered exceptions.
-   Finished: The invocation of the command process is completed.
-   Stopped: The command process is manually stopped.

|
|Output|String|The actual result after the command process completion. The output content is transmitted in the Base64-encoded format.|
|Exitcode|Integer|The exit code of the command process:-   The exit code is the Shell process exit code for Linux instances.
-   The exit code is the Bat or PowerShell process exit code for Windows instances.

|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=DescribeInvocationResults
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Success response example**

**XML format**

```
<DescribeInvocationResultsResponse>
    <TotalCount>5</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>5</PageSize>
    <Invocationresults>
    <Invocationresult>
            <FinishedTime>2018-01-05 15:45:02</FinishedTime>
            <Invokerecordstatus> finished </invokerecordstatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc789xxxxxxxx</InvokeId>
            <Output>MTU6NDU6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:40:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-a8935b93739442e59ed621a6xxxxxxxx</InvokeId>
            <Output> </Output>
            <CommandId>c-e67505b2be3e477dae94c0f0xxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:30:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc78xxxxxxxx</InvokeId>
            <Output>MTU6MzA6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:20:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-a8935b93739442e59ed621a6xxxxxxxx</InvokeId>
            <Output> </Output>
            <CommandId>c-e67505b2be3e477dae94c0f0xxxxxxxx</CommandId>
            <Exitcode> 0 </exitcode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:15:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc789xxxxxxxx</InvokeId>
            <Output>MTU6MTU6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        </InvocationResults>
    <RequestId>567FA138-6026-47C6-A299-5D50xxxxxxxx</RequestId>
</DescribeInvocationResultsResponse>
```

**JSON  format**

```
{
    "Invocation": {
        "TotalCount": 5,
        "PageNumber": 1,
        "InvocationResults": {
            "InvocationResult": [
                {
                    "FinishedTime": "2018-01-05 15:45:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-001937b74e2a4242891fc789xxxxxxxx",
                    "Output": "MTU6NDU6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:40:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-a8935b93739442e59ed621a6xxxxxxxx",
                    "Output": "",
                    "CommandId": "c-e67505b2be3e477dae94c0f0xxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:30:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-001937b74e2a4242891fc78xxxxxxxx",
                    "Output": "MTU6MzA6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:20:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmd3zj4k74",
                    "InvokeId": "t-a8935b93739442e59ed621a6xxxxxxxx",
                    "Output": "",
                    "CommandId": "c-e67505b2be3e477dae94c0f0xxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:15:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmd3zj4k74",
                    "InvokeId": "t-001937b74e2a4242891fc789xxxxxxxx",
                    "Output": "MTU6MTU6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                }
            ]
        },
        "PageSize": 5
    },
    "RequestId": "567FA138-6026-47C6-A299-5D50xxxxxxxx"
}
```

**Error response example**

**XML format**

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.RegionId</Code>
    <Message>The input parameter “RegionId” that is mandatory for processing this request is not supplied.</Message>
</Error>
```

**JSON format**

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.RegionId"
    "Message": "The input parameter “RegionId” that is mandatory for processing this request is not supplied."
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code |Meaning|
|:---------|:------------|:----------------|:------|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `RegionId`, or you cannot use the resources in the `RegionId`.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId` does not exist.|
|InternalError.Dispatch|An internal error occurred when dispatch the request.|500|Internal error. Please try again later.|

