# Creating a Security Group {#concept_ocl_bvz_xdb .concept}

Each ECS instance must join at least one security group. For more information, see [Security groups](../../../../intl.en-US/Product Introduction/Network and security/Security groups.md#).

If you do not have a security group when your create an ECS instance, you can use the default one provided by the system. For more information, see  [Default security group rules](intl.en-US/User Guide/Security groups/Default security group rules.md#).

Alternatively, you can create a security group to meet your business needs and add your instances to it. This article describes how to create a security group.

## Prerequisite {#section_ctl_3vz_xdb .section}

To create a VPC-Connected security group, you must [Manage a VPC](../../../../intl.en-US/User Guide/Manage a VPC.md#).

**Note:** 

You can create a VPC-Connected security group across VSwitches, but not across VPCs.

## Procedure {#section_nyb_kvz_xdb .section}

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, select **Networks & Security \>** \> **Security group**.
4.  Click **Create Security Group**.
5.  In the Create Security Group dialog box, complete the following configurations:
    -   **Template**: If the instances in the security group are for Web server deployment, select an ideal template to simplify security group rule configuration.

        |Setting|Template|Note|
        |To deploy a Web server on the Linux instances in the security group.|**Web Server Linux**|By default, inbound traffic to port TCP 80, TCP 443, TCP 22, and for ICMP is allowed.|
        |To deploy a Web server on the Windows instances in the security group.|**Web Server Windows**|By default, inbound traffic to port TCP 80, TCP 443, TCP 3389, and for ICMP is allowed.|
        |Not for Web server|**Custom**|After the security group is created, add a security group rule to meet your business needs. [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#)|

    -   **Security Group Name**: Specify a valid security group name.
    -   **Description**: Give a brief to the security group for future management.
    -   **Network Type**:
        -   To create a VPC-Connected security group, select **VPC** and then a specific VPC.
        -   To create a classic network-connected security group, select **Classic**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9717/4657_en-US.png)

6.  Click **OK** to save the rule.

For a new security group without any rules, the following default rules apply to the communication of all the instances in the group over Internet or intranet. Outbound: Allow all for outbound traffic. Inbound: Drop all for inbound traffic.

## Follow-up operations {#section_agj_cwz_xdb .section}

After you create a security, [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#).

To meet your business needs, [Add to or remove from a security group](intl.en-US/User Guide/Instances/Add to or remove from a security group.md#).

## Related APIs {#section_gqg_dwz_xdb .section}

[CreateSecurityGroup](../../../../intl.en-US/API Reference/Security groups/CreateSecurityGroup.md#)

