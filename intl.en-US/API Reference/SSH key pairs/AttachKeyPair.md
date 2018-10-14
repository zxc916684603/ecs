# AttachKeyPair {#AttachKeyPair .reference}

Attaches an SSH key pair to one or more of your Linux instances.

## Description {#section_bqq_wpn_ydb .section}

When you call this interface, consider the following:

-   SSH key pairs are not supported for Windows instances.

-   Once the SSH key pair is used, the authentication method by using the user name and password is disabled, by default.

-   If the instance is in **Running** \(`Running`\) status, restart the instance \([RebootInstance](reseller.en-US/API Reference/Instances/RebootInstance.md#)\) to make the operation take effect.

-   If the instance is in **Stopped** \(`Stopped`\) status, the SSH key pair takes effect immediately once the instance starts \([StartInstance](reseller.en-US/API Reference/Instances/StartInstance.md#)\).

-   If an instance already has an attached SSH key pair, the new SSH key pair replaces the former one automatically.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AttachKeyPair.|
|RegionId|String|Yes|The ID of the region to which the SSH key pair belongs. For more information, call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|KeyPairName|String|Yes| The name of the SSH key pair.|
|InstanceIds|String|Yes|The instance ID. The value can contain arrays of up to 50 instance IDs. The IDs are displayed in the format of \["i-xxxxxxxxx", "i-yyyyyyyyy", … "i-zzzzzzzzz"\] and separated by commas \(,\).|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AttachKeyPair
&RegionId=cn-qingdao
&KeyPairName=test
&InstanceIds=["i-XXXXX"]
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<AttachKeyPairResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</AttachKeyPairResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|MissingParameter|The input parameter RegionId that is required for processing this request is not supplied.|400|You must specify the parameter `RegionId`. Or you are not authorized to use the resource in the specified region.|
|DependencyViolation.WindowsInstance|The instance creating this window, cannot use ssh key pair to login.|403|You cannot attach SSH key pair to Windows instances.|
|InvalidKeyPairName.NotFound|The specified KeyPairName does not exist in our records.|404|The specified `KeyPairName` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

