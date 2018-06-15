# Bind or unbind a SSH key pair {#concept_zzt_nl1_ydb .concept}

## Limits {#section_f2n_pl1_ydb .section}

-   One ECS instance can only bind one SSH key pair.
-   Except for the non-I/O optimized generation I instance, all the Linux instances in the [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#) support the authentication method of SSH key pair.
-   When your ECS instance is in the Running status, [Restart an instance](intl.en-US/User Guide/Instances/Restart an instance.md#) after you bind a SSH key pair to the instance.
-   If the ECS instance has already bound a SSH key pair, after the new key pair is bound, the new key automatically replaces the original key.
-   If you use password-based authentication for Linux logon, the password authentication feature is automatically disabled after the key pair is bound.
-   After a SSH key pair is unbound, you must [Reset an instance password](intl.en-US/User Guide/Instances/Reset an instance password.md#) for successful connection.

## Bind a SSH key pair {#section_d4l_ql1_ydb .section}

To bind a SSH key pair to an ECS instance, follow these steps.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Networks & Security** \> **Key Pairs**.
4.  Choose a key pair, and then click **Bind Key Pair** in the **Actions** column.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9730/4671_en-US.png)

5.  On the Bind Key Pair dialog box, in the **Select Instance** box, select one or more instances, and then click the icon **\>** to move them to the **Selected** column.

    **Note:** In the **Select Instance** box, the instances with gray names are either Windows instances or non-I/O-optimized instances of Generation I. Those instances do not support SSH key pairs.

6.  Click **OK**.

## Unbind a SSH key pair {#section_lqq_yp1_ydb .section}

To unbind a SSH key pair from an ECS instance, follow these steps.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Networks & Security** \> **Key Pairs**.
4.  Choose a SSH key pair, and then in the **Actions** column, click **Unbind Key Pair**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9730/4672_en-US.png)

5.  On the Unbind Key Pair dialog, in the **Select Instance** box, select one or more instances, and then click the icon **\>** to move them to the **Selected** box.
6.  Click **OK**.

