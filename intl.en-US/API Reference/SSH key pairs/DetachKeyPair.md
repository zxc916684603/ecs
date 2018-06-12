# DetachKeyPair {#DetachKeyPair .reference}

Detaches an SSH key pair from one or more of your Linux instances.

## Description {#section_a1k_4qn_ydb .section}

When you call this interface, consider the following:

-   After you detach an SSH key pair, restart the instance \([RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#)\) for the operation to take effect.

-   After the key pair is detached, the user name and password authentication method is used by default.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DetachKeyPair|
|RegionId|String|Yes|The ID of the region to which your SSH key pair belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|KeyPairName|String|Yes|The names of key pairs.|
|InstanceIds|String|No|The instance ID. The instance ID. The value can contain arrays of up to 50 instance IDs. The IDs are displayed in the format of \["i-xxxxxxxxx", "i-yyyyyyyyy", … "i-zzzzzzzzz"\] and separated by commas \(,\).|

## Return parameters {#section_f54_lk5_xdb .section}

All are common parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#).

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DetachKeyPair
&RegionId=cn-qingdao
&InstanceIds=["i-xxxxxxx", "i-yyyyyyy"]
&KeyPairName=test
&<Common Request Parameter>
```

**Response example** 

**XML format**

```
<DetachKeyPairResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DetachKeyPairResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Note|
|:---------|:------------|:----------------|:---|
|MissingParameter|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the parameter `RegionId`.  Or you are not authorized to use the resource in the specified region.|
|DependencyViolation.WindowsInstance|The instance creating is windows, cannot use ssh key pair to login.|403|SSH key pairs are not supported for Windows instances.|
|InvalidKeyPairName.NotFound|The specified KeyPairName does not exist.|404|The specified `KeyPairName` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

