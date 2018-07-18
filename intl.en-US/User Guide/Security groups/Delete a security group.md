# Delete a security group {#concept_s25_pb1_ydb .concept}

You can delete security groups, if you no longer require them. Deleting a security group will delete all its rules.

## Note: {#section_aj1_sb1_ydb .section}

Deleting a security group must meet the following conditions:

-   There are no ECS instances in the security group. About how to move the ECS instance out of the security group, see [Add to or remove from a security group](intl.en-US/User Guide/Instances/Add to or remove from a security group.md#).
-   Ensure it is not referenced in the rules of another security group [Add security group rules](intl.en-US/User Guide/Security groups/Add security group rules.md#). You can delete a security group directly by following the steps described in this document, if the security group is authorized by another security group, you will see the error message shown in the following figure. Delete the corresponding authorization rule.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9723/4661_en-US.png)


## Procedure {#section_pkt_tb1_ydb .section}

To delete a security group, follow these steps:

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region to display a list of all the security groups in the region.
3.  In the left-side navigation pane, click ** Networks & Security** \> ** Security Groups**.
4.  Select one or more security groups. Click **Delete**.
5.  In the displayed Delete a security group dialog box, click **OK**.

## Related API {#section_eyc_yb1_ydb .section}

-   Delete a security group: [DeleteSecurityGroup](../../../../intl.en-US/API Reference/Security groups/DeleteSecurityGroup.md#)
-   To query authorization relationships between a security group and another security group: [DescribeSecurityGroupReferences](../../../../intl.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md#)
-   Move the ECS instance out of the security group: [LeaveSecurityGroup](../../../../intl.en-US/API Reference/Security groups/LeaveSecurityGroup.md#)

