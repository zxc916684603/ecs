# Step 2. Create an instance {#task_zjx_p1f_5db .task}

This article describes how to create an ECS instance by using an existing image. If you want to create a custom image from a snapshot of a system disk, and then use the custom image to create an ECS instance, see [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9627.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#) in the User Guide of Elastic Compute Service.

Before you start creating an ECS instance, you must:

-   [Sign up for Alibaba Cloud](https://www.alibabacloud.com/help/zh/doc-detail/50482.htm).

-   [Bind your credit card or PayPal account](https://www.alibabacloud.com/help/zh/doc-detail/50517.htm).

-    [Register by using your real name](https://www.alibabacloud.com/help/zh/doc-detail/52595.htm) if you want to create an ECS instance in a region inside mainland China.

-    [Create a VPC and VSwitch](https://www.alibabacloud.com/help/zh/doc-detail/65430.htm) for creating an ECS instance of the VPC network.

-   If you do not use the default security group that the system automatically creates, you need to [create a security group](https://www.alibabacloud.com/help/zh/doc-detail/25468.htm) in the target area and [add security group rules that meet your business needs](https://www.alibabacloud.com/help/zh/doc-detail/25471.htm). For more information about the default security group, see [Default security group rules](https://www.alibabacloud.com/help/zh/doc-detail/31707.htm).

-    [Create an SSH key pair](https://www.alibabacloud.com/help/zh/doc-detail/51793.htm) for creating a Linux instance authenticated by using key pairs.

-   Write the [User-defined data](https://www.alibabacloud.com/help/zh/doc-detail/49121.htm) for customizing the startup behaviors of an instance or passing in user-defined data.

-   [Create an instance RAM role and grant it permissions](https://www.alibabacloud.com/help/zh/doc-detail/61175.htm) if you want to authorize instance to play a role.


1.   Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
2.   In the left-side navigation pane, click **Instances**. 
3.   On the Instance List page, select **Create Instance** to Create Cloud Disk. 
4.   Follow these steps to finish Basic Configurations: 
    1.   Select a **Billing Method**: **Subscription** or **Pay-As-You-Go**. 
    2.  Select a region and zone. By default, the Free Zone is assigned randomly, and you can select the applicable one. How to select regions and zones that are available, see [regions and zones](https://www.alibabacloud.com/help/doc-detail/40654.htm?spm=a2c63.p38356.a3.13.4c3b587a2IQHFX) that are available. 

        **Note:** 

        -   When the instance is created, you cannot change the region and the available area.
        -   Some instances of spec families are not available throughout the region. For more information, see  [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9632.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create a gn4 or a gn5 instance.md#), [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9634.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an f1 instance.md#), [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9635.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an f2 instance.md#), [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9637.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an SCC server instance.md#) and [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9638.md\#](../../../../intl.en-US/User Guide/Instances/Create an instance/Create an EBM instance.md#).
    3.   Select an Instance Type and specify the quantity of instances. The available instance type families are determined by the selected region.  For the scenarios of each instance type family, see [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9548.md\#](../../../../intl.en-US/Product Introduction/Instance type families.md#). 

        **Note:** 

        -   The quota of Pay-As-You-Go instances for your account is shown on the page.
        -   To use elastic network interfaces, select an enterprise-level instance type with no less than two vCPU cores or an entry-level instance type with no less than four  vCPU cores. The number of flexible network cards supported by a variety of instance specifications, see [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9548.md\#](../../../../intl.en-US/Product Introduction/Instance type families.md#).
        -   To use an SSD Cloud Disk, select an I/O-optimized instance.
    4.   Select an Image. You can select an image from the list of Public Image, Custom Image, Shared Image, or Marketplace Image. 

        **Note:** 

        -   To use an SSH key pair, select a Linux image.
        -   To use user-defined data, select an image according to the list described in the [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9660.md\#](../../../../intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#).
    5.   Select storage: 
        -   **System Disk**: Required. A system disk is required for the image. Specify the cloud type and capacity of the system tray:

            -   Cloud disk category: The available categories are determined by the selected region.
            -   Size: The default size range is \[40, 500\] GB. If the selected image is greater than 40 GB, the default size range is \[ImageSize, 500\] GB.  The available size range varies according to the selected image, as shown in the following table.

                |Image|System disk capacity range|
                |:----|:-------------------------|
                |Linux \(excluding CoreOS\) FreeBSD|\[max\{20, ImageSize\}, 500\] GB In the public image list, only Ubuntu 14.04 32-bit, Ubuntu 16.04 32-bit, and CentOS 6.8 32-bit are of 40 GB size.|
                |CoreOS|\[max\{30, ImageSize\}, 500\] GB|
                |Windows| \[max\{40, ImageSize\}, 500\] GB|

        -   **Data Disk**: Optional. You can decide to add data disks now or after the instance is created. To add a data disk now, specify the category, size, and quantity of data disks, and decide whether it is necessary for [Encryption](../../../../intl.en-US/Product Introduction/Block storage/ECS disk encryption.md#). You can create an empty data disk or create a data disk from a snapshot. Up to 16 data disks can be added.

            **Note:** 

            The clouds created at this time have the following characteristics:

            -   The data disks added here have the same billing method with that of the instance.
            -   A Subscription data disk is released along with the instance, but a Pay-As-You-Go data disk can be set to be released along with the instance.
        -    If you have selected an instance type that has local disks, such as instance type of the i1, d1, or d1ne family, the local storage information is displayed. You cannot specify the quantity or category of local storage, which is determined by the selected instance type.  For more information, see [../../../../dita-oss-bucket/SP\_2/DNA0011858383/EN-US\_TP\_9548.md\#](../../../../intl.en-US/Product Introduction/Instance type families.md#).

5.   Click, **next: network and security groups** to complete the network and security group settings: 
    1.   Select the network type: 
        -   Use the **default VPC \(Virtual Private Cloud\)**, and then select a VPC and a VSwitch. If you do not have a VPC and a VSwitch, you can use the default ones.
        -   **Classic network**: If you purchased the ECS instance for the first time since June 16, 2016, 12:00 \(UTC + 8\), you can no longer select a classic network.
    2.   Set public network bandwidth: 
        -   If you need to assign an instance a public network IP address, you must select **assign a public network IP address**, select **use the flow meter** to charge for network bandwidth, and specify the bandwidth. The public network IP address assigned in this way cannot be unbound from the instance. For more information about network billing, see [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9596.md\#](../../../../intl.en-US/Pricing/Billing of network bandwidth.md#).
        -   To [use elastic public IP \(EIP\) address for Internet access](../../../../intl.en-US/Quick Start/Create a VPC.md#), do not select Assign public IP.  You can unbind an EIP address from an instance.
    3.   Select a security group. You can use the default security group.  For more information, see  [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9716.md\#](../../../../intl.en-US/User Guide/Security groups/Default security group rules.md#). 
    4.   Add an elastic network interface. If your selected instance type supports elastic network interfaces, you can add one and specify a VSwitch for it. 

        **Note:** By default, the elastic network interface is released along with the instance. You can detach it from the instance in the [ECS console](../../../../intl.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#) or by using the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9952.md\#](../../../../intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#) interface.

6.   Optional. Click **Next: System Configurations** to finish the following configuration: 
    -   Select and set Log on Credentials. You can [set the credential after the instance is created](../../../../intl.en-US/User Guide/Instances/Reset an instance password.md#), or you can set it directly. Select a credential based on the image:

        -   Linux systems: You can select a password or an SSH key pair as a credential for a Linux instance.
        -   Windows systems: Only a password for a Windows instance.
    -   Specify the instance name, which is displayed in the ECS console, and the host name, which is displayed inside the guest operating system.

    -   Set advanced options:

        -   Instance RAM role: authorize the instance a RAM character.
        -   Instance user-defined data: customize instance startup behavior or transmit data to instance.
7.   \(Optional\) Click **Next: Grouping**. You can add tags to the instance to simplify future management. 
8.   Confirm order: 
    -   In the **Configurations Selected**area, confirm all the configurations.  You can click ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/25424/cn_zh/1521471446632/Create_Edit.png) to change settings.
    -   Optional. If you are creating a **Pay-As-You-Go** instance, you can select**Auto Release Schedule** and set the release plan.
    -   Optional. If you are creating a **Subscription** instance, you can specify the Purchase cycle and select **Auto-Renew**.
    -   Confirm Instance Cost, which is the sum of the cost of the instance type \(vCPU + RAM\), the system disk, the data disks \(if any\), and the local disks \(if any\). The way you charge for an instance and public network bandwidth determines the cost information that is displayed, as shown in the following table.

        |Instance billing method|Public network bandwidth billing method|Fee estimates|
        |:----------------------|:--------------------------------------|:------------|
        |Pay-As-You-Go or Spot instance|Based on traffic|Public IP traffic fee + configuration fee. Where configuration costs include: instance specification \(CPU and RAM configuration\), the system disk, the data disks \(if any\), and the local disks \(if any\).|
        |Press fixed bandwidth|Configuration fees include: instance type \(CPU and RAM configuration\), system disk, data disks \(if any\), local disks \(if any\) and public network bandwidth charges.|
        |Subscription|Based on fixed bandwidth|Configuration costs, including: instance specification \(CPU and memory configuration\), system disks, data disks \(if any\), local disks \(if any\) and public network bandwidth charges.|
        |Based on traffic|Public IP traffic fee + configuration fee. Configuration fees include: instance type \(CPU and RAM configuration\), the system disk, the data disks \(if any\), and the local disks \(if any\).|

        |Instance billing method|Fee estimates|
        |:----------------------|:------------|
        |Pay-As-You-Go|Public IP traffic fee + configuration fee. Where configuration costs include: instance specification \(CPU and memory configuration\), system disk, data disk \(if any\), and site \(if any\) the cost.|
        |Subscription|Public IP traffic fee + configuration fee. Among them, configuration costs include: instance specification \(CPU and memory configuration\), system disk, data disk \(if any\), and, if any, the cost of this site.|

    -   Confirm  **ECS Service Terms and Product Terms of Service**.
9.   Click **Create Instance**. 

When the instance is activated, you can go to the**ECS console** to view the instance details. In the **instance list** of the corresponding region, you can view the instance details, such as the instance name, the public IP address, and the private IP address.

-   You can create an FTP site on the instance for transferring files. For details on deploying the FTP service, see creating an FTP site using an ECS instance.
-   To secure your instance after creation, we recommend that you perform security compliance inspection and configuration on:
    -   For Linux instances, see [Harden operating system security for Linux](https://www.alibabacloud.com/help/zh/doc-detail/49809.htm) in Security Advisories.
    -   For Windows instances, see [Harden operating system security for Linux](https://www.alibabacloud.com/help/zh/doc-detail/49781.htm) in Security Advisories.
-   If a data disk is created along with the instance, you must partition the disk and format the partitions. For details, please see [EN-US\_TP\_9604.md\#](intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#) or [EN-US\_TP\_9605.md\#](intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Windows _ Format a data disk.md#).

