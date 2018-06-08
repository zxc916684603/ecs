# Check instance information {#concept_ump_jcd_xdb .concept}

Through the console, you can check all the ECS instances you own. You can check the:

-   On the [View all ECS instances under your account on the Overview page](#overview) page, all ESC instances in all regions and their status under your account can be viewed.
-   View all the ECS instances in a specified region on the Instance List page For details, see[View the information of ECS instances on the Instance List page](#list).
-   Detailed information of any ECS instance on its  Instance Details page. For details, see[View details of an ECS instance on Instance Details page](#detail).

## View all ECS instances under your account on the Overview page {#overview .section}

You can view information of all the ECS instances created by your account on the ECS Overview page, including:

-   Total number of ECS instance, and numbers of instances under each status.
-   Number of resources in different regions and numbers of ECS instances under each status.

The homepage of the ECS console is theOverview  page by default.

## View the information of ECS instances on the Instance List page {#list .section}

To navigate to the Instance List page, follow these steps:

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  On the left-side navigation pane, click **Instances**.
3.  Select a region.

You can see information of all the existing ECS instances in the selected region, including ECS instance ID/name, zone, IP addresses, status, network type, billing method, and actions. You can show or hide the displayed information of an instance  by using the Set Display Items feature.

1.  In the upper-right corner of the Instance List, click the ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/25441/cn_zh/1514174627852/icon_CustomizeItem.png)icon.
2.  In the dialog box of Set Display Items , select the instance information to be displayed and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9639/5368_en-US.png)


## View details of an ECS instance on Instance Details page {#detail .section}

You can navigate to the Instance Details page to view detailed information of an ECS instance.

To navigate to theInstance Detailspage, follow these steps:

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.11.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find the ECS instance you want to view the details of, and then click its instance ID.

On theInstance Details page, you can view the following information:

-   Basic Information, including ECS instance ID, instance name, region, zone, instance type, instance type family, image ID, key pair name \(applies to Linux instances only\), instance RAM role, and tags.
-   Configuration Information, including CPU, memory, I/O optimization, operating system, IP addresses, billing method for bandwidth, current bandwidth, and VPC network information \(applies to VPC instances only\).
-   Payment Information, including billing method, the mode to stop an instance, creation time, and automatic release schedule \(applies to Pay-As-You-Go instances only\).
-   Monitoring Information, including CPU and network usage.

You can also switch from the Instance Detailspage to the Instance Disks, the Shared Block Storage, theInstance Snapshots, the Security Groups, or the page to view resources related to this instance.

