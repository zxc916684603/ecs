# Change EIP Internet bandwidth {#concept_eqg_jbf_5db .concept}

If you are using a VPC-Connected ECS instance, and [an Elastic IP \(EIP\) address is bound to it](https://www.alibabacloud.com/help/zh/doc-detail/27714.htm), you can use the **Change Bandwidth** feature to change the Internet bandwidth any time to meet your business needs. You can use this feature irrespective of your billing method.

## Restrictions {#section_jzn_d3z_xdb .section}

The **Change Bandwidth** feature only applies to the VPC-connected instance, and an Elastic IP \(EIP\) address must have been bound to the instance.

## Change bandwidth {#section_hdd_j3z_xdb .section}

To change the Internet bandwidth of an EIP address, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to which an EIP address is bound, and in the **Actions** column, click **Change Configuration**.
5.  In the Change Configurations dialog box, select change bandwidth, and click **Continue**.
6.  On the Confirm Order page, set the new peak bandwidth.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9646/15367414695429_en-US.png)

7.  Click **Activate** and finish changing the bandwidth as instructed on the page.

## Related operations {#section_wtj_j3z_xdb .section}

For Subscription instances of the classic network type or VPC-connected ECS instances to which no EIP addresses are bound, you can use the following features to change the Internet bandwidth:

-   Use the [Upgrade Configuration](https://www.alibabacloud.com/help/zh/doc-detail/25438.htm) feature to change the Internet bandwidth immediately.

-   Use the [Renew for Configuration Downgrade](https://www.alibabacloud.com/help/zh/doc-detail/48363.htm) feature to change the Internet bandwidth for the next billing cycle.


