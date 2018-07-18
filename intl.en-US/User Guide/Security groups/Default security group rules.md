# Default security group rules {#concept_f4j_vtz_xdb .concept}

This article introduces the default rules in the default security groups created manually or automatically.

**Note:** 

Security groups are stateful. If an outbound packet is allowed, inbound packets corresponding to this connection are also allowed. For more information about security groups, see [Security groups](../../../../intl.en-US/Product Introduction/Network and security/Security groups.md#).

## Security groups created by the system {#section_nwl_d5z_xdb .section}

When you create an ECS instance in a region where you have not created a security group, use the default one provided by the system.

Such a security group only has the default rules for access over the ICMP protocol, TCP Port 22 \(for SSH\), TCP Port 3389 \(for RDP\), TCP Port 80 \(for HTTP\), and TCP Port 443 \(for HTTPS\). The default rules vary according to the network type of the security group.

-   VPC: The rules apply to Internet and intranet access at the same time. The Internet access of the VPC type instance is realized through the private NIC mapping. So, you cannot see the Internet NIC inside the instance, and you can only set intranet rules in the security group. The security group rules take effect for both the intranet and the Internet. The default rules of the default VPC-Connected security group are shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type|Authorization Object|
    |N/A|Inbound|Allow|Custom TCP \(SSH\)|22/22|110|Address Field Access|0.0.0.0/0|
    |Custom TCP \(RDP\)|3389/3389|
    |All ICMP|-1/-1|
    |Custom TCP \(HTTP\), optional|80/80|
    |Custom TCP \(HTTPS\), optional|443|

-   Classic network: The default rules of a classic network-connected security group are shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type|Authorization Object|
    |Internet|Inbound|Allow|Custom TCP \(SSH\)|22/22|110|Address Field Access|0.0.0.0/0|
    |Custom TCP \(RDP\)|3389/3389|
    |All ICMP|-1/-1|
    |Custom TCP \(HTTP\), optional|80/80|
    |Custom TCP \(HTTPS\), optional|443|

    **Note:** Rules with priority 110 means that they have the lowest priority in the security group. When you manually create a security group, only values from 1 to 100 are valid for Priority. For more information about the rule priority, see [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#).


To meet your business needs, you can [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#) in the default security group.

## In a manually created security group, {#section_gbf_x5z_xdb .section}

[Creating a Security Group](intl.en-US/User Guide/Security groups/Creating a Security Group.md#) before you add rules, the following default rules apply to the communication of all the instances in the group over Internet or intranet:

-   Outbound: Allow all for outbound traffic.
-   Inbound: Drop all for inbound traffic.

If your instance has joined such a security group, you [Terminal](intl.en-US/User Guide/Connect/Connect to an instance by using the Management Terminal.md#) whether [Connect to a Linux instance by using a password](intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#) or [Connect to a Windows instance](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#).

To meet your business needs, you can [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#) in the manually created security groups.

