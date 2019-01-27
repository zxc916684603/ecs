# Connect the Internet to a VMC VM {#task_hzb_wvs_ggb .task}

This topic describes how to connect the Internet to a VMC VM.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on NSX Manager with your admin privileges. 
2.   Select **Routing** \> **Routers** \> **tier1**, and then select **Services** \> **NAT**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863736290_en-US.png)

  
3.   In the New NAT Rule dialog box, set **Action** to DNAT, set **Destination IP** to an unused IP address of Ext ENI \(192.168.50.149 is obtained from the procedure [Assign Multiple IP Addresses to Ext ENI](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Assign Multiple IP Addresses to Ext ENI.md#)\), set **Translated IP** to the IP address of the VMC VM that provides external services \(10.100.100.2 in this example\), and then click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863736291_en-US.png)

  
4.   Select **Routing** \> **Routers** \> **tier1**, and then select **Services** \> **NAT**. 
5.   In the New NAT Rule dialog box, set **Action** to SNAT, set **Source IP** to the IP address of the VMC VM that provides external services, set **Translated IP** to the destination IP address specified in the previous step, and then click **SAVE**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863736292_en-US.png)

  
6.   On the Routers tab page, select **tier1** \> **Configuration** \> **Logical Router Ports**, and then obtain the IP address of the tier-1 router uplink.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863736296_en-US.png)

  
7.   On the **Routers** tab page, click **tier0**, and then select **Services** \> **Static Routes**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863736293_en-US.png)

  
8.   Click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836295_en-US.png)

  
9.   In the Add Static Route dialog box, set **Network** to the destination IP address specified in step 3, set **Next Hop** to the IP address obtained in step 6, and then click **SAVE**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836297_en-US.png)

  
10. Log on to the ECS console. 
11. In the left-side navigation pane, select **Virtual Private Cloud** \> **NAT Gateways**. 
12.  Click **NAT Bandwidth Package**, and then click **Add IP Address**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836298_en-US.png)

  
13. In the **Configuration Upgrade** area, set the **number of public IP address** to 2, and set the **bandwidth** as needed. 
14.  Find the created VPC, and then click **Configure DNAT**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836301_en-US.png)

 
15.  On the DNAT Table page, click **Create DNAT Entry**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836302_en-US.png)

 
16.  Select the newly applied IP address from the **Public IP** drop-down list, set the **Private IP Address** to the destination IP address specified in step 3, and then click **OK**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836303_en-US.png)

 
17.  Run the ping <VMC VM IP\> command to verify that the Internet can access the VMC VM.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83732/154857863836304_en-US.png)

 

