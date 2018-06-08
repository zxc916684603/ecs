# DescribeCommands {#DescribeCommands .reference}

查询您已经创建的云助手命令。只输入参数 `Action` 和 `RegionId`，不输入其他任何请求参数，则默认查询您所有可用的命令（`CommandId`）。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeCommands|
|RegionId|String|是|地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|CommandId|String|否|命令 ID。|
|Type|String|否|命令的类型。取值范围：-   RunBatScript：命令为在 Windows 实例中运行的 Bat 脚本
-   RunPowerShellScript：命令为在 Windows 实例中运行的 PowerShell 脚本
-   RunShellScript：命令为在 Linux 实例中运行的 Shell 脚本

|
|Name|String|否|命令的名称，暂不支持模糊查询。|
|Description|String|否|命令的描述，暂不支持模糊查询。|
|PageNumber|Integer|否|当前页码，起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数，最大值：50默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|命令总个数|
|PageNumber|Integer|命令列表页码|
|PageSize|Integer|每页行数|
|Commands|Array|命令数据集类型（[`CommandSetType`](#CommandSetType)）|

 **数据集类型 CommandSetType** 

|名称|类型|描述|
|:-|:-|:-|
|Command|Array|命令类型（[`CommandType`](#CommandType)）|

 **命令类型 CommandType** 

|名称|类型|描述|
|:-|:-|:-|
|CommandId|String|命令 ID|
|Name|String|命令名称|
|Description|String|命令描述|
|Type|String|命令类型|
|CommandContent|String|命令内容，以 Base64 编码后传输|
|WorkingDir|String|执行路径|
|TimeOut|Integer|超时时间|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeCommands
&RegionId=cn-hangzhou
&<公共请求参数>
```

**正常返回示例** 

**XML 格式**

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
}
```

 **JSON 格式** 

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

**异常返回示例** 

**XML 格式**

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.RegionId</Code>
    <Message>The input parameter “RegionId” that is mandatory for processing this request is not supplied.</Message>
</Error>
```

 **JSON 格式** 

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.RegionId"
    "Message": "The input parameter “RegionId” that is mandatory for processing this request is not supplied."
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|您必须指定必需参数 `RegionId`，或者您暂时不能使用指定 `RegionId` 里的资源。|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|指定的参数 `RegionId`不存在。|
|InternalError.Dispatch|An internal error occurred when dispath the request|500|内部错误，请稍后尝试。|

