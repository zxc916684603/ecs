# Elastic network interfaces {#concept_xzg_mgt_xdb .concept}

An Elastic Network Interface \(ENI\) is a virtual network interface that can be attached to an ECS instance in a VPC. By using ENIs, you can build high-availability clusters, implement failover at a lower cost, and achieve refined management network. The ENI feature is available in all the regions.

## Use cases {#section_ac1_qnw_ydb .section}

ENIs are applicable to the following use cases:

-   **Deploying a high-availability cluster**

    An ENI meets the high-availability architecture’s demand for multiple network interfaces on a single instance.

-   **Failover at a low cost**

    You can detach an ENI from an ECS instance and then attach it to another ECS instance to quickly redirect the faulted instance’s traffic to a backup instance. This action recovers the service immediately.

-   **Refined management network**

    You can configure multiple ENIs for an instance. For example, you can use multiple ENIs for internal management and for Internet business access, respectively, to isolate the managerial data and business data. You can configure precisely-targeted security group rules based on the source IP address, protocols, ports, and others for each ENI for secured traffic control.


## ENI types {#section_cc1_qnw_ydb .section}

ENIs are classified into two types:

-   **Primary ENI**

    The ENI created by default with the creation of an instance in a VPC is called the **primary ENI**. The lifecycle of the primary ENI is synchronized with the instance and you are not allowed to remove the primary ENI from the instance.

-   **Secondary ENI**

    You can create a secondary ENI and attach it to an instance or detach it from the instance. The maximum number of ENIs that you can attach to one instance differs according to the instance type. For more information, see [EN-US\_TP\_9548.md\#](intl.en-US/Product Introduction/Instance type families.md#).


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

-   The number of ENIs can be attached to an ECS instance is determined by the instance type. For more information, see [EN-US\_TP\_9548.md\#](intl.en-US/Product Introduction/Instance type families.md#).

-   Only I/O optimized instance types support ENIs.

-   You cannot increase the instance bandwidth capability by attaching multiple ENIs.

    **Note:** The instance bandwidth capability varies according to the instance type.


## Related operations {#section_kc1_qnw_ydb .section}

For those images that cannot recognize ENIs, you can connect to the instance to configure the ENI after an instance is created.

## By using the console {#section_lc1_qnw_ydb .section}

You can complete the following operations in the ECS console:

-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9733.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI when creating an instance.md#)
-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9734.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#)
-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9738.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md#)
-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9735.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md#)The instance must be in the **Stopped** 或 **Running** status.
-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9736.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#)The instance must be in the **Stopped** 或 **Running** status.
-   [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9737.md\#](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Modify attributes of an ENI.md#)You can modify attributes of an ENI, including its name, security group, and description.
-   When an ENI is attached to an instance, you can view the information of the ENI in the instance details page and the network interfaces page.

## By using APIs {#section_oc1_qnw_ydb .section}

You can complete the following operations by using APIs:

-   [Create an ENI](../../../../intl.en-US/API Reference/Elastic network interfaces/CreateNetworkInterface.md#)
-   [Delete an ENI](../../../../intl.en-US/API Reference/Elastic network interfaces/DeleteNetworkInterface.md#)
-   [Query ENI list](../../../../intl.en-US/API Reference/Elastic network interfaces/DescribeNetworkInterfaces.md#)
-   Attach an ENI to an instance: The instance must be in the **Stopped** 或 **Running** status.
-   Detach an ENI from an instance: The instance must be in the **Stopped** 或 **Running** status.
-   Modify ENI attributes: You can modify attributes of an ENI, including its name, its security group, and its description.
-   You can use [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9865.md\#](../../../../intl.en-US/API Reference/Instances/DescribeInstances.md#) the DescribeInstances interface to query the information of the ENI when an ENI is attached to an instance.

