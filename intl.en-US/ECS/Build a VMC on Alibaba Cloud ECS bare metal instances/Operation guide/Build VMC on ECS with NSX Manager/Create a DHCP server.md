# Create a DHCP server {#task_wmy_dhz_lgb .task}

This topic describes how to create a DHCP server that processes DHCP requests from the virtual machines connected to the logical switches.

1.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **DDI** \> **DHCP** \> **Servers**, and then click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236119_en-US.png)

 
3.  Enter a name for the DHCP server. 
4.  \(Optional\) Enter a description. 
5.  Enter the IP address of the DHCP server and its subnet mask in the **IP Address/mask** field \(in CIDR notation\) based on your VMware cloud IP addressing scheme. 
6.  Select a DHCP profile from the drop-down list. 
7.   \(Optional\) On the **Common Options** tab, enter a domain name, a default gateway, DNS servers, and a subnet mask, as shown in the following figure.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236120_en-US.png)

 
8.  \(Optional\) Set the parameters on the **Classless Static Route Option** tab. 
9.  \(Optional\) Set the parameters on the **Other Options** tab. 
10. Click **Add**. 
11. Click the newly created DHCP server. 
12.  On the **Overview** page, expand the **IP Pools** area and click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236121_en-US.png)

 
13. Enter a name for the IP pool. 
14.  Enter an IP pool range, for example, 10.100.100.2-10.100.100.252, based on the VMware cloud IP addressing scheme. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236122_en-US.png)

 
15. Set the default gateway, lease duration, warning threshold, and error threshold, and then click **Add**. 
16.  On the **Servers** tab page, click the **Edit** icon.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236123_en-US.png)

  
17.  On the **Other Options** tab page, click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236124_en-US.png)

  
18.  Select MTU Interface from the drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236125_en-US.png)

  
19.  Set the value of the **MTU Interface** to 1400, and then click **SAVE**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886445236126_en-US.png)

  

