# RebootInstance {#RebootInstance .reference}

Restarts an ECS instance.

## Description {#section_nkm_wnr_xdb .section}

-   You can only restart an ECS instance that is in the **Running** \(`Running`\) status.
-   After an ECS instance is restarted, its intermediate status is **Starting** \(`Starting`\).
-   An instance can be forcefully stopped. Forcing an instance to stop \(`ForceStop`\) is same as a power failure. The temporary data and files in the instance may be lost.
-   If the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance indicates  `"LockReason" : "security"`, you cannot restart the instance.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: RebootInstance.|
|InstanceId|String|Yes|The specified instance ID.|
|ForceStop|String|No|Whether to force shutting down the instance before it restarts. Optional values:-   true: Forces shutting down the instance before it restarts.
-   false: Shuts down the instance normally before it restarts.

Default value: false.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=RebootInstance
&InstanceId=i-instance1
&<Common Request Parameters>
```

**Response example**

 **XML format** 

```
<RebootInstanceResponse>
    <RequestId>F2E2C40D-AB09-45A1-B5C5-EB9F5C4E4E4A</RequestId>
</RebootInstanceResponse>
```

 **JSON format** 

```
{
    "RequestId": "F2E2C40D-AB09-45A1-B5C5-EB9F5C4E4E4A"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskError|IncorrectDiskStatus.|403|Abnormal disk status.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403| You can only restart an ECS instance that is in Running status.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|Your instance is locked for security reasons.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|

