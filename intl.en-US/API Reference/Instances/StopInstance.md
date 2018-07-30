# StopInstance {#StopInstance .reference}

Stops an ECS instance.

## Description {#section_tcm_s4m_xdb .section}

-   You can only stop an instance in **Running**\(`Running`\) status.
-   The instance becomes **Stopping** \(`Stopping`\) after a successful API request, and the instance becomes **Stopped** \(`Stopped`\) after it is stopped successfully.
-   You can force an instance to stop, and the force stop operation is same as the power failure. The temporary files and data in the instance may be lost.
-   If the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance indicates `LockReason: security`, you cannot stop the instance.
-   If a [local disk](../../../../intl.en-US/Product Introduction/Block storage/Local disks.md#) is configured in an instance from the [I1 type family](../../../../intl.en-US/Product Introduction/Instance type families.md#i1), the request parameter `ConfirmStop` is required. The interface can only be called successfully when the parameter ConfirmStop is set to `True`.
-   For an instance from the I1 type family that has a local disk configured, after it is stopped, the data of the local disk is cleared. We recommend that you implement data redundancy at the application layer to guarantee the data availability.
-   This API automatically ignores the parameter `ConfirmStop` for all of the instance types except the instance of I1 type family.
-   After you enable the feature of **[No fees for stopped instances](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#)** for a VPC instance, you can set `StoppedMode=KeepCharging` to disable the feature, you are billed after the instance is stopped,  and its resource and Internet IP address are reserved.

## Request parameters { .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: StopInstance.|
|InstanceId|String|Yes|The specified instance ID.|
|ForceStop|String|No|Whether to force shutdown upon device restart. Value range:-   true: Force the instance to shut down.
-   false: The instance shuts down normally.

Default value: false.|
|ConfirmStop|Boolean|No|Whether to stop an I1 ECS instance or not.  A required parameter for I1 type family instance, it only takes effect when the instance is of I1 type family. Optional values:-   true
-   false

Default value: false.|
|StoppedMode|String|No|Whether a VPC ECS instance is billed after it is stopped or not. Optional value: KeepCharging.After you enable the feature of **[No fees for stopped instances for a VPC instance](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#)**, you can set `StoppedMode=KeepCharging` to disable the feature, the ECS instance will be billed after it is stopped, and its resource and Internet IP address are reserved.

|

## Response parameters {#section_edm_s4m_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=StopInstance
&InstanceId=i-instance1
&<Common Request Parameters>
```

**Response example**

 **XML format** 

```
<StopInstanceResponse>
    <RequestId>1C488B66-B819-4D14-8711-C4EAAA13AC01</RequestId>
</StopInstanceResponse>
```

 **JSON format ** 

```
{
    "RequestId": "1C488B66-B819-4D14-8711-C4EAAA13AC01"
}
```

## Error codes { .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskError|IncorrectDiskStatus|403|The specified ForceStop is invalid, the parameter is not in the enumerated range.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|The resource is currently locked down and the operation is denied.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The current status of the resource does not support the operation.|
|InstanceType.ParameterMismatch|The input parameter ConfirmStop must be true when an instance have localstorage.|403|The instance is locked for security reasons.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceId does not exist.|

