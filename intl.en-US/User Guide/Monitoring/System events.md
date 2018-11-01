# System events {#concept_gdc_tyz_xdb .concept}

System events are scheduled and recorded maintenance events of your ECS resources. System events occur when security updates, invalid operations, expiration of Subscription instances, overdue payment, or unexpected failures are detected in your ECS instances. Your instances will start, restart, stop, or be released when system events occur.

## Routine maintenance versus system events {#section_mnp_5yz_xdb .section}

ECS instances are the core component used to establish your applications. After you select and start ECS instances, initiate configuration, and start to deploy applications, the health of the ECS instance is crucial to your business. To guarantee the backend performance and security of ECS, we perform routine maintenance for the physical servers. When we scan for the hardware and software faults or potential risks on the physical servers, we live-migrate your instances to healthy servers. This is routine maintenance. Unlike system events, you do not receive any notification and also, your instances are not impacted, while the routine maintenance is in progress.

Once system events occur, you are notified about the default actions and the time scheduled to perform these actions on your instances. For planned system events, information such as the impact of the event on the instance and the expected execution point is told in advance. To prevent impact on your business, we recommend that you back up the data and distribute incoming traffic before handling system events. You can query the system events history for the last week later, for further analysis of faulty diagnosis and faulty replay.

## Limits {#section_nnp_5yz_xdb .section}

Phased-out instance types, including but not limited to sn2, sn1, t1, s1, s2, s3, m1, m2, c1, c2, c4, ce4, cm4, n1, n2 and e3, do not support system events. For more information, see [Instance type families](../reseller.en-US/Product Introduction/Instance type families.md#).

## Event types {#section_onp_5yz_xdb .section}

The following table describes the types of ECS system events.

|Category|Event type|Parameter|
|:-------|:---------|:--------|
|Scheduled restart|An instance restarts after planned system maintenance or security update.|`SystemMaintenance.Reboot`|
|Unexpected restart|An instance restarts after unexpected system failures.|`SystemFailure.Reboot`|
|An instance restarts after unexpected instance failures.|`InstanceFailure.Reboot`|
|Stop instances|Subscription instances stop due to expiration.|`InstanceExpiration.Stop`|
|Pay-As-You-Go instances stop due to overdue payment.|`AccountUnbalanced.Stop`|
|Release instances|Subscription instances are released after several days of expiration.|`InstanceExpiration.Delete`|
|Pay-As-You-Go instances are released due after several days of overdue payment.|`AccountUnbalanced.Delete`|

## Event status {#section_snp_5yz_xdb .section}

The following table describes the status of a system event during its lifecycle.

|Status|Status attribute|Description|
|:-----|:---------------|:----------|
|Scheduled|Intermediate status|The system event is scheduled but not performed.|
|Avoided|Stable status|You have taken the actions in advance within the [user operation period](#).|
|Executing|Intermediate state|The response plan of the system event is being performed.|
|Executed|Stable status|The system event has been fixed.|
|Canceled|Stable status|ECS cancels the scheduled system event.|
|Failed|Stable status|The system event is not fixed.|

## System event periods {#section_xnp_5yz_xdb .section}

System events observe the following two periods:

-   **User operation period**: The period between initiation and scheduled time of system events. Normally, you receive a notification from 24 to 48 hours before a system failure event is fixed, from 3 days before a Subscription instances is stopped, and 1 hour before a Pay-As-You-Go instance is stopped. Instances are released 15 days later if no renewal or recharge are made. During this period, you can choose the recommended methods to handle system events in advance. You can also wait until the default actions are triggered.
-   **System action period**: Generally, if you wait until we take the default action, system events are automatically fixed within 6 hours after the system action period begins at a scheduled time. Later you receive the report of system events.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9748/15410419083942_en-US.png)

    **Note:** Only scheduled system events have user operation period. Unexpected system events that are caused by emergency failures or invalid operations do not have user operation periods. Once unexpected system events occur, you will receive notifications, but you cannot take any action. However, you can query the system events history for fault diagnosis, cause analysis, or data recovery.


## View system events {#SystemAlert .section}

If a system event is scheduled, the **Unsettled events** button in the ECS console shows a highlighted tag to remind you to check the event.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select **Overview**.
3.  Select **Unsettled events** from the navigation pane on the right-side of the Overview page.
4.  On the **Unsettled events** page, you can see the list of instance IDs, regions, and running status, system events, recommended user operations, and buttons for operations. Optionally, you can choose recommended user operations under the Actions column to handle the system events.

**API operation**: Call [DescribeInstancesFullStatus](../reseller.en-US/API Reference/Operations and monitoring/DescribeInstancesFullStatus.md) to view system events.

## View system events history {#SystemAlertHistory .section}

On the All events page, you can query the system events history within the last week for faulty diagnosis and faulty replay.

1.  [ECS console](https://partners-intl.console.aliyun.com/#/ecs)
2.  On the left-side navigation pane, select **Overview**.
3.  Select **Unsettled events** from the navigation pane on the right-side of the **Overview** page.
4.  Click **All events**, and on the All events page, click **Scheduled system event** \> **Instances.**You can see the list of instance IDs, event types, and regions, and event status.

**API operation**: Call [DescribeInstanceHistoryEvents](../reseller.en-US/API Reference/Operations and monitoring/DescribeInstanceHistoryEvents.md#) to view system events history.

## System event suggestions {#section_e2q_3zz_xdb .section}

System events make you perceptible to underlying components of Alibaba Cloud ECS. You can optimize the O&M of instances based on system events. We recommend the following actions to handle system events.

|Event type|Parameter|Recommended|
|:---------|:--------|:----------|
|An instance restarts after pending system maintenance.|SystemMaintenance.Reboot|Use either of the following methods at a convenient time within the user operation period:-   [Restart the instance](reseller.en-US/User Guide/Instances/Restart an instance.md#) in the ECS console.

-   Call API [RebootInstance](../reseller.en-US/API Reference/Instances/RebootInstance.md).

**Note:** Instance restart performed in the instance or from the instance list has no effect on this type of system events.


We recommend that you [Create snapshots](reseller.en-US/User Guide/Snapshots/Create snapshots.md#) \([CreateSnapshot](../reseller.en-US/API Reference/Snapshots/CreateSnapshot.md)\) for the attached disks to back up your data.|
|An instance restarts after unexpected system failures.|SystemFailure.Reboot|When you receive the notification, your instances are being restarted. We recommend that you verify the recovery of instances and applications after the event.|
|An instance restarts after unexpected instance failures.|InstanceFailure.Reboot|When you receive the notification, your instances are being restarted. We recommend that you:-   Verify the recovery of instances and applications.

-   Analyze the cause of instance crashes to prevent potential events.


|
|A Subscription instance stops due to expiration.|InstanceExpiration.Stop|You can either [renew the instances](../reseller.en-US/Pricing/Renew instances/Renewal overview.md#) or wait for the instances to stop.|
|A Pay-As-You-Go instance stops due to overdue payment.|AccountUnbalanced.Stop| You can either keep sufficient balance of your credit card or wait for the instances to stop.

 |
|A Subscription instance is released due to expiration.|InstanceExpiration.Delete|You can either [renew the instances](../reseller.en-US/Pricing/Renew instances/Renewal overview.md#) or wait for the instances to be released.|
|A Pay-As-You-Go instance is released due to overdue payment.|AccountUnbalanced.Delete| You can either keep sufficient balance of your credit card or wait for the instances to be released.

 |

