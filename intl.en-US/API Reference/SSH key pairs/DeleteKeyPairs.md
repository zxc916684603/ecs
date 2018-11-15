# DeleteKeyPairs {#DeleteKeyPairs .reference}

Deletes one or more of your SSH key pairs. Once an SSH key pair is deleted, we remove the related entry of the public key from our database. However, the instances that have the SSH key pair attached, can use it normally, and you can still view the instance key pair name in the instance details list.

## Description {#section_kq4_trn_ydb .section}

When you call this interface, consider the following:

-   The SSH key pair cannot be described \([DescribeKeyPairs](reseller.en-US/API Reference/SSH key pairs/DescribeKeyPairs.md#)\) any more.

-   When you obtain the information about the instances \([DescribeInstances](reseller.en-US/API Reference/Instances/DescribeInstances.md#)\), the key pair name \(`KeyPairNames`\) is still returned, but without any information about the SSH key pair.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteKeyPairs.|
|RegionId|String|Yes|The ID of the region to which the SSH key pair belongs. For more information, call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|KeyPairNames|String|Yes|The names of key pairs. The value can contain arrays of up to 100 SSH key pairs. The key pair name are displayed in the format of \["key-xxxxxxxxx", "key-yyyyyyyyy", … "key-zzzzzzzzz"\]  and separated by commas \(,\).|

## Return parameters {#section_f54_lk5_xdb .section}

All are common parameters. See [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteKeyPairs
&RegionId=cn-qingdao
&KeyPairNames=test
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<DeleteKeyPairsResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteKeyPairsResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code |Meaning|
|:---------|:------------|:----------------|:------|
|MissingParameter|The input parameter RegionId that is mandatory for processing this request is not supplied.|400|You must specify the parameter `RegionId`.  Or you are not authorized to use the resource in the specified region.|
|MissingParameter|The input parameter KeyPairName that is mandatory for processing this request is not supplied.|400| You must specify the `KeyPairName` parameter.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

