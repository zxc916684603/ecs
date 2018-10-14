# DescribeInvocations {#DescribeInvocations .reference}

Queries the cloud assistant command invocation list and status on your ECS instances.

## Description {#section_n1g_w44_ydb .section}

When the `InvokeStatus` value is `Finished`, it indicates that the command process is Finished, but not necessarily is as effective as expected. You can check the specific invocation result by calling [DescribeInvocationResults](reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#).

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInvocations.|
|RegionId|String|Yes|The region ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InvokeId|String|No|Invocation ID of a command process.|
|CommandId|String|No|Command ID. You can query all the available `CommandId` by calling the [DescribeCommands](reseller.en-US/API Reference/Cloud assistant/DescribeCommands.md#).|
|CommandName|String|No|Name of the command.|
|Type|String|No|Type of the command. Optional values:-   RunBatScript: A Bat script for Windows instances.
-   RunPowerShellScript: A PowerShell script for Windows instances.
-   RunShellScript: A Shell script for Linux instances.

|
|Timed|Boolean|No|Whether the command is periodically performed or not. Optional values:-   True: Periodical invocation.
-   False: Not periodical invocation.

Default value: False.|
|InvokeStatus|String|No|Specifies the overall invocation status of a command. The overall invocation status is depends on the invocation status of command processes on all target instances. Optional values:-   Running: The command process is running.
    -   **Periodical invocation**: Before you manually stop a command on periodical invocation, the command process is always in the **Running** \(`Running`\) status.
    -   **One-time invocation**: The overall invocation status is **Running** \(`Running`\), as long as the command process is in the **Running** \(`Running`\) status on any target instance.
-   Finished: The invocation of the command process is completed.
    -   **Periodical invocation**: The command process can never be in the **Finished** \(`Finished`\) status.
    -   **One-time invocation**: When invocation of command processes on all the target instances managed by the specified command is completed, the overall invocation status is **Finished** \(`Finished`\).

Or when you manually stop the invocation of command processes on some target instances \(`Stopped`\) and the invocation on other target instances is completed, the overall invocation status is **Finished** \(`Finished`\).

-   Failed: The command process invocation failed, the command process timed out, or encountered other exceptions.
    -   **Periodical invocation**: The command process can never be in the **Failed** \(`Failed`\) status.
    -   **One-time invocation**: When invocation of command processes on all the target instances managed by the specified command fails, the overall invocation status is **Failed** \(`Failed`\).
-   PartialFailed: Part of the invocation of command processes failed.
    -   **Periodical invocation**: The command process can never be in the **PartialFailed** \(`PartialFailed`\) status.
    -   **One-time invocation**: The overall invocation status is **PartialFailed** \(`PartialFailed`\) when any command process is in the **Failed** \(`Failed`\) status on any target instance managed by the specified command.
-   Stopped: The command process is manually stopped.

|
|InstanceId|String|No|Instance ID. When you pass in the parameter, the system queries the invocation-record status of all commands on the instance.|
|PageNumber|Integer|No|Current page number. Start value: 1.Default value: 1.

|
|PageSize|Integer|No|The number of rows per page for multi-page display. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|Total number of commands.|
|PageNumber|Integer|Page number of the query result.|
|PageSize|Integer|The number of rows per page.|
|Invocations|Array of [`InvocationSetType`](#)|Type of the command invocation record set.|

 **Type of the command invocation record set \(InvocationSetType\)** 

|Name|Type|Description|
|:---|:---|:----------|
|Invocation|Array of [`InvocationType`](#)|Command invocation type.|

 **Command invocation type \(InvocationType\)** 

|Name|Type|Description|
|:---|:---|:----------|
|InvokeId|String|Command invocation ID.|
|CommandId|String| Command ID.|
|CommandName|String|Command name.|
|InvokeStatus|String|Specifies the overall invocation status of a command. The overall invocation status is dependent on the invocation status of command processes on all the target instances. `InstanceInvokeStatus`. Optional values:-   Running: The command process is running.
    -   **Periodical invocation**: Before you manually stop a command on periodical invocation, the command process is always in the **Running** \(`Running`\) status.
    -   **One-time invocation**: The overall invocation status is **Running** \(`Running`\), as long as the command process is in the **Running** \(`Running`\) status on any target instance.
-   Finished: The invocation of the command process is completed.
    -   **Periodical invocation**: The command process can never be in the **Finished** \(`Finished`\) status.
    -   **One-time invocation**: When invocation of command processes on all the target instances managed by the specified command is completed, the overall invocation status is **Finished** \(`Finished`\).

Or when you manually stop the invocation of command processes on some target instances **Stopped** \(`Stopped`\), and the invocation on other target instances is completed, the overall invocation status is **Finished** \(`Finished`\).

-   Failed: The command process invocation failed, the command process timed out, or encountered other exceptions.
    -   **Periodical invocation**: The command process can never be in the **Failed** \(`Failed`\) status.
    -   **One-time invocation**: When invocation of command processes on all the target instances managed by the specified command fails, the overall invocation status is **Failed** \(`Failed`\).
-   PartialFailed: Part of the invocation of command processes failed.
    -   **Periodical invocation**: The command process can never be in the **PartialFailed** \(`PartialFailed`\) status.
    -   **One-time invocation**: The overall invocation status is **PartialFailed** \(`PartialFailed` \) when any command process is in the **Failed** \(`Failed`\) status on any target instance managed by the specified command.
-   Stopped: The command process is manually stopped.

|
|CommandType|String|Command type|
|Timed|Boolean|Whether the command is periodically performed or not.|
|Frequency|String|The interval of a periodical task. |
|InvokeInstances|Array of [`InvokeInstanceSetType`](#)|Type of the target instance set for invocation.|

 **Type of the target instance set for invocation \(InvokeInstanceSetType\)** 

|Name|Type|Description|
|:---|:---|:----------|
|InvokeInstance|Array of [`InvokeInstanceType`](#)|Invocation status type of the target instance.|

 **Invocation status type of the target instance \(InvokeInstanceType\)** 

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|Instance ID.|
|InstanceInvokeStatus|String|The command process status of the specified instance.-   Running: The command process is running.
    -   **Periodical invocation**: Before you manually stop a command on periodical invocation, the command process is always in the **Running** \(`Running` \) status.
    -   **One-time invocation**: The command process status on the specified instance is **Running** \(`Running`\).
-   Finished: The invocation of the command process is completed.
    -   **Periodical invocation**: The command process can never be in the **Finished** \(`Finished`\) status.
    -   **One-time invocation**: The command process status on the specified instance is **Finished** \(`Finished`\).
-   Failed: The command process invocation failed, the command process timed out, or encountered other exceptions.
    -   **Periodical invocation**: The command process can never be in the **Failed** \(`Failed`\) status.
    -   **One-time invocation**: The command process status on the specified instance is **Failed** \(`Failed`\).
-   Stopped: The command process is manually stopped.

|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInvocations
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Success response example** 

**XML format** 

```
<DescribeInvocationsResponse>
    <TotalCount>5</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>10</PageSize>
    <Invocations>
        <Invocation>
                <InvokeStatus>Running</InvokeStatus>
                <InvokeId>t-a8935b93739442e59ed621a6xxxxxxxx</InvokeId>
                <CommandName>Test1</CommandName>
                <CommandType>RunShellScript</CommandType>
                <Frequency>0 */20 * * * *</Frequency>
                <InvokeInstances>
                    <InvokeInstance>
                        <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>finished</InstanceInvokeStatus>
                    </InvokeInstance>
                    <InvokeInstance>
                        <InstanceId>i-uf64isakb713xxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>running</InstanceInvokeStatus>
                    </InvokeInstance>
                </InvokeInstances>
                <Timed>True</Timed>
                <CommandId>c-e67505b2be3e477dae94c0f0xxxxxxxx</CommandId>
        </Invocation>
        <Invocation>
                <InvokeStatus>Running</InvokeStatus>
                <InvokeId>t-001937b74e2a4242891fc789xxxxxxxx</InvokeId>
                <CommandName>Test2</CommandName>
                <CommandType>RunShellScript</CommandType>
                <Frequency>0 */15 * * * *</Frequency>
                <InvokeInstances>
                    <InvokeInstance>
                    <InstanceId>i-mbhsiukj851xxxxjk</InstanceId>
                        <InstanceInvokeStatus>finished</InstanceInvokeStatus>
                    </InvokeInstance>
                    <InvokeInstance>
                        <InstanceId>i-uf64isakb713xxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>Running</InstanceInvokeStatus>
                    </InvokeInstance>
                </InvokeInstances>
                <Timed>True</Timed>
                <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
        </Invocation>
        <Invocation>
                <InvokeStatus>success</InvokeStatus>
                <InvokeId>t-bd09beef975b4e50883e5df1xxxxxxxx</InvokeId>
                <CommandName>Test3</CommandName>
                <CommandType>RunShellScript</CommandType>
                <Frequency> </Frequency>
                <InvokeInstances>
                    <InvokeInstance>
                        <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>finished</InstanceInvokeStatus>
                    </InvokeInstance>
                    sa<InvokeInstance>
                        <InstanceId>i-uf64isakb713xxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>finished</InstanceInvokeStatus>
                    </InvokeInstance>
                </InvokeInstances>
                <Timed>false</Timed>
                <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
        </Invocation>
        <Invocation>
                <InvokeStatus>Success</InvokeStatus>
                <InvokeId>t-c7499dfdfdb44e8aa0acce5bxxxxxxxx</InvokeId>
                <CommandName>test</CommandName>
                <CommandType>RunShellScript</CommandType>
                <Frequency> </Frequency>
                <InvokeInstances>
                    <InvokeInstance>
                        <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
                        <InstanceInvokeStatus>finished</InstanceInvokeStatus>
                    </InvokeInstance>
                </InvokeInstances>
                <Timed>false</Timed>
                <CommandId>c-d2a8ccf6440641ec8635f194xxxxxxxx</CommandId>
        </Invocation>
        <InstanceId>Invention>
                <InvokeStatus>Running</InvokeStatus>
                <InvokeId>t-e733d4172fee452c98106f58xxxxxxxx</InvokeId>
                <CommandName>Test4</CommandName>
                <CommandType>RunBatScript</CommandType>
                <Frequency> </Frequency>
                <InvokeInstances>
                    <InvokeInstance>
                        <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
                        <Instanceinvokestatus> running </instanceinvokestatus>
                    </InvokeInstance>
                </InvokeInstances>
                <Timed>false</Timed>
                <CommandId>c-3f0e5e4a21c045afa197e036xxxxxxxx</CommandId>
        </Invocation>
    </Invocations>
    <RequestId>12E7974A-5AA5-4933-A44C-A16Cxxxxxxxx</RequestId>
</DescribeInvocationsResponse>
```

**JSON format** 

```
{
    "TotalCount": 5,
    "PageNumber": 1,
    "PageSize": 10,
    "Invocations": {
        "Invocation": [
            {
                "InvokeStatus": "Running",
                "InvokeId": "t-a8935b93739442e59ed621a6xxxxxxxx",
                "CommandName": "Test1",
                "CommandType": "RunShellScript",
                "Frequency": "0 */20 * * * *",
                "InvokeInstances": {
                    "InvokeInstance": [
                        {
                            "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                            "InstanceInvokeStatus": "finished"
                        },
                        {
                            "InstanceId": "i-uf64isakb713xxxxxxxx",
                            "InstanceInvokeStatus": "running"
                        }
                    ]
                },
                "Timed": true,
                "CommandId": "c-e67505b2be3e477dae94c0f0xxxxxxxx"
            },
            {
                "InvokeStatus": "Running",
                "InvokeId": "t-001937b74e2a4242891fc789xxxxxxxx",
                "CommandName": "Test2",
                "CommandType": "RunShellScript",
                "Frequency": "0 */15 * * * *",
                "InvokeInstances": {
                    "InvokeInstance": [
                        {
                            "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                            "InstanceInvokeStatus": "finished"
                        },
                        {
                            "InstanceId": "i-uf64isakb713xxxxxxxx",
                            "InstanceInvokeStatus": "running"
                        }
                    ]
                },
                "Timed": true,
                "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx"
            },
            {
                "InvokeStatus": "success",
                "InvokeId": "t-bd09beef975b4e50883e5df1xxxxxxxx",
                "CommandName": "Test3",
                "CommandType": "RunShellScript",
                "Frequency": "",
                "InvokeInstances": {
                    "InvokeInstance": [
                        {
                            "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                            "InstanceInvokeStatus": "finished"
                        },
                        {
                            "InstanceId": "i-uf64isakb713xxxxxxxx",
                            "InstanceInvokeStatus": "finished"
                        }
                    ]
                },
                "Timed": false,
                "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx"
            },
            {
                "InvokeStatus": "success",
                "InvokeId": "t-c7499dfdfdb44e8aa0acce5bxxxxxxxx",
                "CommandName": "test",
                "CommandType": "RunShellScript",
                "Frequency": "",
                "InvokeInstances": {
                    "InvokeInstance": [
                        {
                            "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                            "InstanceInvokeStatus": "finished"
                        }
                    ]
                },
                "Timed": false,
                "CommandId": "c-d2a8ccf6440641ec8635f194xxxxxxxx"
            },
            {
                "InvokeStatus": "Running",
                "InvokeId": "t-e733d4172fee452c98106f58xxxxxxxx",
                "CommandName": "Test4",
                "CommandType": "RunBatScript",
                "Frequency": "",
                "InvokeInstances": {
                    "InvokeInstance": [
                        {
                            "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                            "InstanceInvokeStatus": "running"
                        }
                    ]
                },
                "Timed": false,
                "CommandId": "c-3f0e5e4a21c045afa197e036xxxxxxxx"
            }
        ]
    },
    "RequestId": "12E7974A-5AA5-4933-A44C-A16Cxxxxxxxx"
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

|Error code|Error message| HTTP status code| Meaning|
|:---------|:------------|:----------------|:-------|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter of `RegionId`, or you cannot use the resources in the specified `RegionId`.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId` does not exist.|
|InternalError.Dispatch|An internal error occurred when dispath the request|500|Internal error. Please try again later.|

