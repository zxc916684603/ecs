# Reset an instance password {#concept_qct_gfl_xdb .concept}

If you did not specify a logon password for an instance at the time of creation, or the password is lost, specify a new password in the ECS console. This article describes how to use the Reset Password feature to specify a new logon password.

**Note:** You must restart an instance after its password is reset, which may impact the service. To reduce the impact, we recommend that you reset the password when the related service is not busy.

## Prerequisites {#section_mg1_3fl_xdb .section}

The instance must be in a stable status, such as **Stopped** and **Running**. For more information, see [ECS instance life cycle](../intl.en-US/Product Introduction/Instance/ECS instance life cycle.md#).

## Procedure {#section_ng1_3fl_xdb .section}

To reset a password for one or multiple ECS instances, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  According to the number of instances to be operated, do the following:
    -   To reset the password for one instance, find the instance, and in the **Actions** column, select **More** \> **Reset Password**.

        ![](images/5441_en-US.png)

    -   To reset the passwords for multiple instances, select the instances, and under the instance list, click **Reset Password**.

        ![](images/5442_en-US.png)

5.  In the Reset Password dialog box, specify a new valid password, and click **Submit**.

    ![](images/5443_en-US.png)

6.  Operate different actions to make the password effective according to the instance status:
    -   **Running**: [Restart an instance](intl.en-US/User Guide/Instances/Restart an instance.md#)  in the console.

        ![](images/5444_en-US.png)

    -   **Stopped**: Start the instance in the console.

        ![](images/5445_en-US.png)


