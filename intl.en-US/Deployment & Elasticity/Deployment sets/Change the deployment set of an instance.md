# Change the deployment set of an instance {#concept_q2x_yn4_4gb .concept}

This topic describes how to change the deployment set of an instance by using the ECS console.

## Prerequisites {#section_mnx_ccb_wgb .section}

A deployment set is created for your instance. For more information, see [Create a deployment set](../reseller.en-US/Deployment & Elasticity/Deployment sets/Create deployment sets.md#).

## Procedure {#section_qs1_bcb_wgb .section}

1.  Find the target instance. The instance must be in the **Stopped** or **Running** state.
2.  In the **Actions** column, choose **More** \> **Instance Settings** \> **Change Deployment Set**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21509/156758158812236_en-US.png)

3.  In the Change Deployment Set dialog box, select the destination deployment set and specify the **Force Change** option:

    -   **Yes**: You can change the host of an instance and restart an instance that is in the **Running** or **Stopped** state.
    -   **No**: You cannot change the host of an instance. The deployment set must be added on the current host. This may cause the deployment set modification to fail.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21509/156758158812237_en-US.png)

4.  Click **OK**.

You can also call the [ModifyInstanceDeployment](../reseller.en-US/API Reference/Deployment sets/ModifyInstanceDeployment.md#) API action to modify the name and description of a deployment set.

