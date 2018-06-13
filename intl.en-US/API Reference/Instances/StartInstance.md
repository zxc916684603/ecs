# StartInstance {#StartInstance .reference}

Start a specified instance.

## Description {#section_njd_cmm_xdb .section}

-   You can only run this interface when the instance is in **Stopped** \(`Stopped`\) status.
-   After you run this interface successfully, the specified instance is in **Starting** \(`Starting`\) status.
-   If the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance indicates `LockReason: "security"`, you cannot start the instance.

## Request parameters {#section_nzr_pww_ydb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: StartInstance.|
|InstanceId|String|Yes|ID of the instance.|
|InitLocalDisk|Boolean|No|Applicable to instance types of D1, I1, and I2 [instance type family](../../../../intl.en-US/Product Introduction/Instance type families.md#). Recover to the previous normal status of your local disk when exceptions occurs. Optional values:-   true: Recover the local disk to the previous normal status. The accumulated data starting from the previous normal status is overwritten.
-   false: Skip the recovery, and keep the status of the local disk unchanged.

|

## Response parameters {#section_ujd_cmm_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
 https://ecs.aliyuncs.com/?Action=StartInstance
&InstanceId=i-instance1
&<Common Request Parameters>

```

**Response example** 

**XML format**

```
<StartInstanceResponse>
    <RequestId>C0003E8B-B930-4F59-ADC0-0E20xxxxxxxx</RequestId>
</StartInstanceResponse>
```

 **JSON format** 

```
{
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E20xxxxxxxx"
}

```

## Error codes { .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskError|Incorrect Disk Status|403|Your disk is in an abnormal status.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The current state of the instance does not support this operation.|
|InstanceExpired|PrePaid instances has been expired.|403|The Subscription instance has expired. The Pay-As-You-Go instance has been in outstanding payment.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|Operation is denied because the resource is locked for security reasons.|
|InsufficientBalance|Your account does not have enough balance.|403|The instance cannot be started because the account does not have enough balance.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceId does not exist.|
|InstanceNotReady|The specified instance is not ready for use|500|The specified instance is being created.|
|InternalError|The request processing has failed due to some unknown error.|500|Internal error, please try again later.|

