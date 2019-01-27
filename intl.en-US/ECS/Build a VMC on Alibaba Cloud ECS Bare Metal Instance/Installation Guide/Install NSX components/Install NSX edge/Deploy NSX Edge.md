# Deploy NSX Edge {#task_lkm_3z1_hgb .task}

This topic describes how to deploy NSX Edge by using the OVF template.

1.  Log on to the Windows instance where VMware vCenter Server is installed.
2.  Log on to VMware vSphere Web Client.
3.  Download and purchase the OVA file to install NSX Edge. For more information. see [Download vCenter and NSX components](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Download components.md#)

1.   Right-click the IP address of the host that provides network management utilities, and then click **Deploy OVF Template**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773235901_en-US.png)

 
2.  On the Select template page, click **Browse** to navigate to the .ova file, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773235905_en-US.png) 
3.   Enter a name for NSX Edge, and select a folder or vCenter Server datacenter, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773235906_en-US.png)

 
4.  On the **Browse** tab page of the Select a resource page, select the host on which you want to deploy the NSX Edge appliance, and then click **Next**. 

    **说明：** We recommend that you deploy NSX Edge in a host or cluster that provides network management utilities.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773235907_en-US.png)

5.   On the Review details page, confirm the template details, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335908_en-US.png)

 
6.  Select a configuration size: small, medium, or large. In this example, **Medium** is selected. 

    **说明：** The system requirements vary with the configuration size.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335910_en-US.png)

7.   Select a datastore to store the NSX Edge virtual appliance files, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335911_en-US.png)

 
8.  Select the port groups or networks on which you want to deploy the NSX Edge interface, and then click **Next**. 

    **说明：** You can change the networks after NSX Edge is deployed. In this example, the destination networks are temporarily set to **VM Network**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335912_en-US.png)

9.  On the Customize template page, set the password of the CLI admin User according to the rules highlighted in the following figure. 

    **说明：** The core services on the appliance do not start until a password that meets the complexity rules is set.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83722/154857773335536_en-US.png)

10. On the Customize template page, set a password for the System Root User according to the password complexity rules. 

    **说明：** The core services on the appliance do not start until a password that meets the complexity rules is set.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83722/154857773335537_en-US.png)

11. Run the `ipconfig/all` command in the Windows command console, find the DNS IP addresses, the default IPv4 gateway IP address, and the management network netmask IP address, and then enter these settings in the corresponding fields. 

    **说明：** NSX Edge is in the same network as the Windows instance on which the vCenter is installed.

12.  Set the **Hostname** to nsx-edge. Select an unused secondary management ENI attached to the host that provides network management utilities, find its IP address on the Network Interfaces page of the ECS console, and set the **Management Network IPv4 Address**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335915_en-US.png)

  
13.  In the **Services Configuration** area of the Customize template page, select **Allow root SSH logins** and **Enable SSH**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335916_en-US.png)

  

    If you enabled SSH, make sure that you can open an SSH session to your NSX Edge. Specifically, make sure:

    -   You can ping your NSX Edge.
    -   NSX Edge can ping its default gateway.
    -   NSX Edge can ping the hypervisor hosts that are in the same network as NSX Edge.
    -   NSX Edge can ping its DNS server and NTP server.
14.  On the Ready to complete page, confirm the configuration data, and then click **Finish**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335917_en-US.png)

  
15.  Verify that the NSX Edge deployment process is completed in the **Recent Tasks** list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85017/154857773335926_en-US.png)

 

