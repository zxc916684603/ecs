# DescribeKeyPairs {#DescribeKeyPairs .reference}

Describes one or more of your SSH key pairs.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeKeyPairs.|
|RegionId|String|Yes| The ID of the region to which your SSH key pairs belong. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
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

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of key pairs.|
|PageNumber|Integer| The current page.|
|PageSize|Integer|The maximum entries on a page.|
|RegionId|String|The region of the key pair.|
|KeyPairs|[KeyPairItemType](intl.en-US/API Reference/Data type/KeyPairItemType.md#)|Information about key pairs, a set composed by KeyPairItemType.|

## Example { .section}

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

    "PageNumber": 1,
    "PageSize": 2,
    "TotalCount": 1,
    "KeyPairs": {
        "KeyPair":[{
            "KeyPairName": "test",
            "KeyPairFingerPrint": "xxxxxxxxxx"
        
    
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400| The `RegionId` parameter must be specified.|
|InvalidParameter|The specified parameter “PageNumber” is not valid.|400|The specified `PageNumber` parameter is invalid.|
|InvalidParameter|The specified parameter “PageSize” is not valid.|400| The specified `PageSize` parameter is invalid.|

