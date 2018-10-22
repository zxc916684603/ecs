# Typical applications of security group rules {#concept_fg1_y2t_xdb .concept}

This article introduces the typical applications of security group rules. It applies to instances in classic and VPC network.

The typical applications listed in this article include:

-   [Use SSH to connect to Linux instances remotely](reseller.en-US/User Guide/Security groups/Typical applications of security group rules.md#sshLinux)
-   [Use RDP to connect to Windows instances remotely](reseller.en-US/User Guide/Security groups/Typical applications of security group rules.md#rdpWindows)
-   [Ping ECS instances in public network](reseller.en-US/User Guide/Security groups/Typical applications of security group rules.md#ping)
-   [Use ECS instances as Web servers](reseller.en-US/User Guide/Security groups/Typical applications of security group rules.md#web)
-   [Use FTP to upload or download files](reseller.en-US/User Guide/Security groups/Typical applications of security group rules.md#ftp)

## Use SSH to connect to Linux instances remotely {#sshLinux .section}

After you create a Linux ECS instance, you can use SSH to connect to the ECS instance remotely. Add the following security group rules.

|Network Types|Network Card Type|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|SSH \(22\)|22/22|Address segment access|0.0.0.0/0|1|
|Classic network|Alibaba Cloud|

## Use RDP to connect to Windows instances remotely {#rdpWindows .section}

After the Windows ECS instance has been created, use RDP to connect to the ECS instance remotely. Add the following security group rules.

|Network Type|Network Card Type|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|RDP \(3389\)|3389/3389|Address segment access|0.0.0.0/0|1|
|Classic network|Public network|

## Ping ECS instances in public network {#ping .section}

After creating the ECS instance, use Ping program to test the communication status between the ECS instances. Add the following security group rules.

|Network Type|Network Card Type|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|ICMP|-1/-1|Address segment or security group access|Fill it in according to license type, see [add security group rules](reseller.en-US/User Guide/Security groups/Add security group rules.md#).|1|
|Classic network|Public network|

## Use ECS instances as Web servers {#web .section}

If you use your instance as a Web server, install the Web server program on the instance, and add the following security group rules.

**Note:** 

Start the Web server program, and verify if port 80 works properly.

|Network Type|Network Card Type|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|HTTP \(80\)|80/80|Address segment access|0.0.0.0/0|1|
|Classic network|Public network|

If you cannot access your instance through the http://public network IP address, verify if the TCP port 80 works properly.

## Use FTP to upload or download files {#ftp .section}

To use FTP to upload/download files to/from the ECS instance, add the following security group rules.

**Note:** 

You must install the FTP program on the instance, and verify if port 20/21 works properly.

|Network Type|Network Card Type|Rule Direction|Authorization Policy|Protocol Type|Port Range|Authorization Type|Authorization Object|Priority|
|VPC network|No configuration required|Direction of entry|Allow|Custom TCP|20/21|Address segment access|0.0.0.0/0|1|
|Classic network|Public network|

