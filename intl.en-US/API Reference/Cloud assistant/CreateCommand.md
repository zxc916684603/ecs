# CreateCommand {#CreateCommand .reference}

Creates a command. You can perform the command by using cloud assistant.

## Description {#section_iyx_fl4_ydb .section}

-   You can only create commands of the following types:
    -   Bat scripts for Windows instances \(`RunBatScript`\).
    -   PowerShell scripts for Windows instances \(`RunPowerShellScript`\).
    -   Shell scripts for Linux instances \(`RunShellScript`\).
-   You can specify the `TimeOut` parameter to set the maximum timeout value for command invocation on ECS instances. When the command invocation times out, the [client](../reseller.en-US/User Guide/Cloud assistant/Cloud assistant client.md#) forces the command process to stop.
    -   For one-time invocation, after an invocation timeout, the command invocation status \([`InvokeRecordStatus`](reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#InvokeRecordStatusRequest)\) for the specified ECS instance becomes `Failed`.
    -   For periodical invocation:
        -   The timeout value of periodical invocation is effective for every invocation record.
        -   After one invocation operation times out, the status for the invocation record \([`InvokeRecordStatus`](reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#InvokeRecordStatusRequest)\) becomes `Failed`.
        -   The timeout status of last invocation does not affect the next invocation.
-   You can specify the `WorkingDir` parameter to specify the invocation path of the command. For Linux instances, commands are performed in the `/root` directory by default. For Windows instances, commands are performed in the directory where the cloud assistant client process is located, such as `C:\ProgramData\aliyun\assist\$(version)`.
-   You can create 100 commands at maximum under a Alibaba Cloud Region.

    **Note:** If you require a higher quota of commands, please submit a ticket to apply for.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CreateCommand.|
|RegionId|String|Yes|The region ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|Name|String|Yes|Command name. Supporting all the character encoding sets.|
|Type|String|Yes|Command type. RunBatScript: Creates a Bat script for Windows instances. RunPowerShellScript: Creates a PowerShell script for Windows instances. RunShellScript: Creates a Shell script for Linux instances. Optional values:-   RunBatScript: Creates a Bat script for Windows instances.
-   RunPowerShellScript: Creates a PowerShell script for Windows instances.
-   RunShellScript: Creates a Shell script for Linux instances.

|
|Description|String|No|Command description. Supporting all the character encoding sets.|
|CommandContent|String|No|The Base64-encoded content of the command. You must pass in this parameter at the same time when you pass in the `Type` request parameter. The parameter value must be Base64-encoded for transmission and the script content size before the Base64 encoding cannot exceed 16 KB.|
|WorkingDir|String|No|The directory where your created command runs on the ECS instances. Default value:-   For Linux instances, commands are performed in the `/root` directory.
-   For Windows instances, commands are performed in the directory where the cloud assistant client process is located, such as `C:\ProgramData\aliyun\assist\$(version)`.

|
|TimeOut|Integer|No|The invocation timeout value of the command. The unit is seconds. When the command fails to run for some reason, the invocation may time out, after which the cloud assistant client forces the command process to stop by canceling the command PID. The parameter value must be greater than or equal to `60`. If the value is smaller than `60`, the timeout value is 60 seconds by default.Default value: 3600.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|CommandId|String|Command ID.|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=CreateCommand
&RegionId=cn-hangzhou
&Name=Test
&Type=RunShellScript
&CommandContent=ZWNobyAxMjM=
&<Common Request Parameters>
```

**Success response example**

**XML format**

```
<CreateCommandResponse>
    <RequestId>540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx</RequestId>
    <CommandId>c-e996287206324975b5fbe1dxxxxxxxxx</CommandId>
</CreateCommandResponse>
```

**JSON format**

```
{
    "RequestId":"540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx",
    "CommandId":"c-e996287206324975b5fbe1dxxxxxxxxx"
}
```

**Error response example**

**XML format** 

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.Name</Code>
    <Message>The input parameter “Name” that is required for processing this request is not supplied.</Message>
</Error>
```

**JSON format**

```

    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.Name"
    "Message": "The input parameter “Name” that is required for processing this request is not supplied."

```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|Invalid.CommandContent|The specified CommandContent is not valid or exceed max|400|The specified `CommandContent` parameter is invalid. Or the `CommandContent` value exceeds 16 KB.|
|MissingParameter.Name|The input parameter “Name” that is required for processing this request is not supplied.|400|You must specify the required parameter `Name`.|
|MissingParameter.RegionId|The input parameter “RegionId” that is required for processing this request is not supplied.|400|You must specify the required parameter `RegionId`. Or you cannot use the resources in the specified region.|
|MissingParameter.Type|The input parameter “Type” that is required for processing this request is not supplied.|400|You must specify the required parameter `Type`.|
|InvalidCmdType.NotFound|The specified command type does not exist|404|The specified `Type` parameter does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId` does not exist.|
|InternalError.Dispatch|An internal error occurred when dispath the request|500|Internal error. Please try again later.|

