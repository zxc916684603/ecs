# Connect a tier-0 logical router to a VLAN logical switch {#task_ppx_fhz_lgb .task}

This topic describes how to connect a tier-0 logical router to a VLAN logical switch to create an NSX Edge uplink.

-   You have created a VLAN logical switch.
-   You have created a tier-0 router.

1.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **Routing** \> **Routers**, and then click the tier-0 logical router.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154891805636133_en-US.png)

 
3.  Choose **Configuration** \> **Router Ports** and click **ADD**. 
4.   Enter a name for the new tier-0 router port.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154891805636134_en-US.png)

 
5.  Enter an optional description. 
6.  Select Uplink in the **Type** field. 
7.  Set the MTU size less or equal to 1500. 
8.  Select the Edge transport node from the drop-down list. 
9.  Select Strict for the **URPF Mode**. Unicast Reverse Path Forwarding \(URPF\) is a security feature. 
10. Select the VLAN logical switch from the drop-down list. 
11. Select whether to attach the uplink router port to a new switch port or to an existing switch port. 
12. Type an IP address in CIDR notation in the same subnet as the connected port on the Top-of-Rack \(ToR\) switch. In this example, this IP address is the address of created **eni-ext** ENI that you can find in the ECS console. 

