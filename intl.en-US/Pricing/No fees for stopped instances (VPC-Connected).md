# No fees for stopped instances \(VPC-Connected\) {#concept_js1_1fd_5db .concept}

## Overview {#section_kvc_4qk_zdb .section}

The ECS introduces the **No fees for stopped instances \(VPC-Connected\)** feature. If you enable this feature, you do not have to pay for a VPC-Connected Pay-As-You-Go instance when it enters the **Stopped** \(`Stopped`\) status after you stop it in the [ECS console](../../../../intl.en-US/User Guide/Instances/Start or stop an instance.md#) or when you use the [StopInstance](../../../../intl.en-US/API Reference/Instances/StopInstance.md#) interface or [Alibaba Cloud CLI](https://www.alibabacloud.com/help/product/29991.htm).

## Applicable resources {#section_lvc_4qk_zdb .section}

The **No fees for stopped instances \(VPC-Connected\)** feature is **only applicable to** VPC-Connected Pay-As-You-Go instances.  

This **No fees for stopped instances \(VPC-Connected\)** feature is **not applicable to** the following ECS resources:

-   All instances with local disks, including but not limited to d1ne, d1, i2, i1, gn5, and ga1 instances.

-   Cloud disks attached to the instances \(including system disks and data disks\), Internet bandwidth, elastic IP \(EIP\) addresses, and images. After the **No fees for stopped instances \(VPC-Connected\)** feature is enabled, billing of these resources continues when the instance is **stopped**. For more information about billing, see [Pay-As-You-Go](intl.en-US/Pricing/Pay-As-You-Go.md#), [Cloud disk pricing](https://www.alibabacloud.com/product/ecs), [Billing of network bandwidth](intl.en-US/Pricing/Billing of network bandwidth.md#), [Bandwidth pricing](https://www.alibabacloud.com/product/ecs), and [EIP pricing](https://www.alibabacloud.com/help/doc-detail/27767.htm).

-   New VPC-Connected Pay-As-You-Go instances that are in the **Stopped** \(`Stopped`\) status after they are created, either by using the [ECS console](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#) or the [CreateInstance](../../../../intl.en-US/API Reference/Instances/CreateInstance.md#) interface, and before entering the **Running** \(`Running`\) status.

-   Instances that are stopped because of overdue payment. In this case, the billing also stops. The computing resources and public IP address will be released too. You can [reactivate your instance](../../../../intl.en-US/User Guide/Instances/Reactivate an instance.md#) and its related resources only after the overdue payment is cleared. Billing of all resources resumes after your instance is successfully reactivated.

-   Pay-As-You-Go instances in classic networks. After such an instance enters the **Stopped** status, Alibaba Cloud still bills the instance and its related resources. The public and private IP addresses of the instance remain unchanged after the instance is started.


## Influences of the feature {#section_qvc_4qk_zdb .section}

The **No fees for stopped instances \(VPC-Connected\)** feature has the following influences on your instance when the feature is enabled and the instance is stopped:

-   The CPU and RAM will be released, so you may fail to start your instance next time. If it happens, try again or start your instance after some time.

-   If the instance has been assigned a public IP address, the address is released. After you start your instance in the [ECS console](../../../../intl.en-US/User Guide/Instances/Start or stop an instance.md#) or by using the [StartInstance](../../../../intl.en-US/API Reference/Instances/StartInstance.md#) interface, your instance is assigned a new public IP address. However, its private IP address remains unchanged.

    **Note:** If you do not want to change the public IP address, you can stop the instance after [converting the public IP address to an EIP address](../../../../intl.en-US/User Guide/Instances/Change IP addresses/Convert public IP address to EIP address.md#).

-   When a t5 instance is stopped, the existing CPU credits are valid but credit accumulation stops. When it starts, CPU credits continue to accumulate. For more information, see [Burstable instances](../../../../intl.en-US/Product Introduction/Instance/Burstable instances.md#).


When you [replace the system disk](../../../../intl.en-US/User Guide/Cloud disks/Change a system disk (public image).md#) \([ReplaceSystemDisk](../../../../intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)\), [roll back a disk](../../../../intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) \([ResetDisk](../../../../intl.en-US/API Reference/Disk/ResetDisk.md#)\), [reinitialize a disk](../../../../intl.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#) \([ReInitDisk](../../../../intl.en-US/API Reference/Disk/ReInitDisk.md#)\), or perform other O&M operations, you must stop your instance and start it when you have performed these actions. Along with the preceding actions, perform any one of the following actions to make sure that your instance starts successfully:

-   Log on to the [ECS console](https://ecs.console.aliyun.com/#/home) to disable the **No fees for stopped instances \(VPC-Connected\)** feature. For more information about the procedure, see [Disable the feature](#disable).

-   If you are using APIs or Alibaba Cloud CLI, set `StoppedMode = KeepCharging` in the [StopInstance](../../../../intl.en-US/API Reference/Instances/StopInstance.md#) interface.


## Enable the feature {#default .section}

You must manually enable the **No fees for stopped instances \(VPC-Connected\)** feature to use the **No fees for stopped instances \(VPC-Connected\)** feature.

Once the **No fees for stopped instances \(VPC-Connected\)** feature is enabled, it applies to the **VPC-Connected Pay-As-You-Go** instances in all the regions under your account. When the feature is enabled, you can choose  **Keep Instance with Fees** or not when you stop a VPC-Connected Pay-As-You-Go instance.

**Note:** If you already have one or more VPC-Connected Pay-As-You-Go instances in use, the **No fees for stopped instances \(VPC-Connected\)** feature is not automatically enabled for the ECS instances under your account so that your systems and applications are not affected accidentally.  After you fully understand and confirm that the feature does not result in uncontrollable impact on your systems or applications, you can log on to the ECS console to enable the feature.

To enable the **No fees for stopped instances \(VPC-Connected\)** feature, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Overview**.
3.  In the upper-right corner of the **Overview** page, click **Settings**.
4.  Toggle **Enable "No Fees for Stopped Instances" for VPC-Connected Instances in All Regions**, read the note in the dialog box, and then click **No Fees for stopped instances \(VPC-Connected\)**.
5.  Click **OK**.

After the **No fees for stopped instances \(VPC-Connected\)** feature is enabled, you can disable it as needed. For more information, see [Disable the feature](#disable).

## Disable the feature {#disable .section}

You can disable the **No fees for stopped instances \(VPC-Connected\)** feature as needed.

**Note:** This operation takes effect for the VPC-Connected Pay-As-You-Go instances in all the regions under your account. Proceed with caution.

After the **No fees for stopped instances \(VPC-Connected\)** feature is disabled:

-   The VPC-Connected Pay-As-You-Go instances in all the regions under your account are still billed even after they are stopped.

-   If the **Stop Instance** mode is **No fees for stopped instances \(VPC-Connected\)**, an instance currently in the **Stopped** \(`Stopped`\) status is not billed. After it is started,

    -   A new public IP address is assigned if it had one before it was stopped.
    -   The EIP address remains unchanged if it is not unbound before the instance was stopped.
-   When your instance enters the **Stopped** \(`Stopped`\) status after the feature is disabled,

    -   The instance is still billed.
    -   If it has been assigned a public IP address, the address is retained and remains unchanged.

To disable the **No Fees for Stopped Instances \(VPC-Connected\)** feature, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Overview**.
3.  In the upper-right corner of the **Overview** page, click **Settings**.
4.  Disable **Enable "No Fees for Stopped Instances" for VPC-Connected Instances in All Regions**, read the note in the dialog box, and then click **I Agree**.
5.  Click **OK**.

