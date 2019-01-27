# Connect a VMC VM to the Internet {#task_zv1_lft_jgb .task}

This topic describes how to connect a VMC Virtual Machine \(VM\) to the Internet.

-   Verify that you have created a VMC VM.

1.  Log on to the ECS console. 
2.   In the left-side navigation pane, select **Virtual Private Cloud** \> **NAT Gateways**, and then click **Create NAT Gateway**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936228_en-US.png)

 
3.  Select a **Region** and the target **VPC ID**, and then click **Buy Now**. 
4.   Find the NAT gateway created in the previous step, and then click **Purchase NAT Bandwidth Package**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936231_en-US.png)

 
5.   In the left-side navigation pane, select **NAT Bandwidth Package**, and then click **Purchase**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936232_en-US.png)

 
6.  Set the **number of public IP address** and **bandwidth** as needed, and then click **Buy Now**. The purchased NAT bandwidth package is displayed, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936234_en-US.png)

7.   Log on to NSX Manager. In the left-side navigation pane, click **Routing**, and then click the **Routers** tab. Select **tier1**, and then select NAT from the **Services** drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936235_en-US.png)

  
8.   On the **Services** tab, click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936236_en-US.png)

  
9.   On the New NAT Rule page, set the NAT rule as follows:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936237_en-US.png)

 
    1.  Specify a priority value. A lower value indicates that the rule takes a higher priority.
    2.  From the **Action** drop-down list, select SNAT to enable the source NAT, or NO\_SNAT to disable the source NAT.
    3.  Select the protocol type. By default, Any Protocol is selected.
    4.  \(Optional\) In the **Source IP** field, specify an IP address or an IP address range in CIDR format, for example, the IP address range specified for the DHCP server.

        **Note:** If you leave this field blank, all sources on the downlink ports of the router are translated.

    5.  \(Optional\) In the **Destination IP** field, specify an IP address or an IP address range in CIDR format.

        **Note:** If you leave this field blank, the NAT applies to all destinations outside of the local subnet.

    6.  If you select SNAT from the **Action** drop-down list, specify an IP address or an IP address range in CIDR format in the **Translated IP** field.

        **Note:** In this example, the translated IP address is set to an unused IP address of Ext ENI \(192.168.50.150is obtained from the procedure [Assign Multiple IP Addresses to Ext ENI](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Assign Multiple IP Addresses to Ext ENI.md#)\).

    7.  \(Optional\) From the **Applied To** drop-down list, select a router port.
    8.  \(Optional\) Set the status of the rule. The rule is enabled by default.
    9.  \(Optional\) Change the logging status. Logging is disabled by default.
    10. \(Optional\) Change the firewall bypass setting. The setting is enabled by default.
10.  On the **tier1** page, click **Routing** \> **Route Advertisement**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936238_en-US.png)

  
11.  On the **Route Advertisement** page, click **EDIT**, and then change the value of **Advertise ALL NSX Connected Routers**, **Advertise ALL NAT Routers**, and **Advertise ALL Static Routers** from No to Yes.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857856936240_en-US.png)

  
12.  Select **tier0**, select **Routing** \> **Static Routers**, and then click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036241_en-US.png)

  
13. In the Add Static Route dialog box, set **Network** to 0.0.0.0/0, set **Next Hop** to the IP address of the Ext subnet gateway, and then click **ADD**. 

    **Note:** Creating a static route to network 0.0.0.0/0 allows you to set a gateway of last resort on a router.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036242_en-US.png)

14.  On the **tier1** page, select **Configuration** \> **Logical Router Ports**, and then obtain the IP address of the tier-1 router uplink \(100.64.32.1 in this example\). ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036243_en-US.png)

  
15. Select **Routers** \> **tier0** \> **Routing** \> **Static Routes** \> **ADD**. 
16.  Set **Network** to the translated IP address specified for the SNAT rule, set **Next Hop** to the IP address obtained from the previous step \(100.64.32.1\), and then click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036244_en-US.png)

  
17. Log on to the ECS console. 
18.  In the left-side navigation pane, select **Virtual Private Cloud** \> **NAT Gateways**. Find the created VPC, and then click **Configure SNAT**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036245_en-US.png)

  
19.  Click **SNAT Table**, and then click **Create SNAT Entry**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036246_en-US.png)

  
20.  Select the previously created external VSwitch from the drop-down list. Select the public IP address assigned when you purchased the NAT Bandwidth Package.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036247_en-US.png)

  The added **SNAT Entry** is displayed on the SNAP Table page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036248_en-US.png)

21.  Log on to the VMC VM as the root user, and then run the ping www.baidu.com command to verify that the VMC VM is connected to the Internet.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83731/154857857036249_en-US.png)

  

