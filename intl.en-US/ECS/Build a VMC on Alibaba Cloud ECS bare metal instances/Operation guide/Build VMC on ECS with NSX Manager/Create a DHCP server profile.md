# Create a DHCP server profile {#task_ihr_chz_lgb .task}

This topic describes how to create a DHCP server profile that specifies an NSX Edge cluster or the members of an NSX Edge cluster. A DHCP server with this profile processes DHCP requests from virtual machines on the logical switches. These logical switches are connected to the NSX Edge nodes specified in the profile.

1.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **DDI** \> **DHCP** \> **Server Profiles**, and then click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886443336117_en-US.png)

 
3.  Enter a server profile name. 
4.  \(Optional\) Enter a description. 
5.   Select an NSX Edge cluster from the drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85014/154886443336118_en-US.png)

 
6.  \(Optional\) Select the members of the NSX Edge cluster. 

    **Note:** You can specify up to two members.

7.  Click **Add**. 

