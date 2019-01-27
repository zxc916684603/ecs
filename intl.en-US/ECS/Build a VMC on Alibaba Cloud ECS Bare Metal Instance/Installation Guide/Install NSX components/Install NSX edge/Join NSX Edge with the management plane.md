# Join NSX Edge with the management plane {#task_vtx_jz1_hgb .task}

This topic describes how to join NSX Edge with the management plane.

-   Log on to the Windows instance where VMware vCenter Server is installed.
-   Obtain the certificate thumbprint of NSX Manager in the [preceding topics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Installation Guide/Install NSX components/Install NSX controller/Configure the VMKernel network interface.md#).

1.  Right-click the NSX Edge virtual appliance, and then click **Power** \> **Power on** to launch NSX Edge. 
2.   Right-click the NSX Edge virtual appliance, and then click **Open Console**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154857776335865_en-US.png)

 
3.  Enter the CLI admin username and password to log on to NSX Edge. 
4.  Run the `join management-plane` command. 

    **Note:** If you have multiple NSX Edge nodes, you need to run the `join management-plane` command on each NSX Edge node. The command includes the following information:

    -   Hostname or IP address of NSX Manager with an optional port number
    -   Username of NSX Manager
    -   Certificate thumbprint of the NSX Manager.
    -   Password of the NSX Manager.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154857776335866_en-US.png)

5.  Verify the result by running the `get managers` command on your NSX Edge. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154857776336871_en-US.png)

6.   In the NSX Manager UI, select **Fabric** \> **Nodes**. The NSX Edge is displayed on the Edges tab page. Manager connectivity should be **Up**. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85019/154857776337233_en-US.png)

 

