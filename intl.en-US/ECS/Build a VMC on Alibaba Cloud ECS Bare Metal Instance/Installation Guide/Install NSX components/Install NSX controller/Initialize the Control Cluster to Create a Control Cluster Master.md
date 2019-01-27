# Initialize the Control Cluster to Create a Control Cluster Master {#task_bv3_5y1_hgb .task}

To enable communication between controller and hypervisor host, initializing the control cluster is required after installing the first NSX Controller.

-   Install at least one NSX Controller.
-   Join the NSX Controller with the management plane.
-   Verify admin privileges to log in to the NSX Controller appliance.
-   Assign a shared secret password. A shared secret password is a user-defined shared secret password.

1.  Right-click the NSX Controller virtual appliance and click **Power** \> **Power on** in the vCenter Server. 
2.  Right-click the NSX Controller virtual appliance and click **Open Console**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154857770335865_en-US.png)

 
3.  Enter the CLI admin username and password to log in to the NSX Controller. 
4.  Run the `set control-cluster security-model shared-secret secret <secret>` command and type a shared secret when prompted.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154857770335869_en-US.png)

 
5.  Run the `initialize control-cluster` command. This command configures the specified controller as the control cluster master. 

    **Note:** Only one controller must be initialized in the cluster.

6.  Run the `get control-cluster status verbose` command. Verify that is master and in majority are true, the status is active, and that Zookeeper Server IP status is reachable, ok.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85020/154857770335870_en-US.png)

 

