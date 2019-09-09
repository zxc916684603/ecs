# Convert an ECS public IP address in a VPC to an Elastic IP Address {#concept_l2l_jgn_xdb .task}

This topic describes how to convert the public IP address of an ECS instance in a VPC to an Elastic IP Address \(EIP\). After conversion, the public IP address is retained. You can keep the public IP address bound to the instance, or bind it to another instance. Converting the public IP address does not affect public access to your ECS instance, and does not cause transient traffic interruptions.

Before converting a public IP address to an EIP, make sure the following requirements are met:

-   The ECS instance has been assigned a public IP address.
-   If the ECS instance is a subscription instance, you cannot convert the address within 24 hours prior to instance expiration.
-   If the ECS instance is a pay-as-you-go instance, your account must not have any overdue payments.
-   If the instance type of the ECS instance has been changed, wait until the change takes effect.
-   You have stopped the ECS instance or the ECS instance is in the **Running** state. For more information, see [Start or stop an instance](../reseller.en-US/Instances/Manage instances/Start or stop an instance.md#).

After the public IP address is converted to an EIP:

-   The billing method of public bandwidth remains unchanged.
-   The EIP is billed separately. For more information about EIP billing, see [EIP pricing](../../../../../reseller.en-US/Pricing/Pay-As-You-Go.md#). You can go to the **Billing Management** page, select [Usage Records](https://partners-intl.console.aliyun.com/?accounttraceid=1256cc05-a407-443c-bae2-84fb23d25d8a#/billing), and select **Elastic IP** to export EIP usage records.

This section describes how to convert the public IP address of an ECS instance in a VPC to an EIP by using the ECS console. You can also convert the IP address by calling the [ConvertNatPublicIpToEip](../reseller.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#) operation. To call this operation, use SDK 4.3.0 or later. [Download](../reseller.en-US/SDK Reference/SDK reference.md#) the latest SDK.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
3.  In the top navigation bar, select a region.
4.  Find the target instance with the **VPC** network type, and then choose **More** \> **Network and Security Group** \> **Convert to EIP** from the **Actions** column.
5.  In the dialog box that appears, confirm the information, and click **OK**.
6.  Refresh the instance list.

After the public IP address is converted to an EIP, the original IP address is followed by **\(EIP\)**.

You can click the EIP to go to the [EIP console](https://partners-intl.console.aliyun.com/?spm=a2c6n.7954052.697958.7.50951cbbma1T7R#/vpc) to manage the EIP.

After the public IP address is converted to an EIP, you can:

-   Unbind the EIP from the instance and bind it to another instance, or release it. For more information, see [Disassociate an EIP from a cloud instance](../../../../../reseller.en-US/User Guide/Disassociate an EIP from a cloud instance.md#).
-   [Add EIPs to an Internet Shared Bandwidth instance](../../../../../reseller.en-US/User Guide/Manage Pay-As-You-Go EIPs/Add EIPs to an Internet Shared Bandwidth instance.md#) to save costs. For more information, see [Select a product to gain access to the Internet](../../../../../reseller.en-US/Best practices/Select a product to gain access to the Internet.md#) and [How to save Internet cost](../../../../../reseller.en-US/Best practices/How to save the Internet cost?.md#).

**More information**  


[ConvertNatPublicIpToEip](../reseller.en-US/API Reference/Networks/ConvertNatPublicIpToEip.md#)

