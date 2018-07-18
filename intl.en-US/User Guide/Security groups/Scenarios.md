# Scenarios {#concept_ngr_vht_xdb .concept}

This article introduces several common scenarios of VPC-connected and classic network-connected security groups.

**Note:** 

-   For more information about how to create a security group and its rules, see [Creating a Security Group](intl.en-US/User Guide/Security groups/Creating a Security Group.md#) and [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#).
-   For common ports, see [Introduction to common ECS instance ports](intl.en-US/User Guide/Security groups/Introduction to common ECS instance ports.md#).
-   For security group rule configuration of common port, see[Typical application of security group rules](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#).

-   [Scenario 1: Enable intranet communication](#intranetCommunication) 

    Example: If you want to copy files between two classic network-connected ECS instances owned by different accounts or in different security groups, you can enable intranet communication between both instances by configuring security group rules and then copy files.

-   [Case 2: Mask, intercept, block access to an instance or an instance-specific port for a specific IP Address](#blockAccess) 

    Example: When your ECS instance is compromised by hackers as a zombie, you can modify the port for remote connection, and configure security group rules to allow access from a specified IP address only.

-   [Scenario 2: Allow remote connection from a specified IP address only](#specifyIpAccess) 

    Example: When your ECS instance is compromised by hackers as a zombie, you can modify the login port number in distance,  and configure that the system only allows specific IP address to log onto your ECS instance.

-   [Case 4: only allow instances to access specific external IP addresses.](#specifyInstanceAccess) 

    Example: When your ECS instance is compromised by hackers as a zombie and scan or send packets maliciously, you can configure security group rules to allow the instance to access to a specified IP address.

-   [Case 5: Allow remote connection to the instance](#allowRemoteAccess) 

    Example: You can connect to an ECS instance by configuring a security group rule.

-   [Case 6: allow Internet access through services such as HTTP, https](#allowHttp) 

    Example: If you build a website on your instance, you can configure security group rules to enable your users to access the website.


## Scenario 1: Enable intranet communication {#intranetCommunication .section}

Security group rules can be used in the following cases to enable intranet communication between ECS instances that belong to different accounts or security groups in the same region There are the following cases:

-   Case 1: Instances belong to one region and one account
-   Case 2: Instances belong to one region but different accounts

**Note:** 

For VPC-Connected ECS instances: If they are in one VPC, you can configure their security group rules to enable intranet communication. If they are in different VPCs, or owned by different accounts in the same region, Express Connect is the only option to establish intranet communication. For more information, see [Establish an intranet connection between VPCs under different accounts](https://www.alibabacloud.com/help/doc-detail/44842.htm).

**Case 1: Instances belong to one region and one account**

For two instances in one region but owned by one account, if they are in one security group, intranet communication is enabled by default. If they are in different security groups, you must configure security group rules to enable intranet communication according to the network types.

-   VPC: If they are in one VPC, add a rule in their security groups respectively to authorize the security groups to access each other. The rule must be as follows.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port RangePort range|PriorityPriority|Authorization Type|Authorization Object|
    |N/A|Inbound|Allow|Select the required protocol|Set the required port range|1|Security Group Access \(Authorize This Account\)|Select the Security Group ID on which you want to allow access to the instance|

-   Classic network: Add a rule in their security groups respectively to authorize the security groups to access each other. The rule must be as follows.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type| Authorization Object|
    |Classic network|Intranet|Inbound|Allow|Select the required protocol|Set the required port range|1|Security Group Access \(Authorize This Account\)|Type the other security group ID|


**Case 2: Instances belong to one region but different accounts**

For classic network-connected ECS instances only.

Authorize the security groups to access each other.  For example:

-   UserA owns a classic network-connected ECS instance in the East China 1 region, named InstanceA, with the private IP address A.A.A.A. The security group is GroupA.
-   UserB owns a classic network-connected ECS instance in the East China 1 region, named InstanceB, with the private IP address B.B.B.B. The security group is GroupB.
-   Add a rule in GroupA to authorize access of InstanceA to InstanceB, as shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |Intranet|Inbound|Allow|Select the required protocol |Set the required port range|Security Group Access \(Authorize Other Account\) |Type the  **account** ID of UserB and the security group ID of GroupBSet port range|1|

-   Add a rule in GroupB to authorize access of InstanceB to InstanceA, as shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |Intranet|Inbound|Allow |Select the required protocol|Set the required port range|Security Group Access \(Authorize This Account\)|Type the **account** ID of UserA and the security group ID of GroupBSet port range|1|

    **Note:** To guarantee the security of your instances, when you are configuring an intranet inbound rule for a classic network-connected security group, Security Group Access is the top priority for Authorization Type.  If you select **Address Field Acces**s, you must enter an IP address with CIDR prefix, “/32”, in the format of `a.b.c.d/32`. Only IPv4 is supported.


## Case 2: Mask, intercept, block access to an instance or an instance-specific port for a specific IP Address {#blockAccess .section}

If you need to use security groups to mask, intercept, and block access to your ECS instance for a specific IP address, or mask specific IP addresses to access specific ports of the ECS instance \(like TCP's Port 22\), you can set up security group rules in the following example:

-   If you want to deny access to all ECS ports for a specific public network IP address segment, add the Security Group Rules shown in the following table:

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Drop|All|-1/-1|Address Field Access|The IP address to mask. Use CIDR prefix, in the format of a.b.c.d/27.|1|
    |Classic Network|Internet|

-   To drop access to a specific IP address segment to an ECS-specific port, such as a TCP Port 22, add the following security group rules:

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Drop|SSH\(22\)|22/22|Address Field Access|The IP address to mask. Use CIDR prefix, in the format of a.b.c.d/27.|1|
    |Classic Network|Internet|


## Scenario 2: Allow remote connection from a specified IP address only {#specifyIpAccess .section}

If you want to allow remote connection to your instance from the specified public IP addresses, add the following rule. In this example, we allow remote connection to an instance on TCP Port 22 from a specified IP address.

1.  Allow specific IP address to access TCP Port 22. Set the priority to 1, which is the highest. Perform it first. Security Group rules are shown as follows.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Allow|SSH\(22\)|22/22|Address Field Access|The IP address to allow access, such as 1.2.3.4.|1|
    |Classic Network|Internet|

2.  Drop access to the other IP address, with a lower priority than Priority 1. Security Group rules are shown as follows.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Drop|SSH\(22\)|22/22|Address Field Access|0.0.0.0/0|2|
    |Classic Network|Internet|


After you have configured:

-   Type the specified IP address, such as 1.2.3.4
-   If the instance can be accessed by the specified IP address, it means the rules work.

## Case 4: only allow instances to access specific external IP addresses. {#specifyInstanceAccess .section}

If you just want the instance to have access to a specific IP address, go through the following example for the steps to add a security group rule to the security group in which the instance is located:

1.  To prohibit the instance from accessing all Internet IP addresses with any protocol, the priority should be less than the rule that allows access \(such as  priority 2 in this example \). Security Group rules are shown in the following table.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Drop|All|-1/-1|Address Field Access|0.0.0.0/0|2|
    |Classic Network|Internet|

2.  To allow an instance to access a specific Internet IP address, the priority should be higher than the priority of the security group rule for which access is denied \(for example, set to 1 in this case\).

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Outbound|Allow|Select the applicable protocol type|Set port range|Address Field Access|A specific Internet IP address, such as 1.2.3.4, that is allowed to be accessed by the instance.|1|
    |Classic Network|Internet|


After adding security group rules, connect to the instance, and run `ping`, `telnet` to test. If an instance can only access an IP address that is allowed, it means the security group rule takes effect.

## Case 5: Allow remote connection to the instance {#allowRemoteAccess .section}

There are two cases:

-   Case 1: Allow the public network to remotely connect to the specific instance.
-   Case 2: Allow instances of other accounts in the intranet to remotely connect to a specific instance or all instancess.

**Case 1: Allow the public network to remotely connect to the specific instance**

If you want to allow remote connection instances from the Internet, refer to the following example to add security group rules.

-   VPC: add security group rules as shown below.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|If you allow any Internet IP address to connect to an instance, fill in 0.0.0.0/0. If you only allow a specific IP address to connect to an instance remotely, see [Scenario 2: Allow remote connection from a specified IP address only](#specifyIpAccess).|1|
    |Linux: SSH \(22\)|22/22|
    |Custom TCP|Customize|

-   Classic Network: add security group rules as shown in the following table.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |Classic Network|Internet|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|If you allow any public network IP address to connect to the instance, enter 0.0.0.0/0. If you only allow a specific public network IP address to connect to an instance, see.|1|
    |Linux: SSH\(22\)|22/22|
    |Custom TCP|Customize|


For more information on customizing remote connection ports, see [Modiy the server default remote ports](https://www.alibabacloud.com/help/doc-detail/51644.htm)

**Case 2: Allow an instance in a security group of another account in the intranet to connect to your instance remotely.**

If your account is in the same intranet with another account in the same region, and you want to allow a remote connection to the instance in a security group of that account, follow the example below to add a security group rule.

-   Allow another account in the intranet to connect to your instance.
    -   VPC: ensure instances of both accounts [establish an intranet connection between VPCs under different accounts](https://www.alibabacloud.com/help/doc-detail/44843.htm) before adding the security group rules shown in the following table.

        |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |VPC|N/A|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|The private IP address of the other instance|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Customize|

    -   Classic Network: Add the security group rules shown in the following table.

        |Network Type|NIC|Rule direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |Classic Network|Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Address Field Access|The intranet IP address of the other instance. Out of security concerns, only  single IP authorization is supported, for example:. b. c. d/32.|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Customize|

-   Allow all ECs instances in one Security Group to connect to your instance
    -   VPC: ensure instances of both accounts [establish an intranet connection between VPCs under different accounts](https://www.alibabacloud.com/help/doc-detail/44843.htm) before adding the security group rules shown in the following table.

        |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |VPC|N/A|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security Group access \(cross-account authorization\)|The security group ID of the other instance, and enter the other's account ID|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Customize|

    -   For a classic network instance, add security group rules as shown in the following table.

        |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |Classic Network|Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security Group access \(cross-account authorization\)|The security group ID of the other instance, and enter the other's account ID|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Customize|


## Case 6: allow Internet access through services such as HTTP, https {#allowHttp .section}

If you  host a website on an instance, and you want your users to be able to access your web site via HTTP or HTTPS services, you need to add the following security group rules to the security group in which the instance is located.

-   VPC: assume that all IP addresses on the Internet are allowed to access your web site, add the security group rules shown in the following table.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |VPC|N/A|Inbound|Allow|HTTP\(80\)|80/80|Address Field Access|0.0.0.0/0|1|
    |HTTPS\(443\)|443/443|
    |Custom TCP|Custom, like 8080/8080|

-   Classic Network: assume that all IP addresses on the Internet are allowed to visit your website, add the security group rules shown in the following table.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |Classic Network|Internet|Inbound|Allow|HTTP\(80\)|80/80|Address Field Access|0.0.0.0/0|1|
    |HTTPS \(443\)|443/443|
    |Custom TCP|Customize, such as 8080/8080|


**Note:** 

-   If you are unable to access your instance via `http://Public IP address`, see [Check the TCP port 80 .](https://www.alibabacloud.com/help/faq-detail/59367.htm)

