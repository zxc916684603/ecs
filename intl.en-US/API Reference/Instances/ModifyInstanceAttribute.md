# ModifyInstanceAttribute {#doc_api_1161582 .reference}

Modifies the information of an ECS instance, such as the password, name, description, hostname, and user data. For a burstable performance instance \(t5\), you can also change its running mode.

## Description {#description .section}

When you call this operation, note that:

-   When an instance is in the **starting** \(`Starting`\) state, you cannot reset its password.
-   For an ECS instance on which [Security Control](~~25695~~) is enabled, its `OperationLocks` cannot be tagged as `"LockReason" : "security"`.
-   After resetting the password, you need to [restart the instance](~~25440~~) from the console or call the [RebootInstance](~~25502~~) operation to validate the modifications. The restart operation within the instance will not validate the modifications.
-   When an instance is in the **stopped**\(`Stopped`\) state and meets the requirements for [user data](~~49121~~), you can modify its user data.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=ModifyInstanceAttribute) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|InstanceId|String|Yes|i-instance1| The ID of the instance.

 |
|Action|String|No|ModifyInstanceAttribute| The operation that you want to perform. Set the value to **ModifyInstanceAttribute**.

 |
|CreditSpecification|String|No|Standard| The running mode of the burstable performance instance \(t5\). Valid values:

 -   Standard: the standard mode. For more information, see [Standard t5 instances](~~90635~~).
-   Unlimited: the unlimited performance mode. For more information, see [Unlimited-performance t5 instances](~~90581~~).

 Default value: null.

 |
|DeletionProtection|Boolean|No|false| The release protection attribute of the instance. It indicates whether you can use the ECS console or call the [DeleteInstance](~~25507~~) operation to release the instance.

 Default value: null.

 **Note:** This attribute is applicable to subscription, Pay-As-You-Go, and preemptible instances. It can only be used to block manual release operations, but not automatic release operations by the system.

 |
|Description|String|No|InstanceAttribute| The description of the instance. It must be 2 to 256 characters in length. It cannot start with http:// or https://.

 Default value: null.

 |
|HostName|String|No|LocalHost| The hostname of the instance.

 -   It cannot start or end with a period \(`.`\) or a hyphen \(`-`\). It cannot have two or more consecutive periods \(.\) or hyphens \(-\).
-   For Windows: The hostname cannot contain periods \(`.`\) or contain only digits. It must be 2 to 15 characters in length and can contain uppercase and lowercase letters, digits, and hyphens \(`-`\).
-   For other operating systems: The hostname can be separated by periods \(`.`\). It must be 2 to 64 characters in length and can contain uppercase and lowercase letters, digits, and hyphens \(`-`\).

 |
|InstanceName|String|No|EcsInstance| The name of the instance. It must be 2 to 128 characters in length. It must start with a letter. It cannot start with http:// or https://. It can contain uppercase and lowercase letters, digits, colons \(`:`\), underscores \(`_`\), and hyphens \(`-`\).

 |
|Password|String|No|EcsV587!| The password for the instance.

 **Note:** If Password is specified, we recommend that you send requests over the HTTPS protocol to keep the password confidential.

 It must be 8 to 30 characters in length and can contain uppercase and lowercase letters, digits, and special characters. For Windows, the password cannot start with a forward slash \(/\). The following special characters can be used:

 ```
()`~!@#$%^&*-_+=|{}[]:;'<>,.?/
```

 |
|Recyclable|Boolean|No|false| Indicates whether the instance can be recycled.

 |
|UserData|String|No|ZWNobyBoZWxsbyBlY3Mh| The user data of the instance. User data is encoded in Base64. The size of your UserData must be less than 16 KB. Because user data is imported in plain-text mode, we recommend that you do not import confidential information, such as passwords and keys. If confidential information is required, we recommend that you encrypt it and encode it in Base64 before importing it. Perform decryption in the same way.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The request ID.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=ModifyInstanceAttribute
&InstanceId=i-instance1
&Action=ModifyInstanceAttribute
&CreditSpecification=Standard
&DeletionProtection=false
&Description=InstanceAttribute
&HostName=LocalHost
&InstanceName=EcsInstance
&Password=EcsV587!
&Recyclable=false
&UserData=ZWNobyBoZWxsbyBlY3Mh
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyInstanceAttributeResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId> 
</ModifyInstanceAttributeResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidHostName.Malformed|The specified parameter "HostName" is not valid.|The error message returned when the format of the specified HostName is invalid.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned when the operation is not supported while the resource is in the current state.|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned when the specified SecurityGroupId does not exist under this account. Check whether the SecurityGroupId is correct.|
|403|OperationDenied|The instance amount in the specified SecurityGroup reach its limit.|The error message returned when the maximum number of instances in the specified security group is reached.|
|403|OperationDenied|The current status of the resource does not support this operation.|The error message returned when the operation is not supported while the resource is in the current state.|
|403|InvalidUserData.Forbidden|User not authorized to input the parameter "UserData", please apply for permission "UserData"|The error message returned when you are not authorized to configure UserData. Apply for the permissions first.|
|400|InvalidUserData.NotSupported|TThe specified parameter "UserData" only support the vpc and IoOptimized Instance.|The error message returned when the specified UserData is only supported in VPC-type or optimized instances.|
|400|InvalidUserData.NotSupported|The specified parameter "UserData" only support the vpc and IoOptimized Instance.|The error message returned when the specified UserData is only supported in VPC-type or optimized instances.|
|400|InvalidParameter.RecycleBin|You do not have permission to set recyclable properties.|The error message returned when you are not authorized to perform this operation.|
|400|InvalidParameter.CreditSpecification|The specified CreditSpecification is not supported in this region.|The error message returned when the specified CreditSpecification is not supported in this region.|
|400|InvalidInstanceStatus.CreditSpecRestricted|The current status of the resource does not support this operation.|The error message returned when the operation is not supported while the resource is in the current state.|
|400|InvalidInstanceStatus.NotRunning|The current status of the resource is invalid, you can only do this operation when instance is running.|The error message returned when the current status of the resource is invalid.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

