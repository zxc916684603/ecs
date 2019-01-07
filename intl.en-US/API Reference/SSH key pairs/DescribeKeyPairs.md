# DescribeKeyPairs {#DescribeKeyPairs .reference}

Describes one or more of your SSH key pairs.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeKeyPairs.|
|RegionId|String|Yes| The ID of the region to which your SSH key pairs belong. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|KeyPairFingerPrint|String|No|The fingerprint of the key pair. The public key fingerprint format is defined in RFC4716 and uses the MD5 message digest algorithm. For more information, see [RFC4716](http://tools.ietf.org/html/rfc4716).|
|KeyPairName|String|No|The key pair name. You can use the regular expression and the symbol `*` for fuzzy string search of a key pair name. Sample patterns:-    `*SshKey`: Matches the string set ending with *SshKey*, including *SshKey*.
-    `SshKey*`: Matches the string set beginning with *SshKey*, including *SshKey*.
-    `*SshKey*`: Matches the string set with *SshKey* within, including *SshKey*.
-    `SshKey`: Matches the string set *SshKey*.

|
|PageNumber|Integer|No|Displays the SSH key pairs on several pages.  Start value: 1. Default value: 1.

|
|PageSize|Integer|No|The maximum entries on a page. Maximum value: 50.Default value: 10.

|
|Tag.n.Key|String|Yes|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|Yes|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of key pairs.|
|PageNumber|Integer| The current page.|
|PageSize|Integer|The maximum entries on a page.|
|RegionId|String|The region of the key pair.|
|KeyPairs|[KeyPairItemType](reseller.en-US/API Reference/Data type/KeyPairItemType.md#)|Information about key pairs, a set composed by KeyPairItemType.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeKeyPairs
&RegionId=cn-qingdao
&KeyPairFingerPrint=xxxxxxxxxx
&KeyPairName=test
&PageNumber=1
&PageSize=20
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeKeyPairsResponse>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <TotalCount>1</TotalCount>
    <KeyPairs>
        <KeyPair>
            <KeyPairName>test</KeyPairName >
            <KeyPairFingerPrint>xxxxxxxxxx</KeyPairFingerPrint>
        </KeyPair>
    </KeyPairs>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DescribeKeyPairsResponse>
```

**JSON format** 

```
{
  "PageNumber": 1,
  "PageSize": 50,
  "RequestId": "B04B8CF3-4489-432D-83BA-6F128E4F2295",
  "Tags": {
    "Tag": [
      {
        "TagKey": "test",
        "TagValue": "api"
      }
    ]
  },
  "TotalCount": 1
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter|The input parameter “RegionId” that is required for processing this request is not supplied.|400| The `RegionId` parameter must be specified.|
|InvalidParameter|The specified parameter “PageNumber” is not valid.|400|The specified `PageNumber` parameter is invalid.|
|InvalidParameter|The specified parameter “PageSize” is not valid.|400| The specified `PageSize` parameter is invalid.|

