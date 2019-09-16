# Build Microsoft SharePoint 2016 on an ECS instance {#concept_pmz_5gt_2fb .task}

This topic describes how to build Microsoft SharePoint 2016 on an ECS instance.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

Microsoft SharePoint Portal Server \(Microsoft SharePoint\) is a portal development environment that allows enterprises to develop intelligent portals. Microsoft SharePoint can be seamlessly integrated with knowledge bases and individual users and teams can easily connect to the environment. Microsoft SharePoint empowers your business by means of efficient information processing. Microsoft SharePoint provides an enterprise-wide service solution. Based on the feature of integrating enterprise applications, you can flexibly choose deployment options and management tools to integrate information from various systems into this solution.

The procedure described in this topic is applicable to users that are familiar with ECS instances and Windows Server operating systems.

The following software versions are used:

-   Operating system: Windows Server 2012 R2 DataCenter
-   Database: SQL Server 2014 SP1

The ECS instances described in this topic use the following configurations:

-   CPU: 4 vCPUs
-   Memory: 8 GB

## Procedure {#section_bi1_x2j_v96 .section}

To build Microsoft SharePoint 2016 on an ECS instance, follow these steps:

1.  [Step 1: Add the AD, DHCP, DNS, and IIS services](#section_o8w_kwm_aao)
2.  [Step 2: Install SQL Server 2014](#section_o9w_kwm_bho)
3.  [Step 3: Install SharePoint 2016](#section_o1w_kwm_xxo)
4.  [Step 4: Configure SharePoint 2016](#section_o2w_kwm_cco)

## Step 1: Add the AD, DHCP, DNS, and IIS services {#section_o8w_kwm_aao .section}

To add the Active Directory \(AD\), Dynamic Host Configuration Protocol \(DHCP\), Domain Name System \(DNS\), and Internet Information Services \(IIS\) services, follow these steps:

1.  Purchase an ECS instance. For more information, see [Create an instance by using the wizard](../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).
2.  Disable Internet Explorer Enhanced Security Configuration. 

    ![Disable Internet Explorer Enhanced Security Configuration](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657512311_en-US.png)

3.  Add roles and features of DNS, DHCP, IIS, and .NET Framework3.5. 
    1.  Click **Add roles and features**. 

        ![Add roles and features](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657512312_en-US.png)

    2.  Add the AD, DHCP, and DNS services. Select **Active Directory Domain Services**, **DHCP Server**, and **DNS Server**, and click **Next**. 

        ![Add the AD, DHCP, and DNS services](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612313_en-US.png)

    3.  Add the IIS service. Select **Web Server IIS**, and click **Next**. 

        ![Add the IIS service](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612314_en-US.png)

    4.  In the **Features** section, select **.NET Framework 3.5 Features**. 

        ![Add .NET Framework 3.5 features](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612316_en-US.png)

    5.  Click **Next** until the end of installation.
4.  Configure the AD service. Click **Add a new forest**, and enter a domain name in the **Root domain name** field to create a domain environment. 

    ![Configure the AD domain name](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612317_en-US.png)

5.  Set the password, and click **Next** until the end of the configuration. 

    ![Set the password](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612318_en-US.png)

6.  Click **Complete DHCP configuration** to set the DHCP feature. 

    ![Configure DHCP](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612321_en-US.png)

    1.  Check the DHCP configuration description, and click **Next**.
    2.  Keep the default configuration, and click **Commit** to complete the installation. 

        ![Keep the default configuration](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657612322_en-US.png)


## Step 2: Install SQL Server 2014 {#section_o9w_kwm_bho .section}

To install the SQL Server 2014 database, follow these steps:

1.  Install SQL Server 2014 SP1, go to the SQL Server Installation Center window, and click the first installation option. 

    ![Click the first installation option](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712323_en-US.png)

2.  Enter the product key, and click **Next**.
3.  Accept the license terms, and click **Next**.
4.  Complete the installation check, and click **Next**.
5.  Keep the default option, and click **Next**. 

    ![Keep the default option](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712324_en-US.png)

6.  Click **Select All** to select all features, and click **Next**. 

    ![Select all features](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712325_en-US.png)

7.  Configure the SQL Server instance: Click **Default instance** to use the default instance ID. 

    ![Configure the SQL Server instance](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712326_en-US.png)

8.  Specify the account names and passwords for **SQL Server Database Engine** and **SQL Server Analysis Services**. 

    ![Specify the account names and passwords](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712328_en-US.png)

9.  Click **Add Current User** to add the current user, and click **Next**. 

    ![Add the current user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657712329_en-US.png)

10. Click **Add Current User** to add the current user again, and click **Next**. 

    ![Continue to add the current user](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657812330_en-US.png)

11. Click **Next** until the end of the installation.

## Step 3: Install SharePoint 2016 {#section_o1w_kwm_xxo .section}

To install SharePoint 2016, follow these steps:

1.  Install the SharePoint 2016 prerequisite installer: Open the image folder, and double-click the executable file of the prerequisite installer. 

    ![Open the prerequisite installer](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9787/156862657812331_en-US.png)

2.  In the installation wizard, click **Next**. 
3.  Accept the license terms, and install necessary components.
4.  Open the Setup.exe file, enter the product key in the dialog box that appears, accept the license terms, and then click **Continue**. 
5.  Specify the installation directory, or keep the default setting as shown in this example, and then click **Install Now**. 
6.  At the end of the installation, select **Run the SharePoint Products Configuration Wizard now** and close the wizard.

## Step 4: Configure SharePoint 2016 {#section_o2w_kwm_cco .section}

To configure SharePoint 2016, follow these steps:

1.  Select **Create a new server farm**. 
2.  Specify configuration database settings and the database access account. The database is installed on the local host. Therefore, you must specify the local IP address as the database server. 
3.  Specify the server role. 
4.  Select **Specify port number**, and enter 10000 in the field. You can also specify another port number as needed. 
5.  Check the configurations and click **Next**. Now, you can open the SharePoint Central Administration Web application.

