# System events {#concept_gdc_tyz_xdb .concept}

**System events** are scheduled and recorded maintenance events of ECS. System events occur when security updates, invalid operations, or unexpected failures are detected in your ECS instances. Your instances will start, restart, stop, or be released when system events occur.

## Routine maintenance versus system events {#section_mnp_5yz_xdb .section}

ECS instances are the core component used to establish your applications. After you select and start ECS instances, initiate configuration, and start to deploy applications, the health of the ECS instance is crucial to your business. To guarantee the backend performance and security of ECS, we perform routine maintenance for the physical servers. When we scan for the hardware and software faults or potential risks on the physical servers, we live-migrate your instances to healthy servers. This is routine maintenance. Unlike system events, you do not receive any notification and also, your instances are not impacted, while the routine maintenance is in progress.

Once system events occur, you are notified about the default actions and the time scheduled to perform these actions on your instances. For planned system events, information such as the impact of the event on the instance and the expected execution point is told in advance. To prevent impact on your business, we recommend that you back up the data and distribute incoming traffic before handling system events. You can query the system events history for the last week later, for further analysis of faulty diagnosis and faulty replay.

## Limits {#section_nnp_5yz_xdb .section}

Phased-out instance types including c1, c2, m1, m2, s1, s2, s3, and t1 do not support system events. For more information, see [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9548.md\#](../../../../intl.en-US/Product Introduction/Instance type families.md#).

## Event types {#section_onp_5yz_xdb .section}

The following table describes the types of ECS system events.

|Category|Event type|Parameter|
|Scheduled system event|An instance restarts after planned system maintenance or security update.|`SystemMaintenance.Reboot`|
|Unexpected system event|An instance restarts after unexpected system failures.|`SystemFailure.Reboot`|
|An instance restarts after unexpected instance failures.|`InstanceFailure.Reboot`|

## Event status {#section_snp_5yz_xdb .section}

The following table describes the status of a system event during its lifecycle.

|Status|Status attribute|Description|
|Scheduled|Intermediate status|The system event is scheduled but not performed.|
|Avoided|Stable status|You have taken the actions in advance within the [user operation period](intl.en-US/User Guide/Monitoring/System events.md#ul_ynp_5yz_xdb).|
|Executing|Intermediate state|The response plan of the system event is being performed.|
|Executed|Stable status|The system event has been fixed.|
|Canceled|Stable status|ECS cancels the scheduled system event.|
|Failed|Stable status|The system event is not fixed.|

## System event periods {#section_xnp_5yz_xdb .section}

System events observe the following two periods:

-   **User operation period**: The period between initiation and scheduled time of system events. Normally, you will receive a notification from 24 to 48 hours before an event is fixed. During this period, choose the recommended methods to handle system events in advance. You can also wait until the default actions are triggered.
-   System action period: Generally, if you wait until we take the default action, system events are automatically fixed within 6 hours after the system action period begins at a scheduled time. Later you receive the report of system events.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9748/3942_en-US.png)

    **Note:** Only scheduled system events have user operation period. Unexpected system events that are caused by emergency failures or invalid operations do not have **user operation periods** however, they have a short **system action period**. Once unexpected system events occur, you will receive notifications, and you cannot take any action. However, you can query the system events history for fault diagnosis, cause analysis, or data recovery.


## View system events {#SystemAlert .section}

If a system event is scheduled, the **Unsettled events** button in the ECS console shows a highlighted tag to remind you to check the event.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select **Overview**.
3.  Select **Unsettled events** from the navigation pane on the right-side of the Overview page.
4.  On the **Unsettled events** page, you can see the list of instance IDs, regions, and running status, system events, recommended user operations, and buttons for operations. Optionally, you can choose recommended user operations under the Actions column to handle the system events.

**API operation**: Call [DescribeInstancesFullStatus](../../../../intl.en-US/API Reference/Operations and monitoring/DescribeInstancesFullStatus.md) to view system events.

## View system events history {#SystemAlertHistory .section}

On the All events page, you can query the system events history within the last week for faulty diagnosis and faulty replay.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  On the left-side navigation pane, select **Overview**.
3.  Select **Unsettled events** from the navigation pane on the right-side of the **Overview** page.
4.  Click **All events**, and on the All events page, click**Scheduled system event \>** \> **Instances.**You can see the list of instance IDs, event types, and regions, and event status.

**API operation**: Call [DescribeInstancesFullStatus](../../../../intl.en-US/API Reference/Operations and monitoring/DescribeInstancesFullStatus.md) to view system events history.

## System event suggestions {#section_e2q_3zz_xdb .section}

System events make you perceptible to underlying components of Alibaba Cloud ECS. You can optimize the O&M of instances based on system events. We recommend the following actions to handle system events.

|Event type|Parameter|Recommended|
|An instance restarts after pending system maintenance.|SystemMaintenance.Reboot|Use either of the following methods at a convenient time within the user operation period:-   [EN-US\_TP\_9649.md\#](intl.en-US/User Guide/Instances/Restart an instance.md#) in the ECS console.
-   Call API [RebootInstance](../../../../intl.en-US/API Reference/Instances/RebootInstance.md).

**Note**: Instance restart performed in the instance or from the instance list has no effect on this type of system events.


We recommend that you [EN-US\_TP\_9687.md\#](intl.en-US/User Guide/Snapshots/Create snapshots.md#) \([CreateSnapshot](../../../../intl.en-US/API Reference/Snapshots/CreateSnapshot.md)\) for the attached disks to back up your data.|
|An instance restarts after unexpected system failures.|SystemFailure.Reboot|When you receive the notification, your instances are being restarted. We recommend that you verify the recovery of instances and applications after the event.|
|An instance restarts after unexpected instance failures.|InstanceFailure.Reboot|When you receive the notification, your instances are being restarted. We recommend that you:-   Verify the recovery of instances and applications.
-   Analyze the cause of instance crashes to prevent potential events.

|

