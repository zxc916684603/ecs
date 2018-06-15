# Attach an ENI when creating an instance {#concept_twf_4jj_zdb .concept}

You can attach an ENI when creating an ECS instance in the ECS console.  For more information about instance creation, see Create an ECS Instance.  This document focuses on notes for attaching an ENI during ECS instance creation.

We recommend that you consider the following items when attaching an ENI during ECS instance creation:

1.  Basic Configurations:
    -   Region: elastic network cards are supported in all regions.
    -   Instance Type: Select an instance type that supports ENI. The selected instance type must be I/O optimized.  For more information, see Instance type families.
    -   Image: Only the following images can automatically recognize ENIs without any additional configuration.
        -   Centos 7.3 64-bit
        -   Centos 6.8 64-bit
        -   Windows Server 2016 Data Center Edition 64-bit
        -   Windows Server 2012 R2 Data Center Edition 64-bit

            For other images, you must configure ENI to enable the created instance to recognize the ENI.

2.  Networking:
    -   Network: Select VPC, and then select a VPC and a VSwitch.
    -   Elastic Network Interface: Click Add ENI to attach an ENI, and then select the VSwitch for the ENI.

        **Note:** 

        You are only allowed to attach a maximum of two ENIs when creating an instance in the console.  One of them is the primary network interface, which is attached automatically, and the other one is a secondary network interface. 

        -   After the instance is started, you can attach more secondary network interfaces to the instance based on the instance type in the console or
        -    by using the [AttachNetworkInterface](../../../../intl.en-US/API Reference/Elastic network interfaces/AttachNetworkInterface .md) API.

If you want to keep the secondary network interface that is created in this way, detach it from the instance before you release the instance.

