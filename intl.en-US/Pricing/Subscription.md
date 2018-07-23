# Subscription {#subs_china .concept}

The Subscription billing is a Subscription method, in which you can use the resources only after you make the payment.

## Applicable resources {#section_ilw_jv2_zdb .section}

Currently, the Subscription billing method is applicable to the following ECS resources:

-   ECS instances, including CPU configuration and memory capacity
-   Images
-   System disks and/or data disks

If you create an ECS instance of the Subscription billing method, the **Instance Cost** displayed in the lower right of the instance creation page is the total fee of the preceding three resources.

## Payment methods {#section_klw_jv2_zdb .section}

You can pay for resources in Subscription mode using either of the following methods:

-   Credit cards or PayPal account bound to your account. See [Configure your account](https://www.alibabacloud.com/help/zh/doc-detail/50517.htm) in Account Management to bind a credit card or PayPal account to your account.

-   Coupons that can be used to pay for Subscription products under your account.

    **Note:** Log on to the ECS console and select **Billing Management \>** \> **Coupon Management** to view the **Applicable Scenarios** of your coupons and determine whether the coupons are applicable to Subscription products.


## Settlement cycle {#section_mlw_jv2_zdb .section}

Resources in Subscription mode are billed on a monthly basis. The billing cycle is calculated based on the UTC+8 time zone, starting from the resource activation time to 00:00:00 on the second day after one month or one year.

Example: If you activate an ECS instance in Monthly Subscription mode at 13:23:56 March 12, 2017, the first billing cycle for the instance ends at 00:00:00 April 13, 2017.

The price unit varies depending on different resources. The following table lists the price units for various resources.

|Resource|Price unit|
|:-------|:---------|
|ECS instance|USD/month|
|Image|USD/month|
|System disk|USD/\(GiB\*month\)|
|Data disk|USD/\(GiB\*month\)|

To continue using the resources, you can renew your ECS instance at the end of a settlement cycle. For more information about the renewal procedure, see Manual renewal or Auto-renewal.

## Status changes after expiration {#section_qlw_jv2_zdb .section}

The auto-renewal feature affects the status changes of the resources when a Subscription instance expires.

## Disabled auto-renewal {#section_rlw_jv2_zdb .section}

If a Subscription instance is not set to be auto-renew, it is out of service at any time within the 24 hours from 00:00:00 of the expiration day to the next 00:00:00. If you do not manually renew the instance within 15 days after it expires, the status changes of related resources are displayed in the following table.

|Period|ECS instances and images|System disks|Data disks|Internet IP addresses|Snapshots|
|:-----|:-----------------------|:-----------|:---------|:--------------------|:--------|
|On the expiration day.|Out of service\*, and images are disabled.|Out of service, but data is retained.|Out of service, but data on cloud disks, local disks, or shared block storage devices is retained.| For an instance of the Classic network type: If an Internet IP address is assigned, it is retained.

 For a VPC-Connected ECS instance: If an Internet IP address is assigned, it is retained; If an EIP address is bound, it is retained.

 |Retained.|
|15 days after expiration day|Released automatically|Released along with the instance, and data cannot be recovered.| By default, cloud disks are released along with the instance and data on them cannot be recovered. If you have set the cloud disks not to be released along with the instance, the disks stop working.

 Local disks are released along with the instance and data on them cannot be recovered.

 Shared block storage is detached automatically from the instance.

 | For an instance of the Classic network type: If an Internet IP address is assigned, it is released.

 For a VPC-Connected ECS instance: If an Internet IP address is assigned, it is retained; If an EIP address is bound, it is unbound from the instance.

 |Automatic snapshots are automatically deleted, but those manually created are retained.Manual snapshots are not affected.|

\* When an instance is **Out of service**, you cannot connect to it, the website deployed on the instance cannot be accessed, or your business start to run abnormally.

**Note:** You cannot enable the auto-renewal feature for an instance after the instance expires.

## Enabled auto-renewal {#section_wlw_jv2_zdb .section}

If a Subscription instance is set to be renewed automatically, but it fails to be renewed in the specified period, the status changes of the related resources are displayed in the following table.

|Period| ECS instances and images|System disks|Data disks|Internet IP addresses|Snapshots|
|:-----|:------------------------|:-----------|:---------|:--------------------|:--------|
|Within 15 days after the expiration day|Running properly\*.|Running properly.|Running properly.|Retained.|Retained.|
|15 days after the expiration day|The instance is out of service at any time within the 24 hours from 00:00:00 of the 15th day after expiration to the next 00:00:00. Out of service\*\* and images are disabled.|Out of service, but data is retained.|Out of service, but data is retained.| For an instance of the Classic network type: If an Internet IP address is assigned, it is released.

 For a VPC-Connected ECS instance: If an Internet IP address is assigned, it is retained; If an EIP address is bound, it is retained.

 |Retained.|
|30 days after the expiration day|Automatically released.|Released along with the instance, and data cannot be recovered.| By default, the cloud disks are released along with the instance. If you set them not to be released along with the instance, they stop working.

 Local disks are released along with the instance.

 Shared block storage is automatically detached.

 | For an instance of the Classic network type: If an Internet IP address is assigned, it is released.

 For a VPC-Connected ECS instance: If an Internet IP address is assigned, it is released; If an EIP address is bound, it is unbound from the instance.

 |Automatic snapshots are automatically deleted, but those that are manually created are retained.|

\* **Running properly** means you can start and stop the instance properly and connect to the instance by using the **Management Terminal** in the console or other remote connection methods.

\*\* When an instance is **Out of service**, you cannot connect to it, the website deployed on the instance cannot be accessed, or your business start to run abnormally.

