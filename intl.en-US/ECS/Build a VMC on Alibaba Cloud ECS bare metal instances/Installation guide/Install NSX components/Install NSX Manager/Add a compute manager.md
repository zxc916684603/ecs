# Add a compute manager {#task_pvh_py1_hgb .task}

This topic describes how to add a compute manager. A compute manager is an application that manages resources such as hosts and virtual machines. NSX-T Data Center polls compute managers to find out changes such as the addition or removal of hosts or virtual machines and updates its inventory accordingly.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  From the left-side navigation pane, choose **Fabric** \> **Compute Managers**. 
3.  Click **Add**. 
4.  Set the compute manager parameters.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154892192437980_en-US.png)

 
    1.  Enter the name to identify vCenter Server.
    2.  Enter the IP address of vCenter Server.
    3.  Select vCenter as the type.
    4.  Enter the vCenter Server logon credentials.
    5.  Enter the vCenter Server SHA-256 thumbprint algorithm value. If you left the thumbprint value blank, you are prompted to accept the server provided thumbprint.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154892192437984_en-US.png)

5.  Click **Add**. 

