# Step 2. Create an instance {#task_zjx_p1f_5db .task}

This article describes how to create an ECS instance by using an existing image. If you want to create a custom image from a snapshot of a system disk, and then use the custom image to create an ECS instance, see [Create an instance by using a custom image](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom Image.md#).

Before you start creating an ECS instance, you must:

-   [Sign up for Alibaba Cloud](https://www.alibabacloud.com/help/doc-detail/50482.htm).

-   [Bind your credit card or PayPal account](https://www.alibabacloud.com/help/doc-detail/50517.htm).

-    [Register by using your real name](https://www.alibabacloud.com/help/doc-detail/52595.htm) if you want to create an ECS instance in a region inside mainland China.

-    [Create a VPC and VSwitch](https://www.alibabacloud.com/help/doc-detail/65430.htm) for creating an ECS instance of the VPC network. If you do not have a VPC and VSwitch, use the default one. For more information about the default VPC and VSwitch, see [Create the default VPC and VSwitch](https://www.alibabacloud.com/help/doc-detail/65402.htm).

-   [Create a security group](https://www.alibabacloud.com/help/doc-detail/25468.htm) and [add security rules](https://www.alibabacloud.com/help/doc-detail/25471.htm). If you do not have a security group, use the default one. For more information about the default security group, see [Default security group rules](https://www.alibabacloud.com/help/doc-detail/31707.htm).
-   [Create an SSH key pair](https://www.alibabacloud.com/help/doc-detail/51793.htm) for creating a Linux instance authenticated by using key pairs.
-   [Write the user-defined data](https://www.alibabacloud.com/help/doc-detail/49121.htm) for customizing the startup behaviors of an instance or passing in user-defined data.
-   [Create an instance RAM role and grant it permissions](https://www.alibabacloud.com/help/doc-detail/61175.htm) if you want to authorize instance to play a role.

1.   Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
2.   In the left-side navigation pane, click **Instances**. 
3.  On the Instance List page, select **Create Instance**. 
4.   Follow these steps to finish Basic Configurations: 
    1.  Select a **Billing Method**: **Subscription** or **Pay-As-You-Go**. For more information about the billing methods, see [Billing method comparison](../../../../intl.en-US/Pricing/Billing method comparison.md#). 
    2.  Select a region and a zone. For more information about regions and zones, see [Regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm). 

        **Note:** 

        -   After an instance is created, you cannot change its region and zone.
        -   Some instance type families are not supported in all regions. For more information, see [Create a gn4/gn5 instance](../../../../intl.en-US/User Guide/Instances/Create an instance/Create a gn4 or a gn5 instance.md#), [Create an f1 instance](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an f1 instance.md#), and [Create an f2 instance](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an f2 instance.md#).
    3.  Select an **Instance Type** and specify the quantity of instances. The available instance type families are determined by the selected region. For the scenarios of each instance type family, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#). 

        **Note:** 

        -   The quota of Pay-As-You-Go instances for your account is shown on the page.
        -   To use elastic network interfaces, select an enterprise-level instance type with no less than two vCPU cores or an entry-level instance type with no less than four vCPU cores. For more information about the number of elastic network interfaces supported by instance types, see [Elastic network interfaces](../../../../intl.en-US/Product Introduction/Network and security/Elastic network interfaces.md#).
        -   To use an SSD Cloud Disk, select an I/O-optimized instance.
    4.  Select an **Image**. You can select an image from the list of **Public Image**, **Custom Image**, **Shared Image**, or **Marketplace Image**. 

        **Note:** 

        -   To use an SSH key pair, select a Linux image.
        -   To use user-defined data, select an image according to the list described in the [User-defined data](../../../../intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#).
    5.  Select **Storage**: 
        -   **System Disk**: Required. A system disk is required for the image. Specify the cloud disk category and size for the system disk:

            -   Cloud disk category: The available categories are determined by the selected region.
            -   Size: The default size range is \[40, 500\] GiB. If the selected image is greater than 40 GiB, the default size range is \[ImageSize, 500\] GiB. The available size range varies according to the selected image, as shown in the following table.

                |Image|Available size range|
                |:----|:-------------------|
                |                 -   Linux \(excluding CoreOS\)
                -   FreeBSD
 |\[max\{20, ImageSize\}, 500\] GiB**Note:** In the public image list, only Ubuntu 14.04 32-bit, Ubuntu 16.04 32-bit, and CentOS 6.8 32-bit are of 40 GiB size.

|
                |CoreOS|\[max\{30, ImageSize\}, 500\] GiB|
                |Windows| \[max\{40, ImageSize\}, 500\] GiB|

        -   **Data Disk**: Optional. You can decide to add data disks now or after the instance is created. To add a data disk now, specify the category, size, and quantity of data disks. You can create an empty data disk or create a data disk from a snapshot. Up to 16 data disks can be added.

            **Note:** The data disks added here have the same billing method with that of the instance. A Subscription data disk is released along with the instance, but a Pay-As-You-Go data disk can be set to be released along with the instance.

        -   Local storage: If you have selected an instance type that has local disks, such as instance type of the i1, d1, or d1ne family, the local storage information is displayed. You cannot specify the quantity or category of local storage, which is determined by the selected instance type. For more information, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#).

5.  Click **Next: Networking** to finish the networking and security group configuration: 
    1.  Select a **Network**: Use the default VPC \(Virtual Private Cloud\), and then select a VPC and a VSwitch. If you do not have a VPC and a VSwitch, you can use the default ones. 

        **Note:** To improve the user experience on network, Alibaba Cloud initiated the default VPC strategy that VPC is set as the default network type since 12:00 June 16, 2016 \(UTC+8\). If the switch has not started in your region, you can still create ECS instances of the Classic network. Otherwise, the VPC is the only one option.

    2.  Configure **Network Billing Method**: 
        -   To assign a public IP address to the instance, select **Assign public IP** and specify a non-zero value as the bandwidth. **PayByTraffic** is the only one option for the network billing method. You cannot unbind the assigned public IP address from the instance. For more information about network billing, see [Billing of network bandwidth](../../../../intl.en-US/Pricing/Billing of network bandwidth.md#).
        -   To use elastic public IP \(EIP\) address for Internet access, do not select **Assign public IP**. You can unbind an EIP address from an instance.
    3.  Select a security group. You can use the default security group. For more information, see [Default security group rules](../../../../intl.en-US/User Guide/Security groups/Default security group rules.md#). 
    4.  Add an elastic network interface. If your selected instance type supports elastic network interfaces, you can add one and specify a VSwitch for it. By default, the elastic network interface is released along with the instance. You can detach it from the instance [in the ECS console](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#) or by using the [DetachNetworkInterface](../../../../intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#) interface. 
6.   \(Optional.\) Click **Next: System Configurations** to finish the following configuration: 
    -   Select and set **Log on Credentials**. You can select a password or an SSH key pair as a credential for a Linux instance, but only a password for a Windows instance. You can set the credential after the instance is created.

    -   Specify the instance name, which is displayed in the ECS console, and the host name, which is displayed inside the guest operating system.

    -   Set **Advanced** configurations, such as instance RAM role and user-defined data.

7.  \(Optional.\) Click **Next: Grouping**. You can add tags to the instance to simplify future management. 
8.  Click **Next: Preview** to confirm the order: 
    -   In the **Configurations Selected** area, confirm all the configurations. You can click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9601/2140_en-US.png) to change settings.
    -   \(Optional.\) If you are creating a Pay-As-You-Go instance, you can select **Auto Release Schedule** and set the release plan.
    -   \(Optional.\) If you are creating a Subscription instance, you can specify the **Purchase cycle** and select **Auto-Renew**.
    -   Confirm **Instance Cost**, which is the sum of the cost of the instance type \(vCPU + RAM\), the system disk, the data disks \(if any\), and the local disks \(if any\). If a public IP address is assigned, **Public traffic fee** is displayed.
    -   Confirm **ECS Service Terms** and **Product Terms of Service**.
9.  Click **Create Order** and activate the instance by following the prompts.. 

When the instance is activated, you can go to the ECS console to view the instance details, such as the instance name, the public IP address, and the private IP address.

-   You can create an FTP site on the instance for transferring files. For more information, see [Build an FTP site on an ECS instance](https://www.alibabacloud.com/help/doc-detail/51998.htm?spm=a2c63.p38356.a3.31.4c3b587aegIuna).
-   If a data disk is created along with the instance, you must partition the disk and format the partitions. If the instance is based on a Linux OS, see [Format and mount a data disk](intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#). If the instance is based on a Windows OS, see [Format a data disk](intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Windows _ Format a data disk.md#). If you [create a data disk separately](../../../../intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#), you must [attach the disk](../../../../intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#), and then partition and format the disk.

-   To secure your instance after creation, we recommend that you perform security compliance inspection and configuration on:
    -   Linux instances, see [Harden operating system security for Linux](https://www.alibabacloud.com/help/doc-detail/49809.htm) in Security Advisories.
    -   Windows instances, see [Harden operating system security for Windows](https://www.alibabacloud.com/help/doc-detail/49781.htm) in Security Advisories.

