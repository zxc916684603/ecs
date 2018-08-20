# Scenarios {#concept_ngr_vht_xdb .concept}

This article introduces several common scenarios of of VPC-connected and classic network-connected security groups.

**Note:** For more information about how to create a security group and its rules, see [Create a security group](intl.en-US/User Guide/Security groups/Creating a Security Group.md#) and [Add a security group rule](intl.en-US/User Guide/Security groups/Add security group rules.md#).

-   [Scenario 1: Enable intranet communication](#intranetCommunication) 

    Example: If you want to copy files between two classic network-connected ECS instances owned by different accounts or in different security groups, you can enable intranet communication between both instances by configuring security group rules and then copy files.

-   [Scenario 2: Allow remote connection from a specified IP address only](#specifyIpAccess) 

    Example: When your ECS instance is compromised by hackers as a zombie, you can modify the port for remote connection, and configure security group rules to allow access from a specified IP address only.

-   [Scenario 3: Allow an instance to access a specified IP address only](#specifyInstanceAccess) 

    Example: When your ECS instance is compromised by hackers as a zombie and scan or send packets maliciously, you can configure security group rules to allow the instance to access to a specified IP address.

-   [Scenario 4: Allow remote connection to an ECS instance](#allowRemoteAccess) 

    Example: You can connect to an ECS instance by configuring a security group rule.

-   [Scenario 5: Allow access to an ECS instance over HTTP or HTTPS service](#allowHttp) 

    Example: If you build a website on your instance, you can configure security group rules to enable your users to access the website.


## Scenario 1: Enable intranet communication {#intranetCommunication .section}

Security group rules can be used in the following cases to enable intranet communication between ECS instances that belong to different accounts or security groups in the same region:

-   Case 1: Instances belong to one region and one account
-   Case 2: Instances belong to one region but different accounts

**Note:** For VPC-Connected ECS instances,

-   If they are in one VPC, you can configure their security group rules to enable intranet communication.
-   If they are in different VPCs, or owned by different accounts in the same region, Express Connect is the only option to establish intranet communication. For more information, see [Establish an intranet connection between VPCs under different accounts](https://www.alibabacloud.com/help/doc-detail/44842.htm).

**Case 1: Instances belong to one region and one account**

For two instances in one region but owned by one account, if they are in one security group, intranet communication is enabled by default. If they are in different security groups, you must configure security group rules to enable intranet communication according to the network types.

-   VPC

    If they are in one VPC, add a rule in their security groups respectively to authorize the security groups to access each other. The rule must be as follows.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type|Authorization Object|
    |:--|:-------------|:-------------------|:------------|:---------|:-------|:-----------------|:-------------------|
    |N/A|Inbound|Allow|Select the required protocol|Set the required port range|1|Security Group Access \(Authorize This Account\)|Select the Security Group ID on which you want to allow access to the instance|

-   Classic network

    Add a rule in their security groups respectively to authorize the security groups to access each other. The rule must be as follows.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type| Authorization Object|
    |:--|:-------------|:-------------------|:------------|:---------|:-------|:-----------------|:--------------------|
    |Intranet|Inbound|Allow|Select the required protocol|Set the required port range|1|Security Group Access \(Authorize This Account\)|Type the other security group ID|


**Case 2: Instances belong to one region but different accounts**

For classic network-connected ECS instances only.

Authorize the security groups to access each other. For example:

-   UserA owns a classic network-connected ECS instance in the East China 1 region, named InstanceA, with the private IP address A.A.A.A. The security group is GroupA.
-   UserB owns a classic network-connected ECS instance in the East China 1 region, named InstanceB, with the private IP address B.B.B.B. The security group is GroupB.
-   Add a rule in GroupA to authorize access of InstanceA to InstanceB, as shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Intranet|Inbound|Allow|Select the required protocol |Set the required port range|Security Group Access \(Authorize Other Account\) |Type the account ID of UserB and the security group ID of GroupB|1|

-   Add a rule in GroupB to authorize access of InstanceB to InstanceA, as shown in the following table.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Intranet|Inbound|Allow |Select the required protocol|Set the required port range|Security Group Access \(Authorize Other Account\)|Type the account ID of UserA and the security group ID of GroupA|1|

    **Note:** To guarantee the security of your instances, when you are configuring an intranet inbound rule for a classic network-connected security group, **Security Group Access** is the top priority for **Authorization Type**. If you select **Address Field Access**, you must enter an IP address with CIDR prefix, `/32`”, in the format of a.b.c.d/32. Only IPv4 is supported.


## Scenario 2: Allow remote connection from a specified IP address only {#specifyIpAccess .section}

If you want to allow remote connection to your instance from the specified public IP addresses, add the following rule. In this example, we allow remote connection to an instance on TCP Port 22 from a specified IP address.

|Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
|VPC|N/A|Inbound|Allow|SSH\(22\)|22/22|Address Field Access|The IP address to allow access, such as 1.2.3.4.|1|
|Classic Network|Internet|

## Scenario 3: Allow an instance to access a specified IP address only {#specifyInstanceAccess .section}

If you want your instance to access a specified IP address, add the following rules in its security group.

1.  Add the following rule to drop any access to all public IP addresses. The priority must be lower than the rule in step 2.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |VPC|N/A|Inbound|Drop|All|-1/-1|Address Field Access|0.0.0.0/0|2|
    |Classic Network|Internet|

2.  Add the following rule to allow access to the specified IP address, with a higher priority than that in step 1.

    |Network Type|NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |VPC|N/A|Outbound|Allow|Select the required protocol|Set the required port range|Address Field Access|Type the specified IP address, such as 1.2.3.4|1|
    |Classic Network|Internet|


After you add the rules, connect to the instance and try to ping or telnet the instance from the specified IP address and other IP addresses. If the instance can be accessed by the specified IP address, it means the rules work.

## Scenario 4: Allow remote connection to an ECS instance {#allowRemoteAccess .section}

You may want to connect to your instance in the following cases:

-   Case 1: Allow remote connection to your instance from Internet
-   Case 2: Allow remote connection to your instance from intranet

**Case 1: Allow remote connection to your instance from Internet**

To allow remote connection to your instance from Internet, add the following rule according to the network type and the operating system of your instance.

-   VPC

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |N/A|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|To allow Internet access from any public IP address, type 0.0.0.0/0. To allow Internet access from a specified Internet IP address, see [Scenario 2](#specifyIpAccess).|1|
    |Linux: SSH \(22\)|22/22|
    |Custom TCP|Customized|

-   Classic Network

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Internet|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|To allow Internet access from any public IP address, type 0.0.0.0/0. To allow Internet access from a specified Internet IP address, see [Scenario 2](#specifyIpAccess).|1|
    |Linux: SSH\(22\)|22/22|
    |Custom TCP|Customized|


To customize the port for remote connection, see Modify the default remote access port.

To customize the port for remote connection, see [Modify the default remote access port](https://www.alibabacloud.com/help/doc-detail/51644.htm).

**Case 2: Allow remote connection to your instance from intranet**

If you have enabled intranet communication between instances that belong to one region but different accounts, and you want to allow the instances in different security groups to connect to each other, add the following rules as needed.

-   To allow a private IP address to connect to an instance.
    -   VPC

        Make sure that intranet communication has been built between both accounts by using [Express Connect](https://www.alibabacloud.com/help/doc-detail/44843.htm), and then add any one of the following rule.

        |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |N/A|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address Field Access|Specify the private IP address of the peer instance|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Customized|

    -   Classic Network

        Add any one of the following rules.

        |NIC|Rule direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Address Field Access|Specify the private IP address of the peer instance. To secure the instance, only an IP address with CIDR prefix, `/32`, in the format of a.b.c.d/32, is allowed.|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Customized|

-   To allow all the instances in a security group of one account to connect to your instance:
    -   VPC

        Make sure that intranet communication is built between both accounts by using [Express Connect](https://www.alibabacloud.com/help/doc-detail/44843.htm), and then add any one of the following rules.

        |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |N/A|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security Group Access \(Authorize Other Account\)|Type the account ID of the peer and the security group ID|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Customized|

    -   Classic network

        Add any one of the following rules.

        |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security Group Access \(Authorize Other Account\)|Type the account ID of the peer and the security group ID|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Customized|


## Scenario 5: Allow access to an ECS instance over HTTP or HTTPS service {#allowHttp .section}

If you have built a website on your instance and expect your users to visit the site over HTTP or HTTPS service, add any one of the following rules.

-   VPC

    To allow all public IP addresses to access your site, add any one of the following rules.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |N/A|Inbound|Allow|HTTP\(80\)|80/80|Address Field Access|0.0.0.0/0|1|
    |HTTPS\(443\)|443/443|
    |Custom TCP|Customized, such as 8080/8080|

-   Classic Network

    To allow all public IP addresses to access your site, add any one of the following rules.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Internet|Inbound|Allow|HTTP\(80\)|80/80|Address Field Access|0.0.0.0/0|1|
    |HTTPS \(443\)|443/443|
    |Custom TCP|Customized, such as 8080/8080|


**Note:** 

-   If your users cannot access your instance by using `http://Public IP address`, [verify if TCP port 80 works properly](https://www.alibabacloud.com/help/faq-detail/59367.htm)
-   TCP Port 80 is the default port for HTTP service. If you want to use other ports, modify the port in the configuration file of the Web server.

