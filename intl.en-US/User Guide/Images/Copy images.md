# Copy images {#concept_a3m_5dm_xdb .concept}

Copying images allows you to deploy an application across regions by running the same image environment. You can copy a custom image from one region to another. The task completion time depends on the network transfer speed and the number of concurrent tasks in the queue.

## Attention {#section_wgf_n2m_xdb .section}

-   Upon copying a custom image, a corresponding snapshot is created in the target region, and then the image is created from that snapshot in the target region. As a result, fees are incurred due to data transfer between different regions. Currently, no fee is charged for such traffic, and when it will be charged is subject to the official notice.
-   After copying a custom image, an identical image is created in the target region. However, the relevant role and service authorization information is lost, which is also true for previously configured [user data](intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#).

## Procedure {#section_sv3_x2m_xdb .section}

To copy images in the ECS console, perform the following steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).
2.  Select a region.
3.  In the left-side navigation pane, select **Snapshots and Images** \> **Images**.
4.  Select the custom image you want to copy. Note that **Type** must be **Custom Images**. In the **Actions** column, click **Copy Image**.

    **Note:** If your custom image is larger than 200 GiB, you need to open a ticket to complete the operation. When you click **Copy Image**, you are directed to open a ticket.

5.  In the Copy Image dialog box, you can find the ID of the selected image. Also, you need to make the following configurations:
    1.  Select the **Target Region**.
    2.  Enter the **Custom Image Name** and **Custom Image Description** that are shown in the target region.
    3.  Click **OK**.
6.  Switch to the target region and check the progress. When 100% is displayed, the image is copied successfully.

    **Note:** If **Progress** is not 100%, **Status** is **Creating**. In this case, you can click **Cancel Copy** to cancel the operation. After the operation is canceled, the image information is removed from the target region.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9699/15391774316780_en-US.png)


You can also use the ECS APIs [CopyImage](intl.en-US/API Reference/Images/CopyImage.md#) and [CancelCopyImage](intl.en-US/API Reference/Images/CancelCopyImage.md#) to perform the operation.

## Next Steps {#section_kmp_xfm_xdb .section}

When the image appears as **Available**, you can use it to [create an instance](../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#) or [change the system disk](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#).

You can also view the copied snapshot in the target region.

## FAQs {#section_alb_2gm_xdb .section}

[FAQs about copying images](https://www.alibabacloud.com/help/zh/faq-detail/40569.htm?spm=a2c63.q38357.a3.5.218e437aDm1XZR)

