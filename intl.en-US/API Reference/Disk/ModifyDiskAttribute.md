# ModifyDiskAttribute {#ModifyDiskAttribute .reference}

Modifies the attribute of a cloud disk.

## Description {#section_ntk_xp5_xdb .section}

In this interface, when the **DeleteWithInstance** \(`DeleteWithInstance=false`\) attribute is set to false, once the ECS instance on which the disk is attached is [locked](reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) and the `OperationLocks` of instance indicates `"LockReason" : "security"`, the `DeleteWithInstance` attribute of disk is ignored and the disk is released along with the instance.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyDiskAttribute.|
|DiskId|String|Yes|ID of the target disk.|
|DiskName|String|No|The disk name.-   It can contain \[2, 128\] English letters an must begin with an uppercase or lowercase letter. Can contain digits, colons \(:\), periods \(.\), underscores \(\_\), and hyphens \(-\).
-   It cannot begin with http:// or https://.
-   If it is left empty, the original value is used. The default value is null.

|
|Description|String|No|The description of a disk.-   It can contain \[2, 256\] letters and must begin with an uppercase or lowercase letter. Can contain digits, colons \(:\), periods \(.\), underscores \(\_\), and hyphens \(-\).
-   Cannot begin with http:// or https://.
-   If it is left empty, the original value is used. The default value is null.

|
|DeleteWithInstance|String|No|Whether the disk is released along with the instance or not. Optional values:-   True: If the instance is released, this disk is also released.
-   False: If the instance is released, this disk is retained.

Default value: None. In the following conditions, when you set `DeleteWithInstance` to `false`, an error is returned.-   When the Category \(`category`\) attribute of disk is ephemeral \(`ephemeral`\).
-   When the Category \(`category`\) attribute of disk is cloud \(`cloud`\) and the Portable \(`Portable=false`\) attribute is false.

|
|DeleteAutoSnapshot|String|No|Whether the automatic snapshots of a cloud disk are deleted or not when the disk is deleted. Optional values:-   True: If the disk is released, its automatic snapshots are also released.
-   False: If the disk is released, its automatic snapshots are retained.

Default value: None.|
|EnableAutoSnapshot|String|No|If you have created an automatic snapshot policy, you can decide whether an automatic snapshot policy is applied to the disk or not. Optional values:-   True: The disk runs an automatic snapshot policy.
-   False: The disk does not run an automatic snapshot policy.

Default value: None.|

## Response parameters {#section_b5k_xp5_xdb .section}

All are common return parameters. For more information, see [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyDiskAttribute
&DiskId=d-23jbf2v5m
&DiskName=MyDiskName
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyDiskAttributeResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyDiskAttributeResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidDiskName.Malformed|The specified disk name is wrongly formed.|400|The format of the specified DiskName is incorrect.|
|NoAttributeToModify|No attribute to be modified in this request.|400|Duplicate requests.|
|DiskNotPortable|The specified disk is not a portable disk.|403|When you set the `DeleteWithInstance=false` attribute, you cannot set the attribute `Portable` of the specified cloud disk to `false`.|
|IncorrectDiskStatus|The operation is not supported in this status.|403|The status of the cloud disk is incorrect. For more information, see [Basic cloud disk status](reseller.en-US/API Reference/Appendix/Basic cloud disk status table.md#).|
|InvalidDescription.Malformed|The specified description is wrongly formed.|404|The format of specified Description is incorrect.|
|InvalidDiskId.NotFound|The specified disk does not exist.|404|The specified DiskId does not exist.|

