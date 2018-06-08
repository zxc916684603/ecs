# Auto-renewal {#autoRenew_intl .concept}

Automatic maid applies only to, package year month, instance. This article describes the automatic functions and describes how to turn them on and off.

## Introduction {#section_pvl_5nk_zdb .section}

The auto-renewal service can be activated any time after the ECS instance is purchased and before it expires. 

**Note:** It cannot be activated after a Subscription instance expires. 

The monthly subscription service automatically renews the instance on a monthly basis when a monthly subscription instance expires. The annual subscription service automatically renews the instance on a yearly basis when a yearly subscription instance expires.

**Note:** The auto-renewal service does not support switching between monthly subscription and annual subscription.   If you want to change the service duration for an instance, you can choose the Manual renewal service.

After you activate the auto-renewal service,After the automatic copy function is turned on,

-   You are notified of the expiration of your Subscription instances on the seventh day, third day, or one day before the expiration day \(T\).

-   Alibaba Cloud charges the subscription fee to your linked credit card or PayPal account on the expiration day \(T\).  If the fee payment fails, Alibaba Cloud tries again on Day 7 \(T+6\) and Day 15 \(T+14\) until the payment is successful.  If all the three payment attempts fail, the instance shuts down.

    -   If the payment for the subscription is successful, your instance is no longer be in the Expired status and the next billing cycle starts from the expiration day.

        For example, if your monthly subscription instance expired at 00:00:00 on April 25, 2016, but it was successfully renewed automatically on May 9, 2016, the billing cycle for this renewal is from 00:00:01 on April 25, 2016 to 00:00:00 on May 25, 2016.

    -   If all the three payment attempts fail, the instance shuts down 15 days after its expiration day. And, if the instance shuts down, it stops providing services and you cannot log on or even remotely connect to the instance. At this point, you can only choose  Manual renewal. If the instance is not renewed within 15 days after the expiration day, the instance is released and the data is lost.
    -   Alibaba Cloud sends a notification email to your linked email address for each failed auto-renewal attempt. Therefore, keep checking your mailbox frequently so that you do not miss any such notifications and can take necessary action to avoid further business impact.
-   Alibaba Cloud charges the subscription fee to your linked credit card at 08:00:00 \(UTC+8\) on the date of expiry \(T\), Day 7 \(T+6\), or Day 15 \(T+14\).  But Alibaba Cloud daily performs auto-renewal in turn on all the ECS instances that have been expired, so your fee may be charged after 08:00:00 \(UTC+8\), but not later than 18:00:00 \(UTC+8\).


If you manually renew the instance even before the auto-renewal is attempted, your instance gets renewed and no auto-renewal is attempted for the current billing cycle. And, the instance goes into the next billing cycle.

## Activate auto-renewal {#section_tvl_5nk_zdb .section}

To activate the auto-renewal service, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  At the top of the page, choose **Billing Management** \> **Renew**.
3.  In the left-side navigation pane, click **Elastic Compute Service**。
4.  On the Renew page, select the  **Manually Renew** tab.
5.  Find an instance, and in the  **Actions** column, click **Enable Auto-Renew**.

    **Note:** If you need to activate auto-renewal for multiple instances, after you select multiple instances that have not expired, click at the bottom of the list Enable Auto-Renew.

6.  On the  Enable Auto-Renew dialog box, click **Enable Auto-Renew**.

Then you can select the Auto-Renew tab  and then find the instance.

## Deactivate auto-renewal {#section_xvl_5nk_zdb .section}

To deactivate the auto-renewal service for an instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  At the top of the page, choose **Billing Management** \> **Renew**.
3.  In the left-side navigation pane, click **Elastic Compute Service**.
4.  On the Renew page, select the **Auto-Renew**  tab.
5.  Find the instance, and in the **Actions** column, click **Modify Auto-Renew**.

    **Note:** If you need to cancel auto-renewal for multiple instances, after you select multiple instances that have not expired, click at the bottom of the list, click **Modify Auto-Renew**.

6.  On the Modify Auto-Renew dialog box, select  **Disable Auto-Renew** and then click **OK**.

After you cancel auto-renewal, click the **Manually Renew**  tab.

