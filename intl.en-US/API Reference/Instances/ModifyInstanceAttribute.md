# ModifyInstanceAttribute {#ModifyInstanceAttribute .reference}

Modifies the information of an ECS instance, such as the name, password, host name, and description of an instance.

## Description {#section_ufy_4pt_xdb .section}

When you call this interface, consider the following:

-   You cannot reset the password for an instance when it is in the **Deleted** or **Starting** status.

-   If the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance indicates `"LockReason" : "security"`, you cannot reset its password.

-   The new password takes effect only after the instance is [restarted](../intl.en-US/User Guide/Instances/Restart an instance.md#) in the console or by calling the interface [RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#). 

-   When an instance is in the **Stopped** status and is not limited to pass a user data script, you can modify its [user data](../intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md).


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyInstanceAttribute.|
|InstanceId|String|Yes|The specified instance ID.|
|InstanceName|String|No|The name of the instance can be 2 to 128 characters in length. It must begin with an uppercase or lowercase English letter, or Chinese character. It can contain digits, periods \(.\), colons\(:\), underscores \(\_\), and hyphens \(-\). It cannot begin with http:// or https://.|
|Description|String|否|The description of the instance is null by default. It can be 2 to 256 characters in length, but cannot begin with http:// or https://. The instance description is displayed on the Alibaba Cloud console.|
|Password|String|否|Reset the administrative password of the instance. The password can be 6 to 30 characters in length and can only contain  digits, and/or alphabets.

|
|HostName|String|否|Name of the instance. It cannot start or end with period \(.\) or hyphens \(-\) and it cannot have two or more consecutive periods \(.\) or hyphens \(-\) symbols.-   **For a Windows instance**: the host name can be \[2, 15\] characters in length. It can contain uppercase or lowercase letters. It can contain digits, periods \(.\), and hyphens \(-\). It cannot contain only numeric characters.
-   **For a Linux instance**, the host name can be up to \[2, 128\] characters in length. It can be segments concatenateed by periods \(.\). Segments can contain uppercase or lowercase letters, digits, or underscores \(\_\).

|
|UserData|String|No|The user-defined data of your ECS instance. The size of your UserData must be less than 16 KB before the Base64 encodement. Refrain from entering confidential information, such as SSH key pair and AccessKey, in your request. If you do so, make sure the confidential information is encrypted before Base64 encoding. Also, do not forget to decrypt the information after it passes into your ECS instance.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceAttribute
&InstanceId=i-instance1
&Password=pwd
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyInstanceAttributeResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyInstanceAttributeResponse>
```

 **JSON format** 

```

    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidDescription.Malformed|The specified parameter “Description” is not valid.|400|The specified Description is invalid.|
|InvalidDescription.Malformed|The specified destination image description is wrongly formed.|400|The specified Description is invalid.|
|InvalidHostPassword.Malformed|The specified parameter “Password” is not valid.|400|The specified Password is invalid.|
|InvalidInstanceName.Malformed|The specified parameter “InstanceName” is not valid.|400|The specified InstanceName is invalid.|
|InvalidHostName.Malformed|The specified parameter “HostName” is not valid.|400|The specified HostName is invalid.|
|InvalidPassword.Malformed|The specified parameter “Password” is not valid.|400|The specified Password is invalid.|
|InvalidUserData.SizeExceeded|The specified parameter “UserData” exceeds the size.|400|The size of your UserData must be less than 16 KB.|
|InvalidUserData.NotSupported|The specified parameter “UserData” only support the vpc and IoOptimized Instance.|400|You can only specify UserData for a VPC instance or an I/O optimized instance.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|You cannot reset the password for an instance when it is in Deleted or Starting status.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|Your instance has been locked.|
|OperationDenied|The Specified operation is denied as your instance is locked for security reasons.|403|Your instance has been locked.|
|OperationDenied|The current status of the resource does not support this operation.|403|You cannot reset the password for an instance when it is in Deleted or Starting status.|
|HOSTNAME\_ILLEGAL|hostname is not valid.|404|The specified HostName is invalid.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceId does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified SecurityGroupId does not exist.|

