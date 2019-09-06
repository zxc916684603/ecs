# ECS data security best practices {#concept_51404_zh .concept}

This topic describes the recommended best practices for improving the data security of ECS instances from an O&M perspective.

## Best practices {#section_kwg_dv2_2fb .section}

-   Back up data regularly
-   Design security domains
-   Set security group rules
-   Set logon passwords
-   Improve server port security
-   Protect application vulnerabilities
-   Collect security information

## Back up data regularly {#section_nwg_dv2_2fb .section}

Backing up data regularly reduces the risks of data loss due to system failures, operation errors, and security problems. The snapshot backup function of ECS instances can be used as a means to backup data regularly. To use this function, you must first customize a backup policy by performing one of the following operations:

-   [Create a snapshot](../../../../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#).
-   Define automatic snapshot policies and [apply automatic snapshot policies to disks](../../../../reseller.en-US/Snapshots/Automatic snapshot policies/Apply or disable an automatic snapshot policy.md#).

Next, you need to create automatic snapshots regularly, such as on a daily basis, and then store snapshots for a period of at least seven days. This will significantly increase disaster tolerance, minimizing potential data losses.

## Design security domains {#section_pwg_dv2_2fb .section}

You can use VPCs to build private networks, or intranets, that separate servers of different security levels in your enterprise. This prevents servers from affecting each other over an interconnected network.

## Set security group rules {#section_qwg_dv2_2fb .section}

You can use security groups to set network access control for one or more ECS instances. By using security groups, you can set firewall policies at the instance level, which allow you to control the access to and from an instance over the network. Specifically, you can restrict the inbound and outbound access on a port, and allow or deny access to and from specific IP addresses.

To learn more about security groups, see [Application cases](../../../../reseller.en-US/Security/Security groups/Scenarios.md#). If you require additional security options, we recommend that you use third-party VPN products to encrypt the logon data. You can purchase software in .

Consider the following example. By default, the remote access port for Linux ECS instances is port 22. This port does not provide direct access to the Internet. To enable an instance to access the Internet, you can set up a security group to control the access authorization of ECS instances, such as by authorizing the access of fixed IP addresses to the Internet.

To learn more about security groups, see [Application cases](../../../../reseller.en-US/Security/Security groups/Scenarios.md#). If you require additional security options, we recommend that you use third-party VPN products to encrypt the logon data. You can purchase software in .

## Set strong logon passwords {#section_swg_dv2_2fb .section}

We recommend that you set a strong server password to make your services more secure. To meet the password conventions of most Alibaba Cloud services, we recommend that you set each password to at least eight characters in length and include the following character types: uppercase letters, lowercase letters, numbers, and special characters. We also recommend that you change your password at least once every six months.

## Improve server port security {#section_twg_dv2_2fb .section}

To ensure that your servers are securely connected to the Internet, we recommend that you open only required ports as needed, and that you use only custom ports \(port number 30000 or higher\). Additionally, we recommend that access control is also implemented on service ports.

For example, we recommend that you restrict database services to an intranet for most general scenarios. However, if your services require access to the Internet, we recommend that you change the original connection port from 3306 to a higher port number and authorize the relevant IP addresses according to your service requirements.

## Install a Web Application Firewall \(WAF\) {#section_bts_32f_2fb .section}

We recommend that you install a [Web Application Firewall \(WAF\)](../../../../reseller.en-US/Quick Start/Quick start.md#) to prevent potential attacks due to application vulnerabilities. Installing one ensures the security and availability of your services in the cloud.

Application vulnerability are security defects that hackers may exploit to illegally access data. Some common application vulnerabilities include SQL injection, XSS attacks, illegal HTTP requests, and unauthorized access to core files.

Application design alone cannot guarantee protection from such vulnerabilities, therefore it is important that you make sure to install a WAF for this purpose.

