# Convert public IP address to EIP address {#concept_l2l_jgn_xdb .concept}

This article describes how to convert the assigned public IP address of an ECS instance in a VPC network, which is called **VPC instance** for short in this article, to an elastic public IP \(EIP\) address. After conversion, you can keep the public IP address and bind it to another ECS instance.

## Limits {#section_asc_kgn_xdb .section}

To convert a public IP address to an EIP address, consider the following limits:

-   The action is irreversible.

-   Only a VPC instance assigned a public IP address is supported.

-   Only a VPC instance in the **Stopped** or **Running** status is supported.

-   Only a VPC instance that does not have any inactivated specification changes is supported.

-   Only a VPC instance that is not within the last 24 hours of its life cycle is supported.

-   You can only use this feature to convert a public IP address to an EIP address.


## Note {#section_mj3_qgn_xdb .section}

-   The conversion has no effect on the Internet access of the VPC instance. It does not cause transient traffic interruption.

-   The billing method of the public traffic remains unchanged.

-   After conversion, the EIP address is charged separately. For more information about billing of EIP addresses, see [EIP billing](https://www.alibabacloud.com/help/doc-detail/72142.htm). You can go to the [Usage Records](https://billing.console.aliyun.com/#/usage/record) page in the **Billing Management** to download the **Elastic Public IP** usage record.


## Procedure {#section_fsc_kgn_xdb .section}

To convert a public IP address to an elastic public IP \(EIP\) address, follow these steps:

1.  Log on to the [ECS Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find a **VPC instance** to convert the public IP address, in the **Actions** column, select **More** \> **Convert to EIP**.
5.  In the Convert the public IP address to EIP dialog box, read the note and click **OK**.
6.  Refresh the instance list.

After the public IP address is converted to an EIP address, the IP address is followed by \(**Elastic IP Address**\). 

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9657/5473_en-US.png)

Click the IP address to go to the EIP console to manage the EIP address. 

## Follow-up operations {#section_jsc_kgn_xdb .section}

After the public IP address is converted to an EIP address, you can unbind the EIP address from the instance and bind it to another instance. Besides, you can release the EIP address. For more information, see [EIP User Guide](https://www.alibabacloud.com/help/doc-detail/65203.htm).

## Related APIs {#section_lsc_kgn_xdb .section}

You can use the [ConvertNatPublicIpToEip](../../../../intl.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#) interface to convert a public IP address to an EIP address.  Currently, only SDK 4.3.0 or a higher version supports this interface.

[Download](https://www.alibabacloud.com/help/doc-detail/25699.htm) the latest SDK.

