# DeleteCommand {#DeleteCommand .reference}

Deletes a created cloud assistant command. The log of the original invocation is retained after a command is deleted.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteCommand.|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|CommandId|String|Yes|Command ID. You can query all the available CommandId by calling the [DescribeCommands](reseller.en-US/API Reference/Cloud assistant/DescribeCommands.md#).|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. See [Common response parameters](../reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteCommand
&RegionId=cn-hangzhou
&InvokeId=c-f0902c0972984e31aaf2129fd48a9c6d
&<Common Request Parameters>
```

**Success response example** 

**XML format**

```
<DeleteCommandResponse>
    <RequestId>540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx</RequestId>
</DeleteCommandResponse>
```

**JSON format** 

```
{
    "RequestId":"540CFF28-407A-40B5-B6A5-73Bxxxxxxxxx",
}
```

**Error response example** 

**XML format**

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
    "HostId": "ecs.aliyuncs.com"
    "Code": "InvalidInstance.NoClient"
    "Message": "The specified instances have no cloud assistant client installed."
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidCmdId.NotFound|The specified ImageId does not exist.|404|The specified CommandId does not exist.|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|The specified RegionId does not exist.|
|Internalerror. Dispatch|An internal error occurred when dispath the request|500|Internal error. Please try again later.|

