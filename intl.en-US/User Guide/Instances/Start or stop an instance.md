# Start or stop an instance {#concept_mnp_lsl_xdb .concept}

This article describes how to start or stop an ECS instance.

## Start an instance {#section_bdq_nsl_xdb .section}

You can start an instance in the ECS console. When an instance starts successfully, it is in a **Running** status.

**Prerequisite**

The instance must be in a **Stopped** status.

**Procedure**

To start an instance, follow these steps:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to be started, and in the **Actions** column, select **More** \> **Start**. If you want to start multiple **Stopped** instances, select them, and under the instance list, click **Start**.
5.  In the Start Instance dialog box, read the note and click **OK**.

The instance is in a **Running** status after it is started.

## Stop an instance {#section_fdq_nsl_xdb .section}

To stop an instance is to shut it down. You can stop an ECS instance in the ECS console. When an instance stops successfully, it is in a **Stopped** status.

**Note:** Stopping an instance interrupts your business operations. Proceed with caution.

If you stop a \(Subscription\) instance part of the way through its billing period, the bill for that period will not be affected. If the auto-renewal service is activated, you will continue to be billed for the stopped instance at the start of each new billing period.

For a Pay-As-You-Go instance, its network type and the No Fees for Stopped Instances \(VPC-Connected\) feature determine billing:

-   VPC: If the **No Fees for Stopped Instances \(VPC-Connected\)** feature is enabled, you can decide whether to keep being billed for the instance or not. However, you will continue to be billed for other ECS-related resources. For more information, see [No fees for stopped instances \(VPC-Connected\)](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#). If this feature is not enabled, billing continues after the instance is stopped.
-   Classic network: A stopped instance still incurs fees. Billing will stop only after you [Release an instance](intl.en-US/User Guide/Instances/Release an instance.md#).

**Prerequisites**

The instance is in the **Running** status.

**Procedure**

To stop an instance, follow these steps:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to be stopped, and in the **Actions** column, select  **More** \> **Stop**. If you want to stop multiple **Running** instances, select them, and under the instance list, click **Stop**.
5.  According to the billing method and network type of the instance, apply suitable actions:
    -   Subscription instance or classic network pay per volume instance: In the Stop Instance dialog box, select **Stop or Force Stop**, and then click **OK**.
    -   A VPC-Connected Subscription instance:

        -   If the **No Fees for Stopped Instances \(VPC-Connected\)** feature is enabled, read the notice, and read the Notice, in the Stop Instance dialog box, select **Stop Method** \(Stop or Force Stop\), and select **Stop Mode** \(whether to keep the instance after stopping and continue charging\), and then click **OK**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9648/15347531535448_en-US.png)

        -   If the **No Fees for Stopped Instances \(VPC-Connected\)** feature is disabled, in the Stop Instance dialog box, select **Stop Method** \(Stop or Force Stop\).

            **Note:** To disable the **No Fees for Stopped Instances \(VPC-Connected\)** feature, see [Disable the feature](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#disable).


Once the instance is successfully stopped, the instance enters a **Stopped** status. For a VPC-Connected Pay-As-You-Go instance, if you choose not to keep the instance, **Stop Instance, No Fees** is shown in the **Stop Mode** column of the instance list. Otherwise, **Keep Instance, Fees Apply** is shown. For other ECS instances, the **Stop Mode** column shows no information.

## Related APIs {#section_pdq_nsl_xdb .section}

Start instance: [StartInstance](../../../../intl.en-US/API Reference/Instances/StartInstance.md#)

Stop instance: [StopInstance](../../../../intl.en-US/API Reference/Instances/StopInstance.md#)

