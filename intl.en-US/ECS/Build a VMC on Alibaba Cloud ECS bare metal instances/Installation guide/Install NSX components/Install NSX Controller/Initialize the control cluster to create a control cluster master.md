# Initialize the control cluster to create a control cluster master {#task_bv3_5y1_hgb .task}

This topic describes how to initialize the control cluster to create a control cluster master. To enable communication between NSX Controller and hypervisor host, you need to initialize the control cluster after installing the first NSX Controller.

-   You have installed at least one NSX Controller.
-   You have joined NSX Controller with the management plane.
-   You have verified admin privileges to log on to the NSX Controller appliance.
-   You have assigned a shared secret password, which is a user-defined shared secret password.

1.  Right-click the NSX Controller virtual appliance, and then choose **Power** \> **Power on** in the vCenter Server. 
2.  Right-click the NSX Controller virtual appliance and click **Open Console**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154886399535865_en-US.png)

 
3.  Enter the CLI admin username and password to log on to NSX Controller. 
4.  Run the `set control-cluster security-model shared-secret secret <secret>` command and enter a shared secret as prompted.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154886399635869_en-US.png)

 
5.  Run the `initialize control-cluster` command. This command configures the specified controller as the control cluster master. 

    **Note:** Only one controller must be initialized in the cluster.

6.  Run the `get control-cluster status verbose` command. Verify that is master and in majority are true, the status is active, and that Zookeeper Server IP status is reachable, ok.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154886399635870_en-US.png)

 

