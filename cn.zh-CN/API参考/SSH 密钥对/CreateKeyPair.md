# CreateKeyPair {#doc_api_Ecs_CreateKeyPair .reference}

调用CreateKeyPair创建一对SSH密钥对。我们会为您保管密钥的公钥部分，并返回未加密的PEM编码的PKCS\#8格式私钥。您需要自行妥善保管私钥部分。

## 接口说明 {#description .section}

除了调用CreateKeyPair创建密钥对之外，您还可以使用第三方工具创建密钥对，然后上传（[ImportKeyPair](~~25542~~)）到某一阿里云地域，其使用方法和我们为您创建的密钥对是一致的。

您在每个地域的密钥对数最高为500对。更多详情，请参见[SSH密钥对](~~51792~~)。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=CreateKeyPair&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|KeyPairName|String|是|FinanceJoshuaV23|密钥对名称。长度为2~128个英文或中文字符。必须以大小字母或中文开头，不能以http://和https://开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|RegionId|String|是|cn-hangzhou|密钥对所在的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|CreateKeyPair|系统规定参数。取值：CreateKeyPair

 |
|ResourceGroupId|String|否|rg-resourcegroupid1|SSH密钥对所在的企业资源组ID。

 |
|Tag.N.Key|String|否|FinanceDept|密钥对的标签键。N的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持64个字符，不能以aliyun和acs:开头，不能包含http://或者https://。

 |
|Tag.N.Value|String|否|FinanceDept.Joshua|密钥对的标签值。N的取值范围：1~20。一旦传入该值，允许为空字符串。最多支持128个字符，不能以aliyun和acs:开头，不能包含http://或者https://。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|KeyPairFingerPrint|String|89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:\*\*|密钥对的指纹。根据RFC4716定义的公钥指纹格式，采用MD5信息摘要算法。更多详情，请参见[RFC4716](https://tools.ietf.org/html/rfc4716)。

 |
|KeyPairName|String|FinanceJoshuaV23|密钥对名称。

 |
|PrivateKeyBody|String|xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx|密钥对的私钥。PEM编码的PKCS\#8格式的私钥部分。

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=CreateKeyPair
&RegionId=cn-qingdao
&KeyPairName=test
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateKeyPairResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
      <KeyPairName>test</KeyPairName>
      <KeyPairFingerPrint>89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:**</KeyPairFingerPrint>
      <PrivateKeyBody>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</PrivateKeyBody>
</CreateKeyPairResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
	"PrivateKeyBody":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
	"KeyPairFingerPrint":"89:f0:ba:62:ac:b8:aa:e1:61:5e:fd:81:69:86:6d:6b:f0:c0:5a:**",
	"KeyPairName":"test"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidKeyPairName.Malformed|Specified Key Pair name is not valid.|密钥对名称不合法|
|403|QuotaExceed.KeyPair|The key pair quota exceeds.|密钥对数量已达上限。|
|400|KeyPair.AlreadyExist|The key pair already exist.|密钥对已存在，请不要重复添加。|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|资源组并不在记录中。|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|标签键中存在重复的键。|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|指定的标签键不合法。|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|指定的标签值不合法。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ecs)查看更多错误码。

