# Release an instance {#concept_jfp_wbf_5db .concept}

To save cost, we recommend that you release a Pay-As-You-Go instance if you no longer need it.

For a Pay-As-You-Go instance, if the [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9595.md\#](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature is not enabled, charges do not stop until the instance is released.

For a Subscription instance, the instance is automatically released after the billing cycle expires.

To release a Pay-As-You-Go instance, you have two options:

-   Release now: immediately releases the pay-per-order instance.
-   Timed Release: Customizes the release of your Pay-As-You-Go instance. The instance cannot be released automatically in less than 30 minutes from the current time. Applying new schedules overwrites the previous ones.

## Release an instance now {#section_cqg_ccn_xdb .section}

To release an instance now, follow these steps:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Set release:
    -   If you want to release an instance: Find the instance that you want to release, in the **Actions**  column, select **More** \> **Release**.
    -   If you want to release multiple instances: find the Pay-As-You-Go instances according to the  **Billing Method**, select multiple instances to release. And at the bottom of the list, click **Release Setting**.
5.  In the dialog box, select **Release Now**.
6.  Click **Next**, and then click to **Confirm**.

## Enable automatic release {#section_gqg_ccn_xdb .section}

To enable auto release, follow these steps:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-hand navigation bar, click **Instances**.
3.  Select a region.
4.  Set release:
    -   If you want to release a single instance: Find an instance that needs to be released, in the **Actions** column, select **More** \> **Release settings**.
    -   If you want to release multiple instances: find the Pay-As-You-Go instances according to the  **Billing Method**, select multiple instances to release. And at the bottom of the list, click **Release settings**.
5.  In the pop-up window, select **Scheduled release**.
6.  Turn on the Automatic Release Setting switch, and specify the release date and time. The earliest setting can only be set to automatically release an instance after 30 minutes.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9651/5454_en-US.png)

7.  Click **Next**, and then click **Confirm**.

## Disable automatic release {#section_mqg_ccn_xdb .section}

If you want to cancel the automatic release schedule of a Pay-As-You-Go instance, you can disable the feature.

To disable the automatic release feature, follow these steps:

1.  Log on to the [ECS Management Console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-hand navigation bar, click **Instances**.
3.  Select a region.
4.  Release settings:
    -   If you want to release an instance: Find the instance that you want to release, in the **Actions** column, select **More** \> **Release settings**.
    -   If you want to release multiple instances: find the Pay-As-You-Go instances according to the **Billing Method**, select multiple instances to release. And at the bottom of the list, click **Release Setting**.
5.  In the pop-up window, select **Scheduled release**.
6.  Turn off the Automatic Release Setting switch.
7.  Click **Next**, and then click **Confirm**.

## Related APIs {#section_rqg_ccn_xdb .section}

[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9861.md\#](../../../../intl.en-US/API Reference/Instances/DeleteInstance.md#)

