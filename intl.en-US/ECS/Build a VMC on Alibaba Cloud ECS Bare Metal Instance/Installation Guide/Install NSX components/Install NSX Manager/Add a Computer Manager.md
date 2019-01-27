# Add a Computer Manager {#task_pvh_py1_hgb .task}

A computer manager is an application that managers resources such as hosts and virtual machines. NSX-T Data Center polls compute managers to find out about changes such as the addition or removal of hosts or virtual machines and updates its inventory accordingly.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Select **Fabric** \> **Compute Managers** from the navigation panel. 
3.  Click **Add**. 
4.  Complete the compute manager details.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154857762437980_en-US.png)

 
    1.  Type the name to identify the vCenter Server.
    2.  Type the IP address of the vCenter Server.
    3.  Select vCenter as the type.
    4.  Type the vCenter Server login credentials.
    5.  Type the vCenter Server SHA-256 thumbprint algorithm value. If you left the thumbprint value blank, you are prompted to accept the server provided thumbprint.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154857762437984_en-US.png)

5.  Click **Add** to complete adding a compute manager. 

