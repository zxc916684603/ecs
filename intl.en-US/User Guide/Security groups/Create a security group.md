# Create a security group {#concept_ocl_bvz_xdb .concept}

Each ECS instance must join at least one security group. For more information, see [security group](../../../../reseller.en-US/Product Introduction/Network and security/Security group.md#).

If you do not have not created a security group prior to creating an ECS instance, we recommend that you use the default security group provided by the system. For more information, see [default security group rules](reseller.en-US/User Guide/Security groups/Default security group rules.md#).

Alternatively, you can create a security group to meet your business needs and then add your instances to it. This topic describes how to create a security group.

## Prerequisite {#section_ctl_3vz_xdb .section}

To create a VPC-connected security group, you must [manage a VPC](../../../../reseller.en-US/User Guide/Manage a VPC.md#).

**Note:** 

You can create a VPC-connected security group across VSwitches, but not across VPCs.

## Procedure {#section_nyb_kvz_xdb .section}

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select **Networks and Security** \> **Security Groups**.
3.  Select the target region.
4.  Click **Create Security Group**.
5.  In the Create Security Group dialog box, complete the following configurations:
    -   **Template**: If the instances in the security group are for Web server deployment, select an appropriate template to simplify security group rule configuration.

        |Setting|Template|Note|
        |To deploy a Web server on the Linux instances in the security group|**Web Server Linux**|By default, inbound traffic to TCP 80, TCP 443, TCP 22, and ICMP is allowed.|
        |To deploy a Web server on the Windows instances in the security group|**Web Server Windows**|By default, inbound traffic to port TCP 80, TCP 443, TCP 3389, and ICMP is allowed.|
        |Not for Web server|**Custom**|After the security group is created, [add security group rules](reseller.en-US/User Guide/Security groups/Add security group rules.md#) to meet your business needs.|

    -   **Security Group Name**: Specify a name for the security group.
    -   **Description**: Enter description of the security group for easier management.
    -   **Network Type**:
        -   To create a VPC-Connected security group, select **VPC** and then select the target VPC.
        -   To create a Classic network-connected security group, select **Classic**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9717/15433120874657_en-US.png)

6.  Click **OK**.

For a new security group without any rules, the following default rules apply to the communication of all the instances in the group over the Internet or intranet:

-   Outbound: Allow
-   Inbound: Forbid

## Follow-up operations {#section_agj_cwz_xdb .section}

After you create a security, you can [add security group rules](reseller.en-US/User Guide/Security groups/Add security group rules.md#).

You can also[add/remove an instance to/from a security group](reseller.en-US/User Guide/Instances/Add to or remove from a security group.md#).

## Related API {#section_gqg_dwz_xdb .section}

[CreateSecurityGroup](../../../../reseller.en-US/API Reference/Security groups/CreateSecurityGroup.md#)

