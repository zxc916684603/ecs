# Typical application of security group rules {#concept_fg1_y2t_xdb .concept}

This article introduces the typical application of security group rules. Documentation applies to both classic and VPC network instances. For specific actions to add security group rules, refer to the Documentation :.

The typical applications listed in this article include:

-   [SSH remote connection to Linux instances](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#sshLinux)
-   [RDP remote connection windows instance](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#rdpWindows)
-   [Public Network Ping ECs instance](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#ping)
-   [ECS instance as a Web Server](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#web)
-   [Upload or download files using FTP](intl.en-US/User Guide/Security groups/Typical application of security group rules.md#ftp)

## SSH remote connection to Linux instances {#sshLinux .section}

Once you 've created a Linux ECs instance, you can connect to the ECS instance remotely for SSH, you need to add the following security group rules:

|Network types|Network Card Type|Rule direction|Authorization Policy|Protocol Type|Port range|Authorization type|Authorization object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|SSH \(22\)|22/22|Address segment access|0.5.0.0/0|1|
|Classic network|Alibaba Cloud|

## RDP remote connection windows instance {#rdpWindows .section}

After the Windows ECs instance has been created, connect to the ECS instance remotely for RDP, you need to add the following security group rules:

|Network Type|Network Card Type|Rule direction|Authorization Policy|Protocol Type|Port range|Authorization type|Authorization object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|RDP \(3389\)|3389/3389|Address segment access|0.5.0.0/0|1.|
|Classic Network|Public Network|

## Public Network Ping ECs instance {#ping .section}

After creating the ECS instance, in order to use Ping program to test the communication status between the ECS instances, you need to add the following security group rules:

|Network Type|Network Card Type|Rule direction|Authorization Policy|Protocol Type|Port range|Authorization type|Authorization object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|ICMP|-1/-1|Address segment or security group access|Fill in according to license type, reference.|1.|
|Classic Network|Public Network|

## ECS instance as a Web Server {#web .section}

If the instance you created is used by the Web server, you need to install the Web server program on the instance, add the following security group rules.

**Note:** 

You need to start the Web server program before checking that the 80 ports are working properly. For detailed operation, refer to the Documentation: check if the TCP 80 port is working properly.

|Network Type|Network Card Type|Rule direction|Authorization Policy|Protocol Type|Port range|Authorization type|Authorization object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|HTTP \(80\)|80/80|Address segment access|0.5.0.0/0|1.|
|Classic Network|Public Network|

If you are unable to access your instance via http: // public network IP address, please refer to check if the TCP 80 port is working properly.

## Upload or download files using FTP {#ftp .section}

If you need to use the FTP software to upload or download files to the ECS instance, you need to add the following security group rules:

**Note:** 

You need to install the FTP server program on the instance before checking that port 20/21 is working properly. To install the FTP server program, you can refer to the documentation: the configuration and use of the FTP service under the cloud server ECS.

|Network Type|Network Card Type|Rule direction|Authorization Policy|Protocol Type|Port range|Authorization type|Authorization object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|Custom TCP|20/21|Address segment access|0.5.0.0/0|1.|
|Classic Network|Public Network|

