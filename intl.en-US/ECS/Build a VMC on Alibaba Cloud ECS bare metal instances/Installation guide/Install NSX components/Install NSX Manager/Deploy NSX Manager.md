# Deploy NSX Manager {#task_lyc_hzy_ngb .task}

This topic describes how to deploy NSX Manager by importing an Open Virtualization Format \(OVF\) template. NSX Manager is a powerful and centralized network management component that provides an aggregated system view. It can be installed as a virtual appliance on your ESXi hosts in the vCenter Server environment.

1.  You have logged on to the Windows instance where VMware vCenter Server is installed.
2.  You have logged on to VMware vSphere Web Client.
3.  You have downloaded and purchased the OVA file to install NSX Manager. For more information, see [Download vCenter and NSX components](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Download components.md#).

1.  Right-click the IP address of the host that provides network management utilities, and then click **Deploy OVF Template...**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812135683_en-US.png)

2.  On the Select template page, click **Browse** and select the .ova file, and then click **Next**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85022/154891812135839_en-US.png)

3.  Enter an NSX Manager name, select a folder or vCenter Server datacenter, and then click **Next**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812135687_en-US.png)

4.  On the **Browse** tab page, select the host on which you want to deploy the NSX Manager appliance, and then click **Next**. 

    **Note:** We recommend that you deploy NSX Manager in a host or cluster with network management utilities.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812135688_en-US.png)

5.  On the **Review details** page, confirm the template details, and then click **Next**. 
6.  Select a configuration size: Small, Medium, or Large. The system requirements vary depending on the configuration size. Here, we take Medium as an example. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812135692_en-US.png)

7.  Select a datastore to store the NSX Manager virtual appliance files, and then click **Next**. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93420/154891812136881_en-US.png) 
8.  Select the port groups or networks on which you want to deploy the NSX Manager interface, and then click **Next**. 

    **Note:** You can change the networks after NSX Manager is deployed. In this example, the destination network is temporarily set to **VM Network**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812136589_en-US.png)

9.  On the Customize template page, set the password of the CLI admin User by following the rules highlighted in the following figure. 

    **Note:** The core services on the appliance do not start until a password that meets the complexity rules is set.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812235881_en-US.png)

10. On the Customize template page, set the password of the System Root User by following the password complexity rules. 

    **Note:** The core services on the appliance do not start until a password that meets the complexity rules is set.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812236591_en-US.png)

11. Run the `ipconfig/all` command in the Windows command console, find the DNS IP addresses, the default IPv4 gateway IP address, and the management network netmask IP address, and then enter these settings in the corresponding fields. 

    **Note:** NSX Manager is in the same network as the Windows instance on which vCenter is installed.

12.  Set the **Hostname** to nsx-manager. Select an unused secondary management ENI attached to the host with network management utilities, find its IP address on the Network Interfaces page of the ECS console, and set the **Management Network IPv4 Address**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812235877_en-US.png)

  
13.  In the **Services Configuration** area of the Customize template page, select **Allow root SSH logins** and **Enable SSH**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812235879_en-US.png)

  

    If you enable SSH, make sure that you can open an SSH session to your NSX Manager. Specifically, make sure:

    -   You can ping your NSX Manager.
    -   NSX Manager can ping its default gateway.
    -   NSX Manager can ping the hypervisor hosts that are in the same network as NSX Manager.
    -   NSX Manager can ping its DNS server and NTP server.
14. On the **Ready to complete** page, confirm the configuration data, and then click **Finish**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812235750_en-US.png)

15.  Verify that the NSX Manager deployment process is completed in the **Recent Tasks** list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154891812236617_en-US.png)

 

