# What is ECS? {#concept_rhf_xgv_tdb .concept}

This article gives a brief introduction to what ECS is, and the resources and services that it involves.

Elastic Compute Service \(ECS\) is a type of computing service that features elastic processing capabilities. ECS has a simpler and more efficient management mode than physical servers. You can create instances, change the operating system, and add or release any number of ECS instances at any time to fit your business needs. An ECS instance is a virtual computing environment that includes CPU, memory, and other basic computing components. An instance is the core component of ECS and is the actual operating entity offered by Alibaba Cloud. Other resources, such as disks, images, and snapshots, can only be used in conjunction with an ECS instance.

The following figure illustrates the concept of an ECS instance. You can use the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to configure the instance type, disks, operating system, and other affiliated resources.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9543/15402884994795_en-US.png)

## Basic concepts {#section_jkn_4qj_ydb .section}

It is helpful to understand the following concepts before you use ECS:

-   [Region and zone](https://partners-intl.aliyun.com/help/doc-detail/40654.htm): A physical location where a data center is located.
-   [ECS instance](reseller.en-US/Product Introduction/Instances/What are ECS instances.md#): A virtual computing environment that includes the CPU, memory, operating system, bandwidth, disks, and other basic computing components.
-   [Instance types](reseller.en-US/Product Introduction/Instance type families.md#): The specifications of an ECS instance, including the number of vCPU cores, memory, and networking performance. The instance type of an ECS instance determines its compute capability.
-   [Images](reseller.en-US/Product Introduction/Images.md#): A running environment template for ECS instances. It generally includes an operating system and preinstalled software.
-   [Block storage](reseller.en-US/Product Introduction/Block storage/What is block storage?.md#): Block level storage products for your ECS, including [Cloud disks and Shared Block Storage](reseller.en-US/Product Introduction/Block storage/Cloud disks and Shared Block Storage.md#) based on the distributed storage architecture and [local disks](reseller.en-US/Product Introduction/Block storage/Local disks.md#) located on the physical server that an ECS instance is hosted on.
-   [Snapshots](reseller.en-US/Product Introduction/Snapshots/What are ECS snapshots.md#): A copy of the data on an elastic block storage device as it was at a specific point in time.
-   [Network types](reseller.en-US/Product Introduction/Network and security/Network types.md#): Alibaba Cloud provides two network types, including
    -   Virtual Private Cloud \(VPC\): A private network established in Alibaba Cloud. VPCs are logically isolated from other virtual networks in Alibaba Cloud. For more information, see [What is VPC](../../../../reseller.en-US/Product Introduction/What is VPC?.md#).
    -   Classic network: A network majorly deployed in the public infrastructure of Alibaba Cloud.
-   [Security group](reseller.en-US/Product Introduction/Network and security/Security group.md#): A logical group of instances that are in the same region and have the same security requirements and mutual trust. A security group works as a virtual firewall for the ECS instances inside it.

## Related services {#section_cxf_5sg_kfb .section}

The following services are frequently used together with ECS:

-   [Alibaba Cloud marketplace](https://partners-intl.aliyun.com/marketplace/vodafone/) is an online market. You can purchase software infrastructure, developer tools, and business software provided by third-party partners. If you have software you want to sell, you can become a marketplace service provider. For more information, see [What is Alibaba Cloud Marketplace](https://partners-intl.aliyun.com/help/product/30488.htm).

    Auto Scaling enables you to dynamically scale your computing capacity up or down to meet the workload of your ECS instances according to scaling policies you specify. It also reduces the need for manual provision. For more information, see [What is Auto Scaling](https://partners-intl.aliyun.com/help/product/25855.htm).

-   Container Service enables you to manage the lifecycle of containerized applications by using Docker and Kubernetes. For more information, see [What is Container Service](https://partners-intl.aliyun.com/help/product/25972.htm).

-   Server Load Balancer distributes the incoming traffic among multiple ECS instances according to the configured forwarding rules. For more information, see [What is Server Load Balancer](https://partners-intl.aliyun.com/help/product/27537.htm).

-   CloudMonitor manages ECS instances, system disks, Internet bandwidth, and other resources. For more information, see [What is CloudMonitor](https://partners-intl.aliyun.com/help/product/28572.htm).

-   Server Guard \(Server Security\) provides real-time awareness and defense against intrusion events, which safeguards the security of your ECS instances. For more information, see [What is Server Guard](https://partners-intl.aliyun.com/help/product/28449.htm).

-   Anti-DDoS Basic prevents and mitigates DDoS attacks by routing traffic away from your infrastructure. Alibaba Cloud Anti-DDoS Pro safeguards your ECS instances under high-volume DDoS attacks. For more information, see [What is Anti-DDoS Basic](https://partners-intl.aliyun.com/help/doc-detail/28399.htm) and [What is Anti-DDoS Pro](https://partners-intl.aliyun.com/help/doc-detail/28464.htm).

-   Alibaba Cloud SDK enables you to access Alibaba Cloud services and to manage your applications by using the programming language of your choice. For more information, see [Developer Resources](https://partners-intl.aliyun.com/vodafone/support/developer-resources). You can use [OpenAPI Explorer](https://api.aliyun.com/) to debug ECS API and generate the SDK Demo.


## Operations {#section_lsd_yqj_ydb .section}

Alibaba Cloud provides an intuitive operation interface for you to perform most ECS tasks. You can log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to operate ECS instances. For more information, see [User Guide](../../../../reseller.en-US/User Guide/Quick reference.md#).

You can use API to manage your ECS instances. For more information, see [API References](../../../../reseller.en-US/API Reference/Introduction.md#). You can also use Alibaba Cloud CLI to call API to manage ECS instances. For more information, see [Alibaba Cloud Command Line Interface](https://partners-intl.aliyun.com/help/product/29991.htm).

## ECS pricing and billing {#section_vq5_brj_ydb .section}

ECS supports both Subscription and Pay-As-You-Go billing methods. For more information, see [Billing methods](../../../../reseller.en-US/Pricing/Pricing overview.md#).

For the price information, see the Pricing page.

## Learning Path {#section_ox4_swp_52b .section}

