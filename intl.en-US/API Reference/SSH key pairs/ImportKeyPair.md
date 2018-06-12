# ImportKeyPair {#ImportKeyPair .reference}

Imports the public key of an SSH key pair that you create with other key pair generators into one of the Alibaba Cloud regions. Once the public key is imported we secure it. However, you must save the private key by yourself.

## Description {#section_qqb_kpn_ydb .section}

When you call this interface, consider the following:

-   You can create up to 500 key pairs in each Alibaba Cloud region.

-   The encryption method of your SSH key pair must be any of the following:

    -   rsa
    -   dsa
    -   ssh-rsa
    -   ssh-dss
    -   ecdsa
    -   ssh-rsa-cert-v00@openssh.com
    -   ssh-dss-cert-v00@openssh.com
    -   ssh-rsa-cert-v01@openssh.com
    -   ssh-dss-cert-v01@openssh.com
    -   ecdsa-sha2-nistp256-cert-v01@openssh.com
    -   ecdsa-sha2-nistp384-cert-v01@openssh.com
    -   ecdsa-sha2-nistp521-cert-v01@openssh.com

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ImportKeyPair|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|PublicKeyBody|String|Yes|The public key of the SSH key pair.|
|KeyPairName|String|Yes|The name of the key pair. The name must be unique.-   Can be \[2, 128\] characters in length.
-   Must begin with an uppercase or lowercase English letter. Can contain digits, underscores \(\_\), colons \(:\), or hyphens \(-\).
-   Supports all character set encoding formats.
-   Cannot begin with http:// or https://.

|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|KeyPairName|String|Key pair name.|
|KeyPairFingerPrint|String| Fingerprint of the key pair The public key fingerprint format is defined in RFC4716 and uses the MD5 message digest algorithm. For more information, see [RFC4716](http://tools.ietf.org/html/rfc4716).|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ImportKeyPair
&RegionId=cn-qingdao
&PublicKeyBody=xxxxxxxxxxxxxx
&KeyPairName=test
&<Common Request Parameter>
```

**Response example** 

**XML format**

```
<ImportKeyPairResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
    <KeyPairName>test</KeyPairName>
    <KeyPairFingerPrint> 89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:d7</KeyPairFingerPrint>
</ImportKeyPairResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
    "KeyPairName": "test"
    "KeyPairFingerPrint": "89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:d7"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Meaning|
|:---------|:------------|:----------------|:------|
|MissingParameter|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|You must specify the `RegionId` parameter.|
|InvalidPublicKeyBody.Malformed|The PublicKeyBody format is not supported.|400|The format of the specified `PublicKeyBody` is incorrect.|
|InvalidKeyPairName.Malformed|Specified Key Pair name is not valid.|400| The specified `KeyPairName` is invalid or already exists.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

