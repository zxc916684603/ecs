# DescribeCommands {#DescribeCommands .reference}

Queries the cloud assistant commands that you have created. If you only specify the `Action` and `RegionId` parameters, Alibaba Cloud ECS queries all your available commands \(`CommandId`\) by default.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeCommands.|
|RegionId|String|Yes|The region ID. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|CommandId|String|No|Command ID.|
|Type|String|No|Command type. Optional values:-   RunBatScript: The command process is a Bat script for Windows instances.
-   RunPowerShellScript: The command process is a PowerShell script for Windows instances.
-   RunShellScript: The command process is a Shell script for Linux instances.

|
|Name|String|No|Command name, fuzzy search temporarily not supported.|
|Description|String|No|Command description, fuzzy search temporarily not supported.|
|PageNumber|Integer|No|Current page number. Start value: 1.Default value: 1.

|
|PageSize|Integer|No|The number of rows per page for multi-page display. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|Total number of commands.|
|Pagenumber|Integer|Command list page number.|
|Pagesize|Integer|The number of rows per page.|
|Commands|Array|Type of command data set \([`CommandSetType`](#CommandSetType)\).|

 **CommandSetType** 

|Name|Type|Description|
|:---|:---|:----------|
|Command|Array|Command type \([`CommandType`](#CommandType)\).|

 **CommandType** 

|Name|Type|Description|
|:---|:---|:----------|
|CommandId|String|Command ID.|
|Name|String|Command name.|
|Description|String|Command description.|
|Type|String|Command type.|
|Commandcontent|String|Command content, transmitted in the Base64-encoded format.|
|WorkingDir|String|Invocation path.|
|TimeOut|Integer|Timeout.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeCommands
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Success response example** 

**XML format**

```
<DescribeCommandsResponse>
    <TotalCount>5</TotalCount>
    <Commands>
        <Command>
                <Name>Test</Name>
                <WorkingDir></WorkingDir>
                <CommandContent>ZWNobyAxMjM=</CommandContent>
                <Timeout>3600</Timeout>
                <Type>RunShellScript</Type>
                <CommandId>c-05946950bc63441dab0a72b8xxxxxxxx</CommandId>
                <Description>test</Description>
        </Command>
        <Command>
                <Name>Test1</Name>
                <WorkingDir></WorkingDir>
                <CommandContent>Y2QgL3Jvb3Q=</CommandContent>
                <Timeout>3600</Timeout>
                <Type>RunShellScript</Type>
                <CommandId>c-53253cb556d74cb7b7f7309fdxxxxxxxx</CommandId>
                <Description>test1</Description>
        </Command>
        <Command>
                <Name>Test2</Name>
                <WorkingDir></WorkingDir>
                <CommandContent>eXVtIHVwZGF0ZQ==</CommandContent>
                <Timeout>3600</Timeout>
                <Type>RunShellScript</Type>
                <CommandId>c-57881b01e5ec4403916f8685xxxxxxxx</CommandId>
                <Description>test2</Description>
        </Command>
        <Command>
                <Name>Test3</Name>
                <WorkingDir></WorkingDir>
                <CommandContent>c2VydmljZSBuZ2lueCByZWxvYWQ=</CommandContent>
                <Timeout>3600</Timeout>
                <Type>RunShellScript</Type>
                <CommandId>c-742eea007af14043b07c4978xxxxxxxx</CommandId>
                <Description>test3</Description>
        </Command>
        <Command>
                <Name>Test4</Name>
                <WorkingDir></WorkingDir>
                <CommandContent>bHM=</CommandContent>
                <Timeout>120</Timeout>
                <Type>RunShellScript</Type>
                <CommandId>c-cec3ded3bc434c22aabcfeaaxxxxxxxx</CommandId>
                <Description>test4</Description>
        </Command>
    <PageNumber>1</PageNumber>
    <RequestId>36443468-4AE5-44DB-A6FE-A528xxxxxxxx</RequestId>
    <PageSize>10</PageSize>
</DescribeCommandsResponse>
```

 **JSON format** 

```
{
    "TotalCount": 5,
    "Commands": {
        "Command": [
            {
                "Name": "Test",
                "WorkingDir": "",
                "CommandContent": "ZWNobyAxMjM=",
                "Timeout": 3600,
                "Type": "RunShellScript",
                "CommandId": "c-05946950bc63441dab0a72b8xxxxxxxx",
                "Description": "test"
            },
            {
                "Name": "Test1",
                "WorkingDir": "",
                "CommandContent": "Y2QgL3Jvb3Q=",
                "Timeout": 3600,
                "Type": "RunShellScript",
                "CommandId": "c-53253cb556d74cb7b7f7309fxxxxxxxx",
                "Description": "test1"
            },
            {
                "Name": "Test2",
                "WorkingDir": "",
                "CommandContent": "eXVtIHVwZGF0ZQ==",
                "Timeout": 3600,
                "Type": "RunShellScript",
                "CommandId": "c-57881b01e5ec4403916f8685xxxxxxxx",
                "Description": "test2"
            },
            {
                "Name": "Test3",
                "WorkingDir": "",
                "CommandContent": "c2VydmljZSBuZ2lueCByZWxvYWQ=",
                "Timeout": 3600,
                "Type": "RunShellScript",
                "CommandId": "c-742eea007af14043b07c4978xxxxxxxx",
                "Description": "test3"
            },
            {
                "Name": "Test4",
                "WorkingDir": "",
                "CommandContent": "bHM=",
                "Timeout": 3600,
                "Type": "RunShellScript",
                "CommandId": "c-cec3ded3bc434c22aabcfeaaxxxxxxxx",
                "Description": "test4"
            },
        ]
    },
    "PageNumber": 1,
    "RequestId": "36443468-4AE5-44DB-A6FE-A528xxxxxxxx",
    "PageSize": 10
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

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `RegionId`, or you cannot use  the resources in the specified region.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified `RegionId` parameter does not exist.|
|InternalError.Dispatch|An internal error occurred when dispath the request|500|Internal error. Please try again later.|

