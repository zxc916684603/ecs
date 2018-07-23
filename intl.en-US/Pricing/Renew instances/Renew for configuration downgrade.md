# Renew for configuration downgrade {#concept_pjr_l2d_5db .concept}

After a Subscription instance expires, if renewal has not been completed by the required time, the instance is released automatically. In this case, data is lost permanently and cannot be recovered. To view status changes that occur after Subscription resources expire, see [Subscription](intl.en-US/Pricing/Subscription.md#).

You can use the **Renew for Configuration Downgrade** function to lower the configurations and reduce costs for a Subscription instance. Renew the instance before the instance is released, and at the same time set lower configurations for the next billing period.

You can also use the **Renew for Configuration Downgrade** function to change the billing method of your data disks from Subscription to Pay-As-You-Go.

## Note {#section_fv5_s4k_zdb .section}

Note the following when using Renew for Configuration Downgrade:

-   The function allows you to scale down instance specifications at the time of renewal.
-   Renewal for configuration downgrade can only be used for Subscription instances.
-   After renewal for configuration downgrade, the new package is effective from the next billing cycle. The current package continues until the end of the current billing cycle.
-   If instance specifications are changed during the renewal for configuration downgrade, you must [restart the instance](../../../../intl.en-US/User Guide/Instances/Restart an instance.md#) within the first seven days of the new billing cycle for configurations to be effective. If you restart the instance on the seventh day of the new billing period, the instance is considered to have used the original package for the first six days, and uses the downgraded package only after it is restarted.
-   Once the renewal for configuration downgrade is completed, you cannot [upgrade configurations](../../../../intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#), [increase the system disk size](../../../../intl.en-US/User Guide/Cloud disks/Resize cloud disks/Increase system disk size.md#), or increase the size of a Subscription data disk, which is attached to a [Linux instance](../../../../intl.en-US/User Guide/Cloud disks/Resize cloud disks/Linux _ Resize a data disk.md#) or a [Windows instance](../../../../intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#), during the rest of the current billing cycle.
-   You cannot cancel the renewal orders once the payment is processed.

## Procedure {#section_eql_h4k_zdb .section}

To downgrade the configuration of a Subscription instance during renewal, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find the Subscription instance. In the **Actions** column, click **Change Configuration**.
5.  In the Configuration Change Guide dialog box, select **Renew for Configuration Downgrade** and click **Continue**.
6.  On the Renew for Configuration Downgrade page, complete the following operations as necessary:
    -   Downgrade **Instance Type**. If you want to downgrade specifications for an instance, you must also set the **Restart Time** for that instance.

        **Note:** 

        -   Instance specifications that can be changed are displayed on the page. For more information about instance specifications, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#).
        -   Restarting an instance suspends your business operations on that instance. Please restart the instance during off-peak hours to reduce impact. Restart must be completed within the first seven days of the next billing cycle. However, you cannot restart an instance during the following periods each week \(UTC+8\): 12:00 midday Tuesday − 12:00 midday Wednesday, and 12:00 midday Thursday − 12:00 midday Friday.
    -   If a data disk was created while creating an instance \(Subscription\), you can change the billing method of the data disk to **Pay-As-You-Go**.
    -   If the billing method is not changed to Pay-As-You-Go for the new billing cycle, the data disk billing duration remains the same as that of the instance.
    -   Set bandwidth value.
    -   Set renewal duration.
7.  Click **Pay**, and follow the prompts to complete the process.
8.  \(Optional\) If you have changed instance specifications, or changed the public network bandwidth of a classic instance from 0 Mbit/s to a non-zero value for the first time, you must restart the instance [in the console](../../../../intl.en-US/User Guide/Instances/Restart an instance.md#) or by using the [RebootInstance](../../../../intl.en-US/API Reference/Instances/RebootInstance.md#) API within the first seven days of the next billing period. This step is necessary for the new configuration to be effective.

    **Note:** If the public bandwidth for a VPC instance is changed from 0 Mbit/s to a non-zero value for the first time, the instance does not need to be restarted.


