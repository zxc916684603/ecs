# Change configurations of Pay-As-You-Go instances {#concept_fzw_gbf_5db .concept}

If you find that instance configurations exceed or are insufficient for your application requirements, you can change the instance type, that is, to change memory and CPU configurations. This document describes how to change configurations of Pay-As-You-Go instances. For more information about how to change configurations of \(Subscription\) instances, see [overview of configuration changes](intl.en-US/User Guide/Instances/Change configurations/Overview of configuration changes.md#).

**Note:** Changing instance configurations requires stopping your instance, which interrupts your services. Therefore, we recommend that you change instance configurations during off-peak hours.

## Limits {#section_hxl_fc2_xdb .section}

This feature has the following limits:

-   The interval between two changes should be no less than 5 minutes.

-   Not supported within or between such instance type families: d1, d1ne, i1, i2, ga1, gn5, f1, f2, f3, ebmc4, ebmg5, sccg5, and scch5. For the instance type families that support this feature and the rules for changing instance types, see [instance type families that support upgrading instance types](intl.en-US/User Guide/Instances/Change configurations/Instance type families that support upgrading instance types.md#).


## Prerequisite {#section_jyl_fc2_xdb .section}

The instance has been stopped.

## Procedure {#section_kyl_fc2_xdb .section}

Follow these steps to change memory and vCPU configurations of the instance:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  In the **Actions** column, click **Change Instance Type**.
5.  On the Instance Type page, select the desired instance type and click **Confirm**.

    **Note:** You can enter the instance type information in the search box to filter instance types in real time.


Once the change is complete, it takes effect immediately. You can view the instance type information in the **Basic Information** area of the Instance Details page, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9644/15367408265424_en-US.png)

Then, restart the instance to restore your services.

You can also use the [DescribeResourcesModification](../../../../intl.en-US/API Reference/Others/DescribeResourcesModification.md#) API to query the instance types that can be changed.

