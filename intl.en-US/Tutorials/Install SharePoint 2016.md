# Install SharePoint 2016 {#concept_spr_fzt_2fb .task}

This topic describes how to install SharePoint 2016.

You must have an Alibaba Cloud account before you follow the instructions provided in the tutorial. To create an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).

To install SharePoint 2016, you must meet the following environment requirements:

-   Basic configurations:
    -   Windows Server 2012
    -   CPU: 4 vCPUs. Memory: 8 GB. You can design the architecture and purchase ECS instances according to actual environments.
-   Software environment:
    -   SQL Server 2012 Express
    -   SharePoint 2016
    -   Active Directory \(AD\)
    -   Domain Name System \(DNS\)
    -   Internet Information Services \(IIS\)
-   Required component: .NET Framework 3.5 for installing SQL Server.

    **Note:** 

    -   When you install .Net Framework 3.5, an error may occur at the step of **adding roles and features**. For more information about how to fix this issue, see [What can I do if I am unable to install .NET Framework 3.5.1, or a language package, on Windows Server 2012 R2/2016/2019?](https://help.aliyun.com/knowledge_detail/38203.html)
    -   For more information about the required component of SharePoint, see Microsoft documentation. The system indicates that you need to install dependencies when you install SharePoint. If you fail to install dependencies, you cannot install SharePoint.

1.  Build AD. 

    **Note:** Modify the Security Identifier \(SID\) before you add a client to a domain. In this topic, only one ECS instance is used to install SharePoint. Therefore, all roles and features are assigned to the instance. In your actual running environment, do not install SQL, AD, and SharePoint servers on the same instance.

2.  Install SQL Server 2012 Express. Use the default method to install SQL Server. In this topic, the Express edition is used in the test environment. Follow these rules:

    **Note:** 

    -   The Express edition has the TCP/IP protocol disabled by default. You must manually enable the protocol.
    -   The Express edition may have no console. You must install a SQL management tool.
    -   We recommend that you use the SQL Server Enterprise edition that provides more features than the Express edition.
3.  Install SharePoint 2016. 
    1.  Install the required components of SharePoint. 

        **Note:** To use the installation wizard, your instance must be authorized to access the Internet. If your instance is not authorized, you have to download the components and run commands to install these components. For more information, see Microsoft documentation.

    2.  Restart the ECS instance, and install Sharepoint.
    3.  Run the SharePoint 2016 installation wizard, enter the product key, and then click **Continue**. Start to install SharePoint 2016.
    4.  Run the SharePoint configuration wizard. 
    5.  Click **Create a new server farm**, and click **Next**.
    6.  Specify configuration database settings and the database access account. 
    7.  Specify the server role. 
    8.  Specify the port number for the SharePoint Central Administration Web application and configure security settings. 
    9.  Complete the configuration wizard and start to install SharePoint. 
    10. Click **Finish**. 

After you install SharePoint, you can configure the server farm in the SharePoint Central Administration Web application. When you configure the server farm, only enable the required services. Otherwise, unnecessary memory pressure may be incurred.

