# Build a WordPress website {#concept_43244_zh .concept}

WordPress is a blog platform developed with the PHP language. On servers that support PHP and MySQL databases, you can use WordPress to set up your own website, or use it as a Content Management System \(CMS\). Domain names, spaces, and programs need to be prepared before a website is built. Using WordPress images to create ECS instances, you do not need to deploy the Web environment, eliminating the need to consider spaces or programs. As long as the domain name is registered and ICP filing is completed, the website can be directly launched. In other words, you can buy an instance and use it to build websites right away.

This article describes how to create an instance and launch a website by using the [free WordPress Pure theme image](https://market.aliyun.com/products/52738005/cmjj027560.html) or [commercial WordPress images](https://market.aliyun.com/products/53616009/cmjj028448.html) from the Alibaba Cloud Marketplace.

## Intended audience {#section_ex5_zh2_2fb .section}

Enterprises or individuals who are using ECS for the first time.

## Procedure {#section_stw_132_2fb .section}

To create websites on ECS instances by using the [free WordPress Pure theme image](https://market.aliyun.com/products/52738005/cmjj027560.html) or [commercial WordPress images](https://market.aliyun.com/products/53616009/cmjj028448.html), follow these steps:

Step 1: Buy a WordPress image

Step 2: Install the theme template for the enterprise website

Step 3: Modify the theme elements

Step 4: Buy a domain name

Step 5: Complete ICP Filing

Step 6: Resolve the domain name

**Step 1. Buy a WordPress image**

Assume that you use the Alibaba Cloud ECS service for the first time. You can follow the steps below to create an ECS instance by using the [free WordPress Pure theme image](https://market.aliyun.com/products/52738005/cmjj027560.html) or [commercial WordPress images](https://market.aliyun.com/products/53616009/cmjj028448.html).

1.  Log on to [Alibaba Cloud](https://account.aliyun.com/login/login.htm). If you do not have an Alibaba Cloud account, click [Join Free](https://account.aliyun.com/register/register.htm) to sign up.
2.  Go to the Marketplace and find the [free WordPress Pure theme image](https://market.aliyun.com/products/52738005/cmjj027560.html) or [commercial WordPress images](https://market.aliyun.com/products/53616009/cmjj028448.html). Then click **Choose Your Plan**.
3.  On the ECS Custom page, complete the following **Basic Configurations**:
    1.  Select a **Billing Method**: If you need ICP filing for a website, you must select **Subscription**, and set the **Duration** at the bottom to no less than 3 months. If you do not need ICP filing, you can choose the billing method according to your needs.
    2.  Select a **Region**: Currently, the image is supported in North China 1, North China 2, North China 3, North China 5, East China 1, East China 2, and South China 1. Please select the appropriate region based on the distribution of the website users and your own geographic location. For more information about regions and zones, see [regions and zones](../../../../reseller.en-US/General Reference/Regions and zones.md#).

        **Note:** 

        -   After an instance has been created successfully, you cannot change the region and the zone.
        -   The number of zones, the available instance type families, the available storage types, and the instance prices may differ between regions. Select a region based on your business needs.
    3.  Select an **Instance Type**: Select an instance type \(vCPU, memory\) based on the expected visits to your website. For common corporate websites, the general or entry-level instance types with 1 vCPU + 2 GiB memory or 2 vCPU + 4 GiB memory can meet the requirements. For more information about instance type families, see [instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#).
    4.  Select an **Image**: The **free WordPress 4.9.4 Pure theme image** or **commercial PHP-WordPress1.0.8 image** is already selected from the **Marketplace**. You can also select a different WordPress image from the Marketplace by clicking **Reselect image**.
    5.  Select **Storage**:
        -   **System Disk**: required You can select the type and capacity of cloud disks. In this example, select **Ultra Cloud Disk** for the system disk, with the size of 46 GiB \(the image size\).
        -   **Data Disk**: optional. We recommend that you create a 50 GiB Ultra Cloud Disk as a data disk that is not encrypted.
4.  Click **Next: Networking** to configure the **Network and Security Group**:
    1.  Select a **Network**: Select **VPC**. If you do not create a VPC and VSwitch, select the **Default VPC** and **Default VSwitch**.

        **Note:** If you have already created a Classic Network ECS instance, and the selected instance type also supports the Classic Network, you can select **Classic Network**.

    2.  Set the **Network Billing Method**: Because the instance needs to access the Internet, you need to choose **Assign public IP**. Then, select **Pay-By-Fixed-Bandwidth** or **Pay-By-Traffic** and set the bandwidth according to the expected outbound traffic. It is recommended to select **Pay-By-Fixed-Bandwidth**, with the bandwidth no less than 2 Mbps.
    3.  Select a **Security Group**: If no security group has been created in the current region, you can use the default security group and select **HTTP port 80**.

        **Note:** If you have already created a security group, you must add rules to the security group and allow inbound access to HTTP port 80. For more information, see [add security group rules](../../../../reseller.en-US/User Guide/Security groups/Add security group rules.md#).

5.  Click **Next: System Configurations** to finish the following configurations:
    1.  Set **Log on Credentials**: It is recommended to set the logon password for the instance here. Be sure to keep in mind your logon username and password.
    2.  Set the **Instance Name**, **Description**, and **Host** to facilitate subsequent management.
6.  Skip **Next: Grouping**, and then click **Create Order**:
    -   Confirm the **Configurations Selected**. If you need to modify the configuration, click the ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/44543/cn_zh/1527648165582/edit_icon.png) icon and reselect the configuration.
    -   Confirm the duration \(such as 3 months in this case\) and decide whether to enable **Auto-Renew**.
7.  Read and confirm the ECS Service Level Agreement and Product Terms of Service | Image Product Terms of Use.
8.  Click **Create order**.
9.  Confirm the order and make payment.

After the instance is activated, click **Console** to view it there. In the **Instance List** of the relevant region, you can view the information of the new instance, including the instance name, the Internet IP address, and the private IP address.

**Step 2. Install the theme template for the enterprise website**

To better promote your company on your website, you need to install the appropriate theme template. This part focuses on how to install the WordPress theme template.

1.  [Connect to a Windows instance](../../../../reseller.en-US/User Guide/Connect to instances/Connect to a Windows instance.md#).
2.  Open the IE browser and enter `http://public IP address of the instance/wp-admin` to go to the WordPress logon page.
3.  Enter the username **admin** and the initial password **admin123**, and then click **Log on**.
4.  In the left-side navigation pane of the Dashboard page, select **Appearance** \> **Theme**.
5.  Select the theme that has been installed on the **Themes** page.

    **Note:** After you log on, it is recommended that you modify the password in **Account Management** of **Edit My Profile**.


**Step 3. Modify theme elements**

After installing the theme, you can modify the theme elements to create your own unique website. For more information, see the [Help Center](http://help2.facecloud.net/wordpress) of the image supplier Facecloud.

**Step 4. Buy a domain name**

To facilitate visits to your website, you can choose an easy-to-remember domain name. You can complete the operation by referring to [domain name purchase process](../../../../reseller.en-US/Quick Start/Buy a domain name.md#).

**Step 5. ICP Filing**

If you are filing for the domain name for the first time, you can find the detailed procedure by referring to [first-time ICP Filing guide](../../../../reseller.en-US/ICP Filing Procedures/ICP Filing for the first time.md#). Otherwise, see [ICP Filing Guide](../../../../reseller.en-US/ICP Filing Procedures/Overview.md#).

**Step 6. Resolve the domain name**

Domain name resolution is an integral part of using the domain name to access your website.

## Expand business capacity {#section_glk_sxz_gfb .section}

As your business grows, you can leverage the power of Alibaba Cloud to scale up your business capacity, for example:

-   Scale up the vCPU and memory of a single ECS instance to enhance its processing capabilities. For more information, see [overview of configuration changes](../../../../reseller.en-US/User Guide/Instances/Change configurations/Overview of configuration changes.md#).
-   Add multiple ECS instances and implement load balancing among them. For more information, see [create an instance of the same configuration](../../../../reseller.en-US/User Guide/Instances/Create an instance/Create an instance of the same configuration.md#) and [what is Server Load Balancer](../../../../reseller.en-US/Product Introduction/What is Server Load Balancer?.md#).
-   Use Auto Scaling to automatically increase or decrease the number of ECS instances based on the volume of business. For more information, see [what is Auto Scaling](https://www.alibabacloud.com/help/faq-detail/25857.htm).
-   Use Object Storage Service \(OSS\) to store a massive amount of data such as web pages, images, and videos. For more information, see [what is OSS](../../../../reseller.en-US/Product Introduction/What is OSS?.md#).

