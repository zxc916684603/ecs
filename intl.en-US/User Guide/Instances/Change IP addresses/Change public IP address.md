# Change public IP address {#concept_emj_v2n_xdb .concept}

If your instance is assigned a public IP address, you can change the address within six hours after the instance is created, either in the Classic network or in a VPC network.

## Limits {#section_pv5_w2n_xdb .section}

Following are the limits to change the public IP address of an ECS instance:

-   The instance must be assigned a public IP address, which means you can view the public IP address in the **IP Address** column from the **Instance List** in the ECS console, as displayed in the following figure. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9656/15368068075458_en-US.png)

    **Note:** 

    -   If the public network IP address is not assigned at the time of creation of the instance, after the instance is created successfully, you can assign the public IP address by upgrading or downgrading the network bandwidth configuration. For more information, see [overview of configuration changes](intl.en-US/User Guide/Instances/Change configurations/Overview of configuration changes.md#).
    -   If the public network IP address is not assigned during the creation of a Pay-As-You-Go instance, after the instance is created successfully, public IP address cannot be assigned. You can only [bind an elastic IP \(EIP\) address](https://www.alibabacloud.com/help/doc-detail/27714.htm).
-   The instance must be in the **Stopped** status.

-   The instance has been existing for less than six hours.

    **Note:** After six hours, for a VPC instance, you can [convert public IP address to EIP address](intl.en-US/User Guide/Instances/Change IP addresses/Convert public IP address to EIP address.md#), but you cannot change the public IP address of an instance in the Classic network.

-   You can change the public IP address of an instance three times.


## Prerequisite {#section_tv5_w2n_xdb .section}

Before you change the public IP address of an instance, stop the instance.

## Procedure {#section_uv5_w2n_xdb .section}

To change the public IP address, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find the instance to change the public IP address. In the **Actions** column, select **More** \> **Change Public IP**.

    **Note:** If your instance has been existing for more than six hours, you cannot get the **Change Public IP** option in the **More** drop-down menu.

5.  On the Change Public IP dialog box, click **Start Now**.

    A new public IP address is displayed as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9656/15368068075460_en-US.png)

6.  Click **OK**.

## Related operation {#section_yv5_w2n_xdb .section}

You can [change the private IP of an ECS instance](intl.en-US/User Guide/Instances/Change IP addresses/Change the private IP of an ECS instance.md#).

