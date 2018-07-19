# Restore security group rules {#concept_ec2_bg1_ydb .concept}

Restoring security group rules refers to the process of completely or partially restoring the rules in the original security group to those of a target security group. Specifically:

-   **Completely restoring** refers to moving the rules that do not exist in the target security group from the original security group and adding the rules that only exist in the target security group to the original security group.  After restoration, rules in the original security group are identical with those in the target security group.
-   **Partially restoring** refers to adding the rules that only exist in the target security group to the original security group and ignoring the rules that only exist in the original group.

## Limits {#section_en2_ng1_ydb .section}

Restoring security group rules has the following limits:

-   The original security group and the target security group must be in the same region.
-   The original security group and the target security group must be of the same network type.
-   If any system-level security group rules,  of which the priority is 110, exist in the target security group, they are not created during restoration. After restoration, the rules in the original security group may be different from what is expected.  If you need the system-level security group rules, you have to manually create the rules and set their priority to 100.

## Use cases {#section_egc_4g1_ydb .section}

If you want to apply new security group rules to an ECS instance that is running an online business application, you can clone the former security group as a backup, and then modify the rules inside.  If the new security group rules impair the online business application, you can restore the rules fully or partially.

## Prerequisites {#section_nqx_4g1_ydb .section}

You must own at least one security group of the same network type in the same region.

## Procedure {#section_lzx_wg1_ydb .section}

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region in the security group .
3.  In the left-side navigation pane, choose **Network & Security \> Security Groups**.
4.  Find the security group you want to restore rules for as the original security group, and in the **Action** column, click  **Restore rules.**.
5.  In the  Restore rules dialog box, follow these steps:
    1.  Select the **Target security group**:  Select a security group as the target security group that must have different rules from the original security group.
    2.  Select a **Restore type**:
        -   If you want the original security group to have the same rules as the target security group, select **Completely restored**.
        -   If you only want to add the rules that only exist in the target security group to the original security group,  select **Partially restored**.
    3.  In the Result preview area, preview the restoration result:
        -   Rules highlighted in green only exist in the target security group.  No matter whether you choose  **Completely restored** or **Partially restored**, these rules are added to the original security group.
        -   Rules highlighted in red are the rules that do not exist in the target security group.  If  **Completely restored** is selected, the system removes these rules from the original security group.  If  **Partially restored** is selected, the rules are retained in the original security group.
    4.  Click **OK**.

The Restore rules dialog box is closed automatically after successful creation. In the **Security Group List**  find the original security group you restored the rules for. In the **Action** column, click **Configure Rules** to enter the Security Group Rules page, and view the updated security group rules.

