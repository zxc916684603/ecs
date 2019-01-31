# Attach a DHCP server to a logical switch {#task_crx_2hz_lgb .task}

This topic describes how to attach a DHCP server to an overlay logical switch. A DHCP server must be attached to a logical switch before processing DHCP requests from virtual machines connected to the logical switch because DHCP servers are not directly supported by VLAN logical switches.

1.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Choose **DDI** \> **DHCP**, and then click the **Servers** tab. 
3.  Select the DHCP server. 
4.  Select **Attach to Logical Switch** from the **Actions** drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154892200936127_en-US.png)

 
5.   Select the created overlay logical switch from the drop-down list, and then click **ATTACH**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154892200936128_en-US.png)

  

