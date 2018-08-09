# Elastic network interfaces {#concept_xzg_mgt_xdb .concept}

An Elastic Network Interface \(ENI\) is a virtual network interface that can be attached to an ECS instance in a VPC. By using ENIs, you can build high-availability clusters, implement failover at a lower cost, and achieve refined network management. The ENI feature is available in all the regions.

## Use cases {#section_ac1_qnw_ydb .section}

ENIs are applicable to the following use cases:

-   **Deploying a high-availability cluster**

    An ENI meets the high-availability architecture’s demand for multiple network interfaces on a single instance.

-   **Failover at a low cost**

    You can detach an ENI from an ECS instance and then attach it to another ECS instance to quickly redirect the failed instance’s traffic to a backup instance. This action recovers the service immediately.

-   **Refined network management**

    You can configure multiple ENIs for an instance. For example, you can use multiple ENIs for internal management and Internet business access respectively, so as to isolate the managerial data from business data. You can configure precisely-targeted security group rules based on the source IP address, protocols, ports, and others for each ENI to achieve secured traffic control.


## ENI types {#section_cc1_qnw_ydb .section}

ENIs are classified into two types:

-   **Primary ENI**

    The ENI created by default upon the creation of an instance in a VPC is called the **primary ENI**. The lifecycle of the primary ENI is the same as that of the instance and you are not allowed to remove the primary ENI from the instance.

-   **Secondary ENI**

    You can create a secondary ENI and attach it to an instance or detach it from the instance. The maximum number of ENIs that you can attach to one instance differs with the instance type. For more information, see [Instance type families](intl.en-US/Product Introduction/Instance type families.md#).


## ENI attributes {#section_ec1_qnw_ydb .section}

The following table displays ENI attributes.

|Attribute| Quantity|
|:--------|:--------|
|Primary private IP addresses|1|
|MAC address|1|
|Security group|Min. 1, and Max. 5|
|Description|1|
|ENI name|1|

## Limits {#section_ic1_qnw_ydb .section}

Using an ENI has the following limits:

-   By default, one account can own up to 100 ENIs in one region. For a higher quota, [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

-   The ECS instance must be in the same zone of the same region as the ENI, but they do not have to be in the same VSwitch.

-   The number of ENIs can be attached to an ECS instance is determined by the instance type. For more information, see [ECS instance type families](intl.en-US/Product Introduction/Instance type families.md#).

-   Only I/O optimized instance types support ENIs.

-   You cannot increase the instance bandwidth capability by attaching multiple ENIs.

    **Note:** The instance bandwidth capability varies with the instance type.


## Related operations {#section_kc1_qnw_ydb .section}

For those images that cannot recognize ENIs, you can connect to the instance to [configure the ENI](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Configure an ENI.md) after an instance is created.

You can operate ENIs by using the ECS console or APIs.

## By using the console {#section_lc1_qnw_ydb .section}

You can complete the following operations in the ECS console:

-   [Attach an ENI when creating an instance](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI when creating an instance.md#)
-   [Create an ENI](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#)
-   [Delete an ENI](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md#)
-   [Attach an ENI to an instance](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md#): The instance must be in the **Stopped** or **Running** status.
-   [Detach an ENI from an instance](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#): The instance must be in the **Stopped** or **Running** status.
-   [Modify attributes of an ENI](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Modify attributes of an ENI.md#): You can modify attributes of an ENI, including its name, security group, and description.
-   When an ENI is attached to an instance, you can view the information of the ENI on the instance details page and the network interfaces page.

## By using APIs {#section_oc1_qnw_ydb .section}

You can complete the following operations by using APIs:

-   [Create an ENI](../../../../intl.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md#)
-   [Delete an ENI](../../../../intl.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md#)
-   [Query ENI list](../../../../intl.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md#)
-   [Attach an ENI to an instance](../../../../intl.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface .md): The instance must be in the **Stopped** or **Running** status.
-   [Detach an ENI from an instance](../../../../intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md): The instance must be in the **Stopped** or **Running** status.
-   [Modify attributes of an ENI](../../../../intl.en-US/API Reference/Elastic network interfaces/ModifyNetworkInterfaceAttribute.md): You can modify attributes of an ENI, including its name, its security group, and its description.
-   You can use the [DescribeInstances](../../../../intl.en-US/API Reference/Instances/DescribeInstances.md#) interface to query the information of the ENI when an ENI is attached to an instance.

