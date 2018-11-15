# ModifyImageSharePermission {#ModifyImageSharePermission .reference}

Shares a custom image to other Alibaba Cloud users. Alternatively, withdraws the sharing authorization from other Alibaba Cloud users. Other users can create ECS instances \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\) or replace the system disks \([ReplaceSystemDisk](intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)\) by using the shared images.

## Description {#section_xlx_bjz_xdb .section}

When you call this interface, consider the following:

-   You can only share custom images to other Alibaba Cloud users.

-   One image can be shared to a maximum of 10 Alibaba Cloud accounts at a time. Or up to 10 accounts to whom a custom image is shared can be removed at a time.  If more than 10 account IDs are specified in the parameter `AddAccount.n` or `RemoveAccount.n`, the parameter takes no effect.

-   One image can be shared to 50 Alibaba Cloud accounts at most. However, you can [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) if you want to share it with more users.

-   If an instance is created \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\) by using a shared image, once the image owner withdraws the sharing authorization or deletes the custom image \([DeleteImage](intl.en-US/API Reference/Images/Deleteimage.md#)\), the specified instance cannot be reinitialized \([ReInitDisk](intl.en-US/API Reference/Disk/ReInitDisk.md#)\).


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyImageSharePermission.|
|RegionId|String|Yes|ID of the region to where the custom image belongs. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|ID of the custom image.|
|AddAccount.n|String|No|IDs of to-be-added Alibaba Cloud accounts where the image is shared. Value range of n: \[1, 10\]. If n is greater than 10, this parameter is ignored.

|
|RemoveAccount.n|String|No|IDs of to-be-removed Alibaba Cloud accounts where the image is shared. Value range of n: \[1, 10\]. If n is greater than 10, this parameter is ignored.

|

## Response parameters {#section_hmx_bjz_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyImageSharePermission
&RegionId=cn-hangzhou
&ImageId=m-281234567
&AddAccount. 1=23412345234
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyImageSharePermissionResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</ModifyImageSharePermissionResponse>
```

 **JSON format** 

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|IncorrectImageStatus|The image is not available.|400|The specified image is unavailable.|
|InvalidRegionId.NotFound|The specified region does not exist.|400|The specified `RegionId` does not exist.|
|MissingParameter|An input parameter RegionId that is mandatory for processing the request is not supplied.|400|You must specified the `RegionId` parameter.|
|MissingParameter|An input parameter ImageId that is mandatory for processing the request is not supplied.|400|You must specified the `ImageId` parameter.|
|OperationDeined.EncryptedSnapshot|The image contains encrypted snapshots, which do not support share.|403|This action fails because the specified image contains encrypted snapshot.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|403|The specified `ImageId` does not exist.|
|QuotaExceed.ShareImageUser|The shared image user quota exceeds.|403|You can only share a custom image to 50 Alibaba Cloud users at most. Open a ticket if you want to share it with more users.|
|InvalidAccount.Forbbiden|The specified account does not yourself.|404|You cannot share images to yourself.|
|InvalidAccount.NotFound|The specified parameter AddAccount.n or RemoveAccount.n does not exist.|404|The specified account ID listed in the parameter `AddAccount.n` or `RemoveAccount.n` does not exist.|

