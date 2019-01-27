# Update the MAC addresses of the VMK interfaces {#task_obm_nct_lgb .task}

This topic describes how to update the MAC addresses of VMK interfaces for host transport nodes in an overlay network.

1.  Open an SSH session to the host that provides network management utilities. 
2.  Run the `esxcli network ip interface list` command to view the N-VDS on the ESXi host. 

    The command output includes a VMK interface \(for example, vmk10\), with a VDS name that matches the name you used when you configured the transport zone and the transport node.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/103945/154857793237570_en-US.png)

3.   Run the `esxcli network ip interface ipv4 get` command to check the assigned tunnel endpoint address of the transport node. The vmk10 interface receives an IP address from the IP pool or DHCP, as shown in the following figure.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154857793236092_en-US.png)

 
4.   Run the `esxcli network nic list` command to check the physical NICs that have been installed and loaded. Obtain the MAC address of the physical vmnic. This physical vmnic corresponds to the unused vtep ENI of the host that provides the network management utilities.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/103945/154857793237574_en-US.png)

 
5.  Run the `vi /etc/vmware/esx.conf` command to open the configuration file. 
6.  Modify the MAC address of vmk10 to the MAC address obtained in step 4. 
7.  Modify the MAC address of vmk10 the same way for the other host. 
8.  Restart both hosts to validate the MAC address changes. 

