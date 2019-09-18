# Modify security group rules {#concept_d2r_dsz_ggb .concept}

Improper settings of security group rules may impose serious security risks. You can modify improper rules in a security group.

## Prerequisites {#section_usp_g9k_soz .section}

You have [created a security group](reseller.en-US/Security/Security groups/Create a security group.md#), and [added security group rules](reseller.en-US/Security/Security groups/Add security group rules.md#) in that security group.

## Context {#section_ypy_3sz_ggb .section}

If security group rules do not restrict access to certain ports, it will cause serious security risks. You can review your current security group rules and modify any improperly set rules to ensure the security of your ECS instances.

## Procedure {#section_swc_rsz_ggb .section}

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Network & Security** \> **Security Groups**.
3.  In the top navigation bar, select a region.
4.  On the Security Groups page, find the target security group, and then click **Add Rules** in the **Actions** column.

    ![Modify security group rules - configure rules](images/35540_en-US.png)

5.  Click the traffic direction to which a security group rule applies.
    -   If you need to modify security group rules for a VPC, select **Inbound** or **Outbound**.
    -   If you need to modify security group rules for the classic network, select **Internal Network Inbound**, **Internal Network Outbound**, **Internet Inbound** or **Internet Outbound**.
6.  Find the target security group rule, and click **Modify** in the **Actions** column. For how to configure security group rules, see [Add security group rules](reseller.en-US/Security/Security groups/Add security group rules.md#ul_vpc_qwz_xdb). For use cases of security group rules, see [Typical applications of security group rules](reseller.en-US//Typical applications of security group rules.md#).

    ![Modify security group rules](images/35541_en-US.png)


## API operations {#section_f2p_dwz_ggb .section}

You can call [ModifySecurityGroupRule](../../../../reseller.en-US/API Reference/Security groups/ModifySecurityGroupRule.md#) to modify an inbound rule.

## What to do next {#section_t2q_c5z_ggb .section}

-   To view specific inbound and outbound rules, you can [query security group rules](reseller.en-US//Manage security group rules.md#).
-   To back up security group rules, you can [export security group rules](reseller.en-US//Export security group rules.md#).
-   To create or restore security group rules quickly, you can [import security group rules](reseller.en-US//Import security group rules.md#).
-   If you no longer need a security group rule, you can [delete security group rules](reseller.en-US//Delete a security group rule.md#).

