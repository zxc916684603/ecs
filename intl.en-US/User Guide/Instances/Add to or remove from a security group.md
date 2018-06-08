# Add to or remove from a security group {#concept_jhw_31n_xdb .concept}

## Add an instance to a security group {#section_g4z_32n_xdb .section}

You can add an instance to a security group using the ECS Management console. One ECS instance can be added to up to five security groups.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  Click **Instances** in the left-side navigation pane.
3.  Select your desired region.
4.  Select the desired instance. Click the instance name or corresponding **Manage** button.
5.  Click **Security Groups** in the left-side navigation pane.
6.  Click **Add Security Group**.  In the displayed dialog box, select the appropriate security group.
7.  Click **OK**.

After you add an instance to the security group, the rules apply to the instance automatically. 

## Remove an instance from a security group {#section_j4z_32n_xdb .section}

You can remove instances from security groups.

**Note:** 

-   Note that an instance must be in at least two security group for this action to be performed
-   , and you have done enough test before this operation to avoid any intranet communication error between instances.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  Click **Instances** in the left-side navigation pane.
3.  Select your desired region.
4.  Select the desired instance. Click the instance name or corresponding **Manage** button.
5.  Click **Security Groups** in the left-side navigation pane. You can view the security group list that this instance belongs to. 
6.  Select the security group to remove from and click **Remove**.
7.  Click **OK**.

For use cases of security groups, see [Scenarios](intl.en-US/User Guide/Security groups/Scenarios.md#).

