# AllocatePublicIpAddress {#AllocatePublicIpAddress .reference}

Assigns an Internet IP address to an instance.

## Description {#section_udj_c3n_ydb .section}

When you call this interface, consider the following:

-   Before assigning an Internet IP address, the instance must be in the `Running` or `Stopped` status.
-   If a VPC-Connected instance has an EIP allocated, you cannot assign an Internet IP address to it
-   You can assign only one Internet IP address to the instance. If the instance has an Internet IP address, an error `AllocatedAlready` is returned.
-   After you restart the instance \([RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#)\) or start the instance \([StartInstance](intl.en-US/API Reference/Instances/StartInstance.md#)\), the assigned Internet IP address becomes effective.
-   If the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance indicates `"LockReason" : "security"`, your request is denied.

To assign an Internet IP address to a VPC-Connected instance, you can also allocate an Elastic IP \(EIP\) to the instance. For more information, see [AssociateEipAddress](../../../../intl.en-US/API reference/EIP/AssociateEipAddress.md#).

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AllocatePublicIpAddress.|
|InstanceId|String|Yes|An instance ID that requires an Internet IP address to be assigned.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|IpAddress|String|The assigned Internet IP address.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AllocatePublicIpAddress
&InstanceId=i-instance1
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<AllocatePublicIpAddressResponse>
    <RequestId>F2EF6A3B-E345-46B9-931E-0EA094818567</RequestId>
    <IpAddress>10.1.149.159</IpAddress>
</AllocatePublicIpAddressResponse>
```

**JSON format** 

```

    "RequestId": "F2EF6A3B-E345-46B9-931E-0EA094818567",
    "IpAddress": "10.1.149.159"

```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InsufficientPublicIp|Ip address not found|400|No available Internet IP address, please try again later.|
|OperationDenied|Specified operation is denied as your instance is in VPC.|400| The specified VPC-Connected instance has an EIP allocated and cannot be assigned an Internet IP.|
|AllocatedAlready|There is an IpAddress allocated already for the specified instance.|403|The instance has an Internet IP address assigned.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|Before assigning an Internet IP address, the instance must be in the `Running` or `Stopped` status.|
|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|403|The specified [Subscription](../../../../intl.en-US/Pricing/Subscription.md#) instance has expired or the specified [Pay-As-You-Go](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#) instance has an overdue payment.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|The specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for security reason, and your request is denied.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|

