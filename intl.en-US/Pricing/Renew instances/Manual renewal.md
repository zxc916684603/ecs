# Manual renewal {#Manualrenew_intl .concept}

## Introduction {#section_tl3_rmf_zdb .section}

Manual renewal only applies to instances in **Subscription**  mode.

You can manually renew your instances in Subscription mode  when they are in the **Expired** status or **shut down**.   You can manually renew your instance for a month or a year. Therefore, if you want to modify the service duration of your subscription-mode instances, you can choose manual renewal.

-   Your instance will still work normally when the instance is in the **Expired**status. If the manual renewal is successfully completed within 15 days after expiration, your instance will go into the next billing cycle from the day of expiration.

    For example, if your instance expired at 00:00:00 on April 25, 2016, but you successfully renewed it for one month on May 9, 2016, the billing cycle for this renewal was from  April 25, 2016 to 00:00:00 on May 25, 2016.

-   If the instance fails to be renewed within 15 days after expiration, the instance will be shut down. Your instance will stop providing services, but Alibaba Cloud will still keep the data for you.

-   After the instance is shut down,

    -   If the renewal is successful within 15 days, your instance will go into the new billing cycle from the day of renewal.

        For example, if your instance was shut down at 00:00:00 on May 10, 2016, but you successfully renewed it for one month at 08:09:35 on May 23, 2016, the billing cycle for this renewal is from 08:09:35 on May 23, 2016 to 00:00:00 on June 24, 2016.

    -   If the renewal fails within 15 days, your instance will be automatically released on the 15th day and the data will not be restored.

## Procedure {#section_wl3_rmf_zdb .section}

You can manually renew your instance with the following steps.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  On the  Instance List page, select the expected region and locate the ECS instance by the instance name, instance ID, or status \(**Expired**\).
4.  In the  **Actions** column, click  **Renew**.
5.  On the renewal page,
    1.  Confirm the instance configuration.
    2.  Select the expected renewal length, 1 Month or 1 Year, and click  **Place Order**.
6.  On the Pay page, confirm the order information and click  **Pay** to complete the renewal operation.

