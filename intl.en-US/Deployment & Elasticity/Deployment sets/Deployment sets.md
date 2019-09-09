# Deployment sets {#concept_1846521 .concept}

A deployment set is a distribution strategy to control ECS instances and implement disaster recovery and business availability when ECS instances are created.

## Deployment strategy {#section_xlw_glo_09x .section}

You can use a deployment set to distribute your ECS instances to different physical servers to guarantee high availability and set up underlying disaster discovery. When you create ECS instances in a deployment set, Alibaba Cloud will start the instances on different physical servers within the specified region based on your configured deployment strategy.

Deployment sets support the high availability strategy:

-   When you use the high availability strategy, all the ECS instances within your deployment set are strictly distributed across different physical servers within the specified region. The high availability strategy applies to application architectures where several ECS instances need to be isolated from each other. The strategy significantly reduces the chances of services becoming unavailable.
-   When using the high availability strategy, you may not be able to create ECS instances when there is a supply shortage in the specified region. Furthermore, with the No Fees for Stopped Instances \(VPC-Connected\) feature enabled, pay-as-you-go instances may fail to be started next time. If this problem occurs, wait a while and then try again or create a new instance.

## Deployment example {#section_6c8_xlr_7c1 .section}

The following figure shows a typical example of how to use a deployment set to improve business reliability. In the deployment set, four ECS instances are distributed to four different physical servers.

![Deployment sets](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21423/156799815957239_en-US.png)

If you want to achieve low latency communication between ECS instances, we recommend that you make sure the network types of the instances are the same. For example, select the same VPC for the ECS instances when you create them.

## Billing details {#section_lcd_i5j_ros .section}

Deployment sets are free of charge, but you will be billed for the usage of ECS instances, disks, snapshots, images, and public bandwidth in deployment sets. For more information, see [Billing overview](../../../../reseller.en-US/Pricing/Billing overview.md#).

## Limits {#section_ett_1lb_4ut .section}

Before you use deployment sets, note that:

-   Deployment sets cannot be merged.
-   You cannot create preemptible instances in deployment sets.
-   You cannot create Dedicated Hosts in deployment sets.
-   When you create ECS instances in a deployment set, you can create a maximum of seven ECS instances in each zone. This limit varies depending on your ECS usage. You can use the following formula to calculate the maximum number of ECS instances that can be created in an Alibaba Cloud region: 7 x number of zones.
-   The instance families that can be created in deployment sets include c5, d1, d1ne, g5, hfc5, hfg5, i2, ic5, r5, se1ne, sn1ne, and sn2ne. For more information about instance types and their performance, see [Instance families](../../../../reseller.en-US/Instances/Instance families.md#).
-   Supply shortages may result in a failure to create an instance or restart a pay-as-you-go instance with the No Fees for Stopped Instances \(VPC-Connected\) feature enabled in a deployment set. For more information, see [No fees for stopped VPC instances](../../../../reseller.en-US/Pricing/No fees for stopped VPC instances.md#).

## Operations in the ECS console {#section_bar_s2y_9jo .section}

-   [EN-US\_TP\_21498.md\#](reseller.en-US/Deployment & Elasticity/Deployment sets/Create deployment sets.md#)
-   [Create an instance in a deployment set](reseller.en-US/Deployment & Elasticity/Deployment sets/Create an instance in a deployment set.md#)
-   [Change the deployment set of an instance](reseller.en-US/Deployment & Elasticity/Deployment sets/Change the deployment set of an instance.md#)
-   [Manage deployment sets](reseller.en-US/Deployment & Elasticity/Deployment sets/Manage deployment sets.md#)

## API operations {#section_66k_83u_34h .section}

-   Create a deployment set:[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_21439.md\#](../../../../reseller.en-US/API Reference/Deployment sets/CreateDeploymentSet.md#)
-   Add an instance to a deployment set or migrate an instance from one deployment set to another:[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_21654.md\#](../../../../reseller.en-US/API Reference/Deployment sets/ModifyInstanceDeployment.md#)
-   Query deployment sets:[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_21454.md\#](../../../../reseller.en-US/API Reference/Deployment sets/DescribeDeploymentSets.md#)
-   Modify the properties of a deployment set:[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_21453.md\#](../../../../reseller.en-US/API Reference/Deployment sets/ModifyDeploymentSetAttribute.md#)
-   Delete a deployment set:[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_21452.md\#](../../../../reseller.en-US/API Reference/Deployment sets/DeleteDeploymentSet.md#)

