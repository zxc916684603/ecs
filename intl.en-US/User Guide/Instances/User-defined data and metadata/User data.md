# User data {#concept_fgf_tjn_xdb .concept}

User data is provided by ECS for you to customize the startup behaviors of an ECS instance and to pass data into an ECS instance. You can specify instance user data when creating an instance \([RunInstances](../../../../intl.en-US/API Reference/Instances/RunInstances.md#)\) to customize startup behavior for your instance. For example, automatically update software packages, enable services, print logs, install dependencies, initialize Web services, and other actions that configure your instances. Instance user data is implemented primarily through different types of scripts. User data can also be used as common data to be referenced in the instances.

## Instructions for use {#instructions .section}

To configure instance user data, note that:

-   Only VPC-Connected instances are supported.

-   For [phased-out instance types](https://www.alibabacloud.com/help/faq-detail/55263.htm), they must be I/O optimized. Others [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#) are not limited for I/O optimized.

-   Instance user data requires Base64 encoding before being passed in, and the pre-encoding user data cannot exceed 16 KB.

-   The instance must use an official image or a user image that is created from an official image. The operating system must be one of the followings:

    |Windows instances:|Linux instances:|
    |:-----------------|:---------------|
    |Windows Server 2016 64-bit Windows Server 2012 64-bit Windows Server 2008 64-bit|CentOS Ubuntu SUSE Linux Enterprise OpenSUSE Debian Aliyun Linux|


## Module frequency {#section_uf5_ryn_xdb .section}

After the instance starts to running \(**Running**\), we first run the instance user data with the administrator or root permission, followed by the initialization or `/etc/init` information.

After you modify the instance user data, whether the modified user data will be run again or not depends on the type of scripts and modules. For example:

-   If you configure user data by using a shell script, such as a [user-data script](#User-DataScript), we will not run the modified user data.

-   If the user data configures modules like Byobu, Set Hostname, and Set Passwords, we will not run the modified user data.

-   If the user data configures modules like bootcmd, update\_etc\_hosts, and yum\_add\_repo, we will run the modified user data.

    For more information, see the cloud-init documentation [Modules](http://cloudinit.readthedocs.io/en/latest/topics/modules.html) and pay attention to the module frequency.


## Set user data {#SetUserDataExample .section}

Assume that you write user data development environment is Windows computer, and you use [Upstart Job](#UpstartJob) to configure the user data.

1.  Use the editor to create a text file, such as NotePad ++.
2.  Edit the script related to user data in the text file.

    **Note:** The first line must meet the format requirements of the instance user data script, such as \#! /bin/sh, \#cloud-config, \#upstart-job, \[bat\] and \[powershell\]. For more information , see [Linux instance user data](#linuxCustomScripts) and [Windows instance user data](#windowsCustomScripts).

3.  Debug the script file to confirm that the content is correct.
4.  \(Optional\) If you make a [Gzip compression content](#Gzip), compress the script file in .gz format.
5.  \(Optional\) If you are creating an [Include file](#Include) or a [Gzip compression script](#Gzip), upload script file to available storage services, obtain the link, and set the valid period of the link.

    We recommend that you use the Alibaba Cloud OSS to create links. For more information, see OSS [Upload an object](../../../../intl.en-US/Quick Start/Upload an object.md#) or [Set lifecycle](../../../../intl.en-US/Console User Guide/Manage buckets/Set lifecycle.md#).

6.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
7.  See  [Step 2. Create an instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#) Create a Linux instance.

    **Note:** The instance must be VPC-Connected, and you need to select a [image](#Image) that is compliant with the requirement. For [phased-out instance types](https://www.alibabacloud.com/help/faq-detail/55263.htm), I/O optimized instances are required. Other [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#) are not limited in terms of I/O optimized.

    After creating the instance, select  **Advanced \(based on instance RAM roles or cloud-init\) use text form**, enter your **user data**. If your user data has been encrypted by Base64, click **The text is Base64-encoded**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9660/5484_en-US.png)

8.  Waits for creating the instance.
9.  After the instance is launched, see [Overview](intl.en-US/User Guide/Connect/Overview.md#) to connect to your instance.
10. View the results of the user data. If a failure occurs, check the relevant log files. The following is an output example of user data on a CentOS instance by using the upstart job script:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9660/5485_en-US.png)

    For example, in the /etc/init folder, a startup job file part-001.conf is generated.


Related API: [RunInstances](../../../../intl.en-US/API Reference/Instances/RunInstances.md#) + Parameters `UserData`

## View user data {#linuxCustomData .section}

You can view instance user data from the server `100.100.100.200` .

1.  Connect to the instance.
2.  In the instance, run:
    -   `curl http://100.100.100.200/latest/user-data` View the user data of a Linux instance:
    -   `Invoke-RestMethod http://100.100.100.200/latest/user-data/` View the user data of a Windows instance:

Related APIs:[DescribeUserdata](../../../../intl.en-US/API Reference/Instances/DescribeUserdata.md#)

## Modify user data {#linuxCustomData2 .section}

You must stop the instance in advance. If you need to restart a Pay-As-You-Go VPC-Connected instance immediately after you modify the user data, we recommend that you disable the No fees for stopped instances option.

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Select the target instance, and in the **Actions** column, click **Sets User Data**.
5.  Enter After you fill in the information in the burst window, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9660/5486_en-US.png)


**Note:** After you modify the user data, whether you want to re-run the modified user data depends on the script type and the module type.

Related API: [ModifyInstanceAttribute](../../../../intl.en-US/API Reference/Instances/ModifyInstanceAttribute.md#) + Parameters `Userdata`

## Linux instance user data {#linuxCustomScripts .section}

Linux instance user data can be performed by several types of script, such as [User-data Script](#User-DataScript), [Cloud Config](#CloudConfigData), [Include Files](#Include), [Gzip compression scripts](#Gzip), and  [Upstart Job](#UpstartJob) . The scripts follow the format of open source cloud-init, reference the [Metadata](intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#) for data sources. The configuration of Linux instances are automated at boot. For more information, see Cloud-init [Formats](http://cloudinit.readthedocs.io/en/latest/topics/format.html).

**User-data script**

User-data can be a shell script. It runs once at the instance first boot. The first line is fixed as `#!`, for example `#! /bin/sh`. The content of user-data script cannot exceed 16 KB before Base64 encoding. The following are examples of User-Data script:

```

#! /bin/sh
echo "Hello World. The time is now $(date -R)!" | tee /root/output10.txt
service httpd start
chkconfig httpd on
```

After the instance has been created, start and connect to the instance, and run `cat [file]` to view the results of the user-data script.

```

[root@XXXXX2z ~]# cat output.txt
Hello World. The time is now Mon, 24 Jul 2017 13:03:19 +0800!
```

**Cloud config**

Cloud Config is the easiest way to implement instance customization data, and its interaction is very friendly. You can use cloud Config to configure services such as updating yum sources, importing SSH keys, installing dependency packages, and so on. The first line of Cloud Config is fixed as `#cloud-config`, and the header cannot have spaces. The file must be yaml syntax valid. Depending on the service you configured, the instance user data runs differently.

Cloud Instance user data requires Base64 encoding before being passed in, and the pre-encoding cloud config data  cannot exceed 16 KB. See the following Cloud Config script example:

```

#cloud-config
apt:
primary:
- arches: [default]
uri: http://us.archive.ubuntu.com/ubuntu/
bootcmd:
- echo 192.168.1.130 us.archive.ubuntu.com >> /etc/hosts
```

After the instance has been created, start and connect to the instance to view the results.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9660/5487_en-US.png)

**Include files**

The contents of the include file consist of a script link, with one link on one line. When the instance starts, cloud-init reads the contents of the script link in the include file, once there is an error reading script content in a row, the instance stops performing user data. The first line of Include File is fixed as `#include` and the header cannot have spaces. The update frequency of the instance user data follows the script type configured in the include file.

Instance user data requires Vase64 encoding before being passed in, and the pre-encoding include file cannot exceed 16 KB. See the following include file for example:

```

#include
http://ecs-image-test.oss-cn-hangzhou.aliyuncs.com/UserData/myscript.sh
```

After the instance has been created, start and connect the instance to view the results.

**Gzip compressed content**

The content of [User-Data Script](#User-DataScript), [Cloud Config](#CloudConfigData), and [Include File](#Include) cannot exceed 16 KB. If your script content is more than 16 KB, you can use the Gzip compressed content. Upload the compressed script in available storage service and obtain the link and use the Include file format to render the link. The first line of Gzip compression script is fixed as `#include` and the header cannot have spaces. The update frequency of the instance user data follows the script type configured in the Gzip file. See the following Gzip compressed content for example:

```

#include
http://ecs-image-test.oss-cn-hangzhou.aliyuncs.com/userdata/config.gz
```

**Upstart Job**

Upstart service for your init system is required if you use Upstart Job to configure user data. For example, CentOS 6, Ubuntu 10/12/14, and Debian 6/7 use upstart as the init system. Upstart job script places your instance user data into a file in `/etc/init` directory. The first line of Upstart Job script is fixed as `#upstart-job` and the header cannot have spaces. We perform the instance user data for every instance boot. See the following Upstart Job script example:

```

#upstart-job
description "upstart test"
start on runlevel [2345]
stop on runlevel [! 2345]
exec echo "Hello World. The time is now $(date -R)!" | tee /root/output.txt
```

## Windows instance user data {#windowsCustomScripts .section}

Windows instance user data is a proprietary utility developed by ECS. We provide Windows instance with the ability to run initialization scripts. Instance user data requires base64 encoding before being passed in, and the pre-encoding user data cannot exceed 16 KB. Only SBC case characters are allowed. You can write Bat script or PowerShell script to configure the instance user data.

**Bat scripts**

The first line is fixed as `[bat]` and the header cannot have spaces. For example:

```

[bat]
echo "bat test" > c:\1.txt
```

After the instance has been created, start and connect the instance to view the results, A 1.txt text file is shown under the C:\\ drive.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9660/5488_en-US.png)

**The first line of PowerShell scripts**

is fixed as `[powershell]` and the header cannot have spaces. For example:

```

[powershell] 
write-output "Powershell Test" | Out-File C:\2.txt
```

## Reference {#Reference .section}

For more information about Linux instance user data, see cloud-init [Formats](http://cloudinit.readthedocs.io/en/latest/topics/format.html).

For more information about the update frequency of Linux instance user data, see cloud-init [Modules](http://cloudinit.readthedocs.io/en/latest/topics/modules.html).

