# ModifyInstanceAutoReleaseTime {#ModifyInstanceAutoReleaseTime .reference}

Sets the automatic release time for onePay-As-You-Go instance. Be cautious that the instance is automatically released upon expiration of the specified time.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyInstanceAutoReleaseTime.|
|InstanceId|String|Yes|ID of the instance.|
|AutoReleaseTime|String|No|The automatic release time for the specified instances. The time is represented based on [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#), and the UTC time is used. The format is YYYY-MM-DDTHH:mm:ssZ.-   If the seconds \(`ss`\) place is not   `00`, it is automatically set to start from the current minute \(`mm`\).
-   The automatic release time must be at least half an hour later than the current time.
-   The automatic release time must be less than 3 years since the current time.

If you do not specify the  `AutoReleaseTime`, the specified ECS instance will not be automatically released.|

## Return parameters {#section_rjz_l25_xdb .section}

All are common parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceAutoReleaseTime
&InstanceId=i-instance1
&<Common Request Parameters>
```

**Response sample** 

**XML format**

```
<ModifyInstanceAutoReleaseTimeResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceAutoReleaseTimeResponse>
```

 **JSON format** 

```
{ 
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E209A9012A8"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidAutoReleaseTime.Malformed|The specified paramter autoReleaseTime is not valid.|400|The specified  `AutoReleaseTime`  is invalid.|
|MissingParamter.InstanceId|InstanceId should not be null.|400|You need to pass in the parameter`InstanceId`.|
|UnsupportedParameter|The parameters is unsupported.|400|The specified parameter is not supported.|
|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|403|You cannot release a in service subscription instance.|
|NoSuchResource|The specified resource is not found.|404|The specified resource does not exist.|
|InternalError |The request processing has failed due to some unknown error,exception or failure.| 500| Internal error.|

