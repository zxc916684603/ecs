# Create an f1 instance {#concept_tq5_r31_ydb .concept}

This article describes how to create an f1 instance.

## Prerequisites {#section_plv_1j1_ydb .section}

You need an image preinstalled with the development environment of Intel to create an f1 instance. We can share the image with you. This is the only method to get the image. To apply for the image, [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Procedure {#section_m1m_s31_ydb .section}

Follow the steps described in the Procedure section of [Create an ECS instance](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#), but before doing so, consider the following:

-   **Region**: Select  **China East 1 \(Hangzhou\)** \> **China East 1 Zone F**.
-   **Instance Type**: Select  **Heterogeneous Computing** \> **FPGA ** \> **Compute**. And select the appropriate F1 instance type.
-   **Image**: Select **Shared Image**, and then select the shared image.

    **Note:** You need an image preinstalled with the development environment of Intel to create an f1 instance. We can share the image with you. This is the only method to get the image. You can find quartus17.0, vcs2017.3,  dcp sdk in the opt directory.

-   **Network**: Select VPC, and select a **VPC and VSwitch**.

After an f1 instance is created, [connect to the instance](intl.en-US/User Guide/Connect/Overview.md#), and run the following command to check whether the License is configured.

```
echo $LM_LICENSE_FILE #To check whether the variable is set.
```

## Best practices {#section_q1m_s31_ydb .section}

See best practices of f1 instances:

-   [Use OpenCL on an f1 instance](https://www.alibabacloud.com/help/doc-detail/61410.htm)
-   [Using f1 RTL \(Register Transfer Level\)](https://www.alibabacloud.com/help/doc-detail/61412.htm)

