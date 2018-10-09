# CreateKeyPair {#CreateKeyPair .reference}

Creates an SSH key pair. We keep the public key and return the unencrypted PEM encoded `PKCS#8` private key for you  to save. For more information, see [SSH key pairs](../reseller.en-US/Product Introduction/Network and security/SSH key pairs.md#).

## Description {#section_zjh_r4n_ydb .section}

Apart from calling the CreateKeyPair, you can create your key pair by using other key pair generators and upload it \([ImportKeyPair](reseller.en-US/API Reference/Images/ImportImage.md#)\) to one of the Alibaba Cloud regions.

You can create up to 500 key pairs in each Alibaba Cloud region.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: createkeypair|
|RegionId|String|Yes|The ID of the region to which the key pair belongs. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|KeyPairName|String|Yes|The name of the key pair. The name must be unique.-   Can be \[2, 128\] characters in length.
-   Must begin with an uppercase or lowercase English letter. Can contain digits, underscores \(\_\), colons \(:\), or hyphens \(-\).
-   Supports all character set encoding formats.
-   Cannot begin with http:// or https://.

|
|Tag.n.Key|String|Yes|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|Yes|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|KeyPairName|String|Key pair name.|
|KeyPairFingerPrint|String|Fingerprint of the key pair. The public key fingerprint format is defined in RFC4716 and uses the MD5 message digest algorithm. For more information, see [RFC4716](http://tools.ietf.org/html/rfc4716).|
|PrivateKeyBody|String|The private key of a key pair. Content of the RSA private key is in the format of unencrypted PEM encoded PKCS\#8. For more information, see *OpenSSL* [PKCS\#8](https://www.openssl.org/docs/apps/pkcs8.html).|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CreateKeyPair
&RegionId=cn-qingdao
&KeyPairName=test
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<CreateKeyPairResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
    <KeyPairName>test</KeyPairName>
    <KeyPairFingerPrint>89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:d7</KeyPairFingerPrint>
    <PrivateKeyBody>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</PrivateKeyBody>
</CreateKeyPairResponse>
```

**JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
    "KeyPairName": "test"
    "KeyPairFingerPrint": "89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:d7"
    "PrivateKeyBody": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code |NOTE|
|:---------|:------------|:----------------|:---|
|MissingParameter|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the `RegionId` parameter.|
|InvalidKeyPairName.Malformed|Specified Key Pair name is not valid.|400|The specified `KeyPairName` is invalid or already exists.|
|QuotaExceed.KeyPair|The key pair quota exceeds.|403|The number of your key pairs cannot exceed 500 in each region.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

