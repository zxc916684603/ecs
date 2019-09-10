# O&M and monitoring FAQ {#concept_zbs_spr_wgb .concept}

This topic lists questions related to ECS operation & maintenance and monitoring.

-   Cloud Assistant FAQ
    -   [What is Cloud Assistant?](#section_bkd_r3h_vgb)
    -   [How can I use Cloud Assistant?](#section_ss2_4bh_vgb)
    -   [What operating system is Cloud Assistant supported on?](#section_ts2_4bh_vgb)
    -   [How many Cloud Assistant commands can I have in an Alibaba Cloud region?](#section_ws2_4bh_vgb)
    -   [Can I modify a created Cloud Assistant command?](#section_xs2_4bh_vgb)
    -   [Do I need any permissions to run Cloud Assistant commands on ECS instances?](#section_ys2_4bh_vgb)
    -   [Can I run Cloud Assistant commands on multiple instances at the same time?](#section_at2_4bh_vgb)
    -   [How can I check the execution results of Cloud Assistant commands?](#section_bt2_4bh_vgb)

## What is Cloud Assistant? {#section_os2_4bh_vgb .section}

Cloud Assistant provides native O&M and deployment services in Alibaba Cloud ECS. This tool supports a visualized console and API operations. With Cloud Assistant, you can run Bat, PowerShell, or Shell commands in batches without the need to connect to an instance. For more information, see [Cloud Assistant](../reseller.en-US/Deployment & Maintenance/Cloud assistant/Cloud assistant overview.md).

## How can I use Cloud Assistant? {#section_ss2_4bh_vgb .section}

You can use Cloud Assistant through [ECS console](https://partners-intl.console.aliyun.com/#/ecs) or by calling the [API](../reseller.en-US/API Reference/Cloud assistant/CreateCommand.md#) operation.

## What operating system is Cloud Assistant supported on? {#section_ts2_4bh_vgb .section}

Cloud Assistant is supported on the following operating systems:

-   Windows: Windows Server 2008, 2012, and 2016
-   Unix: Ubuntu 12, 14, and 16, CentOS 5, 6, and 7, Debian 7, 8, and 9, RedHat 5, 6, and 7, SUSE Linux Enterprise Server 11 and 12, OpenSUSE, Aliyun Linux, and CoreOS

**Note:** 

-   The Cloud Assistant client is pre-installed on instances created from ECS public images.
-   For instances created by using custom images or Alibaba Cloud Marketplace images, you must first verify that operating systems on these instances support Cloud Assistant, and then [configure the Cloud Assistant client](../reseller.en-US/Deployment & Maintenance/Cloud assistant/Configure the cloud assistant client.md#).

## How many Cloud Assistant commands can I have in an Alibaba Cloud region? {#section_ws2_4bh_vgb .section}

You can have a maximum of 100 to 10,000 Cloud Assistant commands in an Alibaba Cloud region, depending on the usage of ECS instances.

## Can I modify a created Cloud Assistant command? {#section_xs2_4bh_vgb .section}

You can modify the name and description of a command, but other information such as the script content, expiration time, and execution path cannot be modified.

If you want to modify the script content or execution path, you can [clone the command](../reseller.en-US/Deployment & Maintenance/Cloud assistant/Use the cloud assistant/Manage commands.md#CopyCommands) to create a new version of the command based on the existing command.

## Do I need any permissions to run Cloud Assistant commands on ECS instances? {#section_ys2_4bh_vgb .section}

Yes. You must install and use Cloud Assistant as an administrator or the root user.

-   To run commands on Windows instances, you must have administrator permissions.
-   To run commands on Linux instances, you must have root permissions.

## Can I run Cloud Assistant commands on multiple instances at the same time? {#section_at2_4bh_vgb .section}

Yes. You can run Cloud Assistant commands on up to 50 instances at a time. In an Alibaba Cloud region, you can run a maximum of 5,000 Cloud Assistant commands each day.

## How can I check the execution results of Cloud Assistant commands? {#section_bt2_4bh_vgb .section}

Cloud Assistant commands can be executed only when all required conditions are satisfied, regardless of whether you run commands on the Cloud Assistant client or on an ECS instance. You can use one of the following methods to check the execution results:

-   [ECS console](https://partners-intl.console.aliyun.com/#/ecs)
-   [DescribeInvocationResults](../reseller.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#)
-   Connect to instances to view the log file.
    -   Windows instances: C:\\ProgramData\\aliyun\\assist\\$\{version\}\\log\\aliyun\_assist\_main.log
    -   Linux instances: /usr/local/share/aliyun-assist/$\{version\}/log/aliyun\_assist\_main.log 

        The $\{version\} variable is the version of the Cloud Assistant client on instances, such as 1.0.1.226.


