# Implement access control by using RAM {#concept_stg_4pd_zdb .concept}

This topic describes how to control access to ECS instances at the account level by using Resource Access Management \(RAM\). Specifically, this topic describes how to create a RAM user and how to create policies to grant specific permissions to one or more RAM users and RAM user groups.

## Background information {#section_hlx_szr_lgb .section}

RAM is a resource access control service provided by Alibaba Cloud. For more information, see [What is RAM?](../../../../reseller.en-US/Product Introduction/What is RAM?.md). The following describes how RAM is applied to RAM users and RAM user groups to achieve access control:

-   **RAM users**: If you have purchased one or more ECS instances, and multiple RAM users in your organization \(such as employees, systems, or applications\) need to access the instances, you can create a policy that only grants specific RAM users access to those instances. This application of RAM for access control means you do not need to disclose the AccessKey of your Alibaba Cloud account, which helps maintain account security.
-   **RAM user groups**: You can create multiple user groups and grant different permissions to these user groups so that all RAM users in each user group are applied with the same permissions at the same time. For example:
    -   You can associate a user group with a policy that denies access to the target ECS resources if IP addresses from that user group are not from within your corporate network.
    -   You can add and remove RAM users to and from different user groups when the access control requirements of a RAM user changes. For example, you have two user groups, SysAdmins and Developers, that are applied with specific permissions for system administrators and developers, respectively. If a RAM user who is a developer becomes a system administrator, you can move the target RAM user from the Developers group to the SysAdmins group. Details of the two user groups are as follows:
        -   SysAdmins: This user group requires permissions to create and manage ECS instances. Therefore, you can associate the SysAdmins group with a policy that allows its group members to perform all ECS operations, including the creation and management of ECS instances, images, snapshots, and security groups.
        -   Developers: This user group requires permissions to operate on ECS instances, but not create instances. Therefore, you can associate the Developers group with a policy that allows its group members to call DescribeInstances, StartInstance, StopInstance, RunInstance, and DeleteInstance.

## Authorization policy {#section_vng_gv0_sch .section}

Authorization policies are categorized as either a **System Policy** or **Custom Policy**.

-   **System Policy**: Alibaba Cloud provides a variety of default authorization policies. Some commonly-used system policies for ECS instances are as follows:
    -   AliyunECSReadOnlyAccess: Grants read-only access.
    -   AliyunECSFullAccess: Grants full administrative access.
    -   AliyunECSImageImportDefaultRole: Grants permission to [import a custom image](../../../../reseller.en-US/Images/Custom image/Import images/Import custom images.md#).
    -   AliyunECSImageExportDefaultRole: Grants permission to [export a custom image](../../../../reseller.en-US/Images/Custom image/Export custom images.md#).
    -   AliyunECSNetworkInterfaceManagementAccess: Grants permission to manage [Elastic Network Interfaces \(ENIs\)](../../../../reseller.en-US/Network/Elastic Network Interfaces/ENI overview.md#).
-   **Custom Policy**: A user-generated policy. This policy type is suitable to users who are familiar with various Alibaba Cloud APIs and require fine-grained access control. For more information, see [Step 2](#).

## Step 1: Create a RAM user {#section_93p_xwm_1f5 .section}

1.  Log on to the [RAM console](https://partners-intl.console.aliyun.com/#/ram).
2.  In the left-side navigation pane, click **Users**.
3.  Click **Create User**.

    **Note:** For detailed information about how to create a RAM user, see [RAM users](../../../../reseller.en-US/User Guide/Identity management/User management/RAM users.md#).


## \(Optional\) Step 2: Create a custom policy {#section_vjv_nz8_x3h .section}

1.  In the left-side navigation pane, click **Policies**.
2.  Create **Create Authorization Policy**.
3.  Enter an **Authorization Policy Name** and **Description**.
4.  Enter the parameters for the **Policy Content** according to the JSON template.

    **Note:** For information about the values of the Action and Resource parameters, see [Authentication rules](../../../../reseller.en-US/API Reference/Authentication rules.md#). For information about the values of other parameters, see [Policy elements](../../../../reseller.en-US/User Guide/Permission management/Policy language/Policy elements.md#).

    -   Example policy 1: Allow a RAM user to create Pay-As-You-Go instances.

        ``` {#codeblock_k5g_597_yr2}
        {
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                            "ecs:DescribeImages", 
                          "vpc:DescribeVpcs", 
                          "vpc:DescribeVSwitches", 
                          "ecs:DescribeSecurityGroups", 
                          "ecs:DescribeKeyPairs",
                          "ecs:DescribeTags", 
                          "ecs:RunInstances"
                  ],
                    "Resource": ""
                }
            ],
            "Version": "1"
        }
        ```

    -   Example policy 2: Allow a RAM user to create Subscription instances. Note that bss related APIs are mainly used to view and pay Subscription orders, and the corresponding system policy is `AliyunBSSOrderAccess`.

        ``` {#codeblock_fdz_hyt_tnc}
        {
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                            "ecs:DescribeImages", 
                          "vpc:DescribeVpcs", 
                          "vpc:DescribeVSwitches", 
                          "ecs:DescribeSecurityGroups", 
                          "ecs:DescribeKeyPairs",
                          "ecs:DescribeTags", 
                          "ecs:RunInstances",
                                "bss:DescribeOrderList",
                           "bss:DescribeOrderDetail",
                           "bss:PayOrder",
                          "bss:CancelOrder"
                  ],
                    "Resource": ""
                }
            ],
            "Version": "1"
        }
        ```

    -   Example policy 3: Allow a RAM user to query instance and disk information after creating an ECS instance.

        ``` {#codeblock_k6k_nob_qgz}
        {
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                            "ecs:DescribeInstances", 
                          "ecs:DescribeDisks"
                  ],
                    "Resource": ""
                }
            ],
            "Version": "1"
        }
        ```

5.  Click **Create Authorization Policy**.

## Step 3: Authorize a RAM user {#section_u2f_nxl_87g .section}

1.  In the left-side navigation pane, click **Users**.
2.  Find the RAM user created in step 1 and then, in the **Actions** column, select **Authorize**.
3.  In **Available Authorization Policy Names** area, select one or more system or custom policies.
4.  Click **OK**.

