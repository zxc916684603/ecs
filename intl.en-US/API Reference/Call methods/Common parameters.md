# Common parameters {#EcsApiCommonParameters .concept}

This section describes [the common request parameters](#commonRequestParameters) and  [the common request parameters](#commonResponseParameters).

## Common request parameters {#commonRequestParameters .section}

The following table describes the common parameters that comprise of a URL for a GET request over HTTP or HTTPS protocol.

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The target API. For more information about the optional values, see [API overview](intl.en-US/API Reference/API overview.md#).|
|AccessKeyId|String|Yes|Equivalent to a logon password.  However, an AccessKey is used to call APIs, while logon password is used to log on to the  [ECS console](https://ecs.console.aliyun.com/).  .|
|Signature|String|Yes|Your signature.  For more information, see [Signature](intl.en-US/API Reference/Call methods/Signature.md#).|
|SignatureMethod|String|Yes|Signature method. Value: HMAC-SHA1.|
|SignatureVersion|String|Yes|Signature algorithm version.  Value: 1.0.|
|SignatureNonce|String|Yes|Unique random number, which is used to prevent network replay attacks. Different random numbers must be used for different requests.|
|Timestamp|String|Yes|Request time stamp. Use the offset from Coordinated Universal Time \(UTC\), the time display is based on [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#). Format: YYYY-MM-DDThh:mm:ssZ. For example, 2018-01-01T12:00:00Z indicates 20:00:00, Jan 01, 2018, Beijing time \(UTC+8\).|
|Version|String|Yes|The API version to use. Value: 2014-05-26.|
|Format|String|No|Type of the response parameters. Optional values: json | xml. Default value: xml.|

## Request example {#section_xbw_lxb_wdb .section}

```

https://ecs.aliyuncs.com/?Action=XXXXXX
&Format=xml
&Version=2014-05-26
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dgI%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2018-01-01T12:00:00Z
…
```

## Common response parameters {#commonResponseParameters .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|Request ID. We return a unique RequestId for every API request, whether the request is successful or not.|

