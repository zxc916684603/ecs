# Step 3. Connect to an instance {#concept_irq_dwd_wdb .concept}

The  **Management Terminal**  allows you to connect to your ECS instance by using a web browser, even though you do not purchase bandwidth for Internet access.

## Procedure {#section_grq_2wd_wdb .section}

The following figure illustrates how to use the **Management Terminal**  to connect to an ECS instance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9602/5082_en-US.png)

## Follow these steps: {#section_orq_gwd_wdb .section}

1.  Log on to the  [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click**Instances** .
3.  Select your region.
4.  In the instance list, find your instance, and in the  **Actions**  column, click **Connect**.
5.  On the  VNC Connection Password dialog box, copy the password, and click **Close**.

    **Note:** The connection password is displayed only once during the first connection to the Management Terminal. If you need to use this password to connect to the Management Terminal in the future, please note the password.

6.  On the  Enter VNC Password  dialog box, paste the VNC connection password that you have copied, and click  **OK**.
7.  To log on to the ECS instance, follow the steps  according to the operating system:
    -   For a Linux instance: Enter the user name  **root** and the logon password. If you lose your logon password of your instance, reset the password [Reset an instance password](../../../../intl.en-US/User Guide/Instances/Reset an instance password.md#).

        **Note:** 

        -   The logon password input is invisible.
        -   In the upper left corner of the Management Terminal page,  **select Send Remote Command \> ** \> **CTRL+ALT+DELETE**\(X is 1 ~ 10\), switch to a different **Management Terminal** and connect to a Linux instance to perform different actions.
        -   If a black screen is displayed, the Linux instance may be in sleep mode. To exit sleep mode, click the mouse or press any key.
    -   For a Windows instance: In the upper left corner of the Management Terminal page,  **select Send Remote Command \> ** \> **CTRL+ALT+DELETE, **to enter the logon interface for a Windows instance. Enter the user name \(Administrator\) and the logon password. If you lose your logon password of your instance, [Reset an instance password](../../../../intl.en-US/User Guide/Instances/Reset an instance password.md#).

        ![](images/5085_en-US.png)


For more information about the Management Terminal, see [Terminal](../../../../intl.en-US/User Guide/Connect/Terminal.md#).

## Other connections {#section_rs5_3wd_wdb .section}

You can connect to the ECS instance in other ways. For specific actions, see the following documents:

-   [Connect to a Linux instance by using an SSH key pair](../../../../intl.en-US/User Guide/Connect/Connect to a Linux instance by using an SSH key pair.md#)
-   [Connect to a Linux instance by using a password](../../../../intl.en-US/User Guide/Connect/Connect to a Linux instance by using a password.md#)
-   [Connect to a Windows instance](../../../../intl.en-US/User Guide/Connect/Connect to a Windows instance.md#)
-   [Connect to an instance on a mobile device](../../../../intl.en-US/User Guide/Connect/Connect to an instance on a mobile device.md#)

