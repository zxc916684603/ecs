# Create an f3 instance {#concept_myr_2m1_ydb .concept}

This article describes how to create an f3 instance.

**Note:** Due to limited computing resources, we recommend that you use instances with four cores or more for testing, for example, instance type family g5-ecs.g5.2xlarge \(8 vCPU core, 32 GiB\). Create an f3 instance when you need to download the image to the FPGA chipset.

## Prerequisite {#section_bsy_fm1_ydb .section}

The f3 instance type family is currently available for testing by invited users. [Open a ticket](https://workorder-intl.console.aliyun.com/console.htm#/ticket/createIndex) to request a free f3 instance test.

## Procedure {#section_csy_fm1_ydb .section}

For more information about how to create an f3 instance, see [create an ECS instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#). When you create an f3 instance, follow these guidelines:

-   **Billing Method**: Select **Pay-As-You-Go** or **Subscription**.

    **Note:** 

    -   During the testing phase, f3 instances are available for free. Other ECS resources including cloud disks, public network bandwidth, and snapshots will incur usage fees.
    -   f3 instances are not available as preemptible instances.
-   **Region**: Select **China East 2 \(Shanghai\)**.
-   **Instance Type**: Select **Heterogeneous Computing** \> **FPGA Compute**, and then select your required instance type.
-   **Image**: Click **Shared Image**, and then select the specified image.

    **Note:** We have provided a Xilinx image for development use. At present, the image can only be retrieved through image sharing.

-   **System Disk**: We recommend that you allocate a 200 GiB Ultra Cloud Disk for the system image.
-   **Network**: Select **VPC**.

## Best practices {#section_hsy_fm1_ydb .section}

For the best practices of f3 instances, see [use RTL compiler on an f3 instance](https://www.alibabacloud.com/help/doc-detail/71547.htm).

