# Add a downlink port on a tier-1 logical router {#task_bfs_n5t_lgb .task}

This topic describes how to add a downlink port that connects to the overlay N-VDS logical switch. A downlink port created on a tier-1 logical router can serve as a default gateway for the virtual machines in the same subnet.

You have configured a tier-1 logical router.

1.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **Routing** \> **Routers**, and then click **Add** \> **Tier-1 Router**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154886435336106_en-US.png)

 
3.  Click the **Configuration** tab, and then select **Router Ports**. 
4.  Click **Add**. 
5.  Enter a name for the router port. 
6.  \(Optional\) Enter a description. 
7.  From the **Type** drop-down list, select Downlink. 
8.  Select Strict for the **URPF Mode**. 

    **Note:** Unicast Reverse Path Forwarding \(URPF\) is a security feature.

9.   Select the overlay N-VDS logical switch from the drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886435336131_en-US.png)

 
10. Select **Attach to new switch port** to attach the downlink router port to a new switch port, or select **Attach to existing switch port** to attach the downlink router port to an existing switch port. 
11. Enter the router port IP address in **IP Address/mask** \(CIDR notation\). 

    **Note:** This downlink port serves as the default gateway for the virtual machines in the same subnet. Therefore, this IP address is the same as the gateway address that you set for the DHCP server on the overlay logical switch.

12. \(Optional\) Select a DHCP relay service. 
13. Click **Add**. 

