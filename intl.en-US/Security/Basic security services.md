# Basic security services {#concept_610245 .concept}

Alibaba Cloud Security Center provides ECS with basic security services such as unusual logon detection, vulnerability scan, and baseline check. You can check the security status of your ECS instances in the ECS console or Security Center console.

## What are basic security services? {#section_vex_y4i_k72 .section}

Alibaba Cloud Security Center provides basic security services for ECS, which collect and visualize security logs and fingerprints of ECS assets. Main basic security services **security prevention** and **intrusion detection** are available free of charge. You can view security information about ECS assets on the **Overview** page of the ECS console or in the Security Center console. For more information, see [Security Center Documentation](../../../../../reseller.en-US/Product Introduction/What is Security Center?.md#).

## Security Center agent {#section_wwj_msv_75h .section}

The Security Center agent is a lightweight security control that can be installed on ECS instances. If the Security Center agent is not installed on an ECS instance, the ECS instance is not protected by Security Center. The security data of this instance, such as vulnerabilities, alerts, and baseline vulnerabilities, and asset fingerprints, will not be displayed in the ECS console. For the installation paths of the Security Center agent, see [Security Center agent](../../../../../reseller.en-US/Access Cloud Security Center/Security Center agent.md#).

You can perform the following steps to install or uninstall the Security Center agent:

-   Have the Security Center agent automatically installed when you create an ECS instance.

    1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
    2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
    3.  In the top navigation bar, select a region.
    4.  Create an ECS instance by referring to [Create an instance by using the wizard](../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#). In the **Image** section on the Basic Configurations page, select **Security Enhancement**. The Security Center agent is then automatically installed on the new ECS instance.
    **Note:** You can also automatically install the Security Center agent by using the following method: Call the [RunInstances](../reseller.en-US/API Reference/Instances/RunInstances.md#) operation with `SecurityEnhancementStrategy` set to Active.

-   Manually install the Security Center agent on an existing ECS instance.
    1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
    2.  On the Overview page, click the shield-like **Alibaba Cloud Security** icon to log on to the Security Center console.
    3.  Install the Security Center agent by referring *to* [Install the Security Center agent](../../../../../reseller.en-US/Access Cloud Security Center/Install the Security Center agent.md#) in the Security Center documentation.
-   Uninstall the Security Center agent.
    1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
    2.  On the Overview page, click the **Alibaba Cloud Security** icon to log on to the Security Center console.
    3.  Uninstall the Security Center agent by referring *to* [Uninstall the Security Center agent](../../../../../reseller.en-US/Access Cloud Security Center/Uninstall the Security Center agent.md#) in the Security Center documentation.

## Check the security status of your ECS instance {#section_isg_h7w_f1f .section}

Perform the following steps to check the security status of your ECS instance:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
3.  In the top navigation bar, select a region.
4.  Check the security status of your ECS instance in either of the following ways:
    -   On the **Instances** page, view the Alibaba Cloud Security icon in the Monitoring column corresponding to your ECS instance. If the icon is orange, there are vulnerability or security alerts present in the instance. You can click the icon to log on to the Security Center console and view the alert details.
    -   Click the instance ID to go to the **Instance Details** page. On the **Instance Details** page, view the Alibaba Cloud Security icon. If the icon is orange, there are vulnerability or security alerts present in the instance. You can click the icon to log on to the Security Center console and view the alert details.

## Configure alert notifications {#section_33m_fc1_z40 .section}

Basic security services allow you to configure alert notifications to be sent for security alert items by SMS, email, or internal message. Perform the following steps to configure alert notifications:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  On the Overview page, click the **Alibaba Cloud Security** icon to log on to the Security Center console.
3.  In the left-side navigation pane, Choose **Operation \> Settings**. On the Settings page, click the **Notifications** tab.
4.  In the **Alerts** row, select severities and configure the methods and time for sending alert notifications.

    **Note:** If you have upgraded to Alibaba Cloud Security Advanced or Enterprise Edition, *see* [Security events](../../../../../reseller.en-US/Threat Detection/Events/Security events.md#) in the Security Center documentation for more alert notification methods.


## Related topics {#section_zkg_npr_pyl .section}

-   [Feature comparison among Basic/Advanced/Enterprise Edition](../../../../../reseller.en-US/Product Introduction/Features.md#)
-   [List of Security Center FAQs](../../../../../reseller.en-US/FAQ/List of Security Center FAQs.md#)

