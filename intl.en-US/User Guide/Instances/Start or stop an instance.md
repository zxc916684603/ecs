# Start or stop an instance {#concept_mnp_lsl_xdb .concept}

This article describes how to start or stop an ECS instance.

## Start an instance {#section_bdq_nsl_xdb .section}

You can start an instance in the ECS console. When an instance starts successfully, it is in the **Running** status.

**Prerequisite**

The instance must be in the **Stopped** status.

**Procedure**

Do the following to start an instance:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to be started, and in the **Actions** column, select **More** \> **Start**. If you want to start multiple **Stopped** instances, select them, and under the instance list, click **Start**.
5.  In the Start Instance dialog box, read the note and click **OK**.

The instance is in the **Running** status after start.

## Stop an instance {#section_fdq_nsl_xdb .section}

To stop an instance is to shut it down. You can stop an ECS instance in the ECS console. When an instance stops successfully, it is in the **Stopped** status.

**Note:** Stopping an instance interrupts your business operations. Proceed with caution.

For a \(Subscription\) instance, stopping an instance does not affect its billing. However, for a Pay-As-You-Go instance, its network type and the No Fees for Stopped Instances \(VPC-Connected\) feature determine billing:

-   VPC: If the **No Fees for Stopped Instances \(VPC-Connected\)** is enabled, you can decide to keep your instance being billed or not. However, billing for other ECS-related resources is retained. Other resource are not affected. For more information, see [No fees for stopped instances \(VPC-Connected\)](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#). If this feature is not enabled, billing continues after the instance is stopped.
-   Classic network: A stopped instance still incurs fees.  Only after [Release an instance](intl.en-US/User Guide/Instances/Release an instance.md#) , the billing will stop.

**Prerequisites**

The instance is in the **Running** status.

**Procedure**

Do the following to stop an instance:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to be stopped, and in the **Actions** column, select  **More** \> **Stop**. If you want to stop multiple **Running** instances, select them, and under the instance list, click **Stop**.
5.  According to the billing method and network type of the instance, apply suitable actions:
    -   Subscription instance or classic network pay per volume instance: In the Stop Instance dialog box, select **Stop or Force Stop**, and then click **OK**.
    -   A VPC-Connected Subscription instance,

        -   If the **No Fees for Stopped Instances \(VPC-Connected\)** feature is enabled, read the notice, and read the Notice, in the Stop Instance dialog box, select **Stop Method** \(Stop or Force Stop\), and select **Stop Mode** \(whether to keep the instance after stopping and continue charging\), and then click **OK**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9648/5448_en-US.png)

        -   If the **No Fees for Stopped Instances \(VPC-Connected\)** feature is disabled, in the Stop Instance dialog box, select **Stop Method** \(Stop or Force Stop\).

            **Note:** To disable the **No Fees for Stopped Instances \(VPC-Connected\)** feature, see [Disable the feature](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#disable).


Once the instance is successfully stopped, the instance enters the  **Stopped** status. For a VPC-Connected Pay-As-You-Go instance, if you choose not to keep the instance, in the **Stop Mode** column of the instance list, **Stop Instance, No Fees**. Otherwise, **Keep Instance, Fees Apply** is shown. For other ECS instances, the **Stop Mode** does not display information.

## Related APIs {#section_pdq_nsl_xdb .section}

Start instance: [StartInstance](../../../../intl.en-US/API Reference/Instances/StartInstance.md#)

Stop instance: [StopInstance](../../../../intl.en-US/API Reference/Instances/StopInstance.md#)

