# Scenarios {#concept_ngr_vht_xdb .concept}

This topic describes several scenarios that use security groups. The scenarios include instances of both VPC and Classic network types.

**Note:** 

-   For information about how to create security groups and add security group rules, see [Create a security group](reseller.en-US/Security/Security groups/Create a security group.md#) and [Add a security group rule](reseller.en-US/Security/Security groups/Add security group rules.md#).
-   For information about relevant ports, see [Introduction to common ECS instance ports](reseller.en-US/Security/Security groups/Introduction to common ECS instance ports.md#).
-   For security group rule configurations of relevant ports, see [Typical applications of security group rules](reseller.en-US//Typical applications of security group rules.md#).

-   [Scenario 1: Enable intranet communication](#) 

    If you want to copy files between two Classic network-connected ECS instances owned by different accounts or located in different security groups, you can configure security group rules to enable communication between the instances through the intranet.

-   [Scenario 2: Allow remote connection to your ECS instance from specified IP addresses only](#) 

    You can modify the remote connection port and then configure security group rules to only allow access specified IP address access to your ECS instance.

-   [Scenario 3: Allow your ECS instance to access specified IP addresses only](#) 

    You can configure security group rules to allow your instance to access only specified IP addresses or ports.

-   [Scenario 4: Allow remote connection to your ECS instance](#) 

    You can configure security group rules to allow remote access to your ECS instance through the Internet or intranet.

-   [Scenario 5: Allow access to your ECS instance by using HTTP or HTTPS](#) 

    If you have built a website on your ECS instance, you can configure security group rules to allow users to access the website.

-   [Scenario 6: Deny your ECS instance to access specified external IP addresses](reseller.en-US/Security/Security groups/Scenarios.md#section_qtl_vhz_ngb)

    If you do not want your ECS instance to access specified external IP addresses, you can configure security group rules accordingly.


## Scenario 1: Enable intranet communication {#intranetCommunication .section}

You can create security group rules to allow communication between instances through the intranet in the following cases:

-   Case 1: The ECS instances belong to the same region and account.
-   Case 2: The ECS instances belong to the same region but to different accounts.

**Note:** 

-   For VPC-Connected ECS instances, if they are in the same VPC, you can configure their security group rules to implement intranet communication. If they are in different VPCs \(regardless of whether they are owned by the same account or located in the same region\), you can use Express Connect to implement intranet communication. For more information, see [**Interconnect two VPCs under different accounts**](https://www.alibabacloud.com/help/doc-detail/44842.htm).

**Case 1: The ECS instances belong to the same region and account**

By default, two instances located in the same region and owned by the same account can communicate with each other through the intranet. If the instances are in different security groups, you can configure security group rules to enable intranet communication according to the network type.

-   VPC

    If the instances are in the same VPC, add a rule to each security group to authorize mutual access between the security groups. The rule settings are described as follows.

    |NIC|Rule direction|Authorization policy|Protocol type|Port range|Priority|Authorization type|Authorization object|
    |:--|:-------------|:-------------------|:------------|:---------|:-------|:-----------------|:-------------------|
    |Not required|Inbound|Allow|Select the required protocol.|Set the required port range.|1|Security group access \(authorize this account\)|Select the ID of the security group to which the instance to be accessed belongs.|

-   Classic network

    Add a rule to each security group to authorize mutual access between the security groups. The rule settings are described as follows.

    |NIC|Rule Direction|Authorization Policy|Protocol Type|Port Range|Priority|Authorization Type|Authorization Object|
    |:--|:-------------|:-------------------|:------------|:---------|:-------|:-----------------|:-------------------|
    |Intranet|Inbound|Allow|Select the required protocol.|Set the required port range.|1|Security group access \(authorize this account\)|Select the ID of the security group to which the instance to be accessed belongs.|


**Case 2: The ECS instances belong to the same region but to different accounts**

The information in this case is for Classic network-connected ECS instances only.

Add a rule to each security group to authorize mutual access between the security groups. For example:

-   User A owns a Classic network-connected ECS instance in China East 1, named Instance A \(The intranet IP address is A.A.A.A\), which belongs to the security group A \(Group A\).
-   User B owns a Classic network-connected ECS instance in China East 1, named Instance B \(The intranet IP address is B.B.B.B\), which belongs to the security group B \(Group B\).

1.  Add a rule to Group A to authorize Instance B to access Instance A. The rule settings are described as follows.

    |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Intranet|Inbound|Allow|Select the required protocol.|Set the required port range.|Security group access \(authorize other accounts\) |Enter the account ID of User B and the security group ID of Group B.|1|

2.  Add a rule to Group B to authorize Instance A to access Instance B. The rule settings are described as follows.

    |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Intranet|Inbound|Allow |Select the required protocol.|Set the required port range.|Security group access \(authorize other accounts\)|Enter the account ID of User A and the security group ID of Group A|1|

    **Note:** To guarantee instance security, when you set an intranet inbound rule for the Classic network, **Security Group Access** is the top priority for **Authorization Type**. If you select **Address Field Access**, only a single IP address can be authorized and the authorized object must be in the format of a.b.c.d/32. The IP address can be set as needed, but only IPv4 is supported. The subnet mask must be /32.


## Scenario 2: Allow remote connection to your ECS instance from specified IP addresses only {#specifyIpAccess .section}

If you want to allow remote connection to your instance from specified IP addresses only, add the following rule. In this example, remote connection to an instance on TCP port 22 from a specified IP address is allowed.

|Network type|NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
|:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
|VPC|Not required|Inbound|Allow|SSH\(22\)|22/22|Address field access|IP addresses that allow remote access, such as 1.2.3.4|1|
|Classic network|Internet|

## Scenario 3: Allow your ECS instance to access specified IP addresses only {#specifyInstanceAccess .section}

If you want your ECS instance to access specified IP addresses, add the following rules to its security group.

1.  Add the following rule to deny your instance to access any public IP addresses. The priority \(for example, 2\) must be lower than the rule in step 2.

    |Network type|NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |VPC|Not required|Outbound|Drop|All|-1/-1|Address field access|0.0.0.0/0|2|
    |Classic network|Internet|

2.  Add the following rule to allow your instance to access the specified IP address, with a higher priority than that in step 1.

    |Network type|NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |VPC|Not required|Outbound|Allow|Select the required protocol.|Set the required port range.|Address field access|Enter the specified IP address, for example, 1.2.3.4|1|
    |Classic network|Internet|


After you add the rules, connect to the instance and try to `ping` it or `telnet` to the instance from the specified IP address. If the instance can be accessed, the rule is successfully applied.

## Scenario 4: Allow remote connection to your ECS instance {#allowRemoteAccess .section}

You can allow remote connection to your instance in the following cases:

-   Case 1: Allow remote connection to your instance from the Internet.
-   Case 2: Allow remote connection to your instance from the intranet.

**Case 1: Allow remote connection to your instance from the Internet**

To allow remote connection to your instance from the Internet, add the following rule based on the network type and the operating system of your instance:

-   VPC

    |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Not required|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address field access|To allow Internet access from any public IP address, enter 0.0.0.0/0. To allow Internet access from a specified public IP address, see [Scenario 2](#).|1|
    |Linux: SSH \(22\)|22/22|
    |Custom TCP|Custom|

-   Classic network

    |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
    |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
    |Internet|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address field access|To allow Internet access from any public IP address, enter 0.0.0.0/0. To allow Internet access from a specified public IP address, see [Scenario 2](#).|1|
    |Linux: SSH\(22\)|22/22|
    |Custom TCP|Custom|


To customize the port for remote connection, see [Modify the default remote access port](https://partners-intl.aliyun.com/help/doc-detail/51644.htm).

**Case 2: Allow remote connection to your instance from the intranet**

If you have enabled intranet communication between instances that belong to the same region but to different accounts, and you want to allow the instances in a security group under a different account to connect to your instance, add the following rules as needed.

-   To allow an intranet IP address to connect to your instance:
    -   VPC

        Make sure that you have established intranet communication between both accounts by using [Express Connect](https://www.alibabacloud.com/help/doc-detail/44843.htm), and then add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Not required|Inbound|Allow|Windows: RDP\(3389\)|3389/3389|Address field access|Specify the private IP address of the peer instance.|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Custom|

    -   Classic network

        Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Address field access|Specify the private IP address of the peer instance. To guarantee instance security, only an IP address with the CIDR prefix `/32` in the format of a.b.c.d/32 is allowed.|1|
        |Linux: SSH \(22\)|22/22|
        |Custom TCP|Custom|

-   To allow all instances in a security group under a different account to connect to your instance:
    -   VPC

        Make sure that you have established intranet communication between both accounts by using [Express Connect](https://www.alibabacloud.com/help/doc-detail/44843.htm), and then add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Not required|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security group access \(authorize other accounts\)|Enter the account ID and the security group ID of the peer instance.|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Custom|

    -   Classic network

        Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Intranet|Inbound|Allow|Windows: RDP \(3389\)|3389/3389|Security group access \(authorize other accounts\)|Enter the account ID and the security group ID of the peer instance.|1|
        |Linux: SSH\(22\)|22/22|
        |Custom TCP|Custom|


## Scenario 5: Allow access to your ECS instance by using HTTP or HTTPS {#allowHttp .section}

If you have built a website on your instance and want to allow users to visit the website through HTTP or HTTPS, add the following rules as needed.

-   To allow all IP addresses to access your website:
    -   VPC: Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Not required|Inbound|Allow|HTTP\(80\)|80/80|Address field access|0.0.0.0/0|1|
        |HTTPS\(443\)|443/443|
        |Custom TCP|Custom, for example, 8080/8080|

    -   Classic network: Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Internet|Inbound|Allow|HTTP\(80\)|80/80|Address field access|0.0.0.0/0|1|
        |HTTPS \(443\)|443/443|
        |Custom TCP|Custom, for example, 8080/8080|

-   To allow some public IP addresses to access your website:

    -   VPC: Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Not required|Inbound|Allow|HTTP\(80\)|80/80|Address field access|Specify one or more public IP addresses that you allow to access your website.|1|
        |HTTPS\(443\)|443/443|
        |Custom TCP|Custom, for example, 8080/8080|

    -   Classic network: Add the following rule.

        |NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
        |:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
        |Internet|Inbound|Allow|HTTP\(80\)|80/80|Address field access|Specify one or more public IP addresses that you allow to access your website.|1|
        |HTTPS \(443\)|443/443|
        |Custom TCP|Custom, for example, 8080/8080|


**Note:** 

-   If users cannot access your instance by using `http://Public IP address`, [verify if TCP port 80 works properly](https://partners-intl.aliyun.com/help/faq-detail/59367.htm).
-   TCP port 80 is the default port for HTTP services. If you want to use other ports, such as port 8080, you must modify the listening port settings in the configuration file of the Web server.

## Scenario 6: Deny your ECS instance to access specified external IP addresses {#section_qtl_vhz_ngb .section}

If you do not want your ECS instance to access an external IP address, add the following rule to the security group to which your instance belongs:

|Network type|NIC|Rule direction|Authorization policy|Protocol type|Port range|Authorization type|Authorization object|Priority|
|:-----------|:--|:-------------|:-------------------|:------------|:---------|:-----------------|:-------------------|:-------|
|VPC|Not required|Outbound|Drop|All|-1/-1|Address field access|Specify the public IP address that you deny your instance to access, for example, 1.2.3.4.|1|
|Classic network|Internet|

