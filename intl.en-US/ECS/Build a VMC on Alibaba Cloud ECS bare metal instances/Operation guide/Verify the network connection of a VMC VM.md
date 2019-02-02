# Verify the network connection of a VMC VM {#task_err_svs_ggb .task}

This topic describes how to verify the network connection between the Virtual Machine \(VM\) and the DHCP server.

1.  Log on to VMware vSphere Web Client. 
2.  Right-click the target VMC VM, and then choose **Power** \> **Power On**. 
3.  Right-click the target VMC VM again, and then click **Open Console**. 
4.  Run the ip addr command to view all IP addresses associated with all network interfaces. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154886449636169_en-US.png)

5.  Run the `dhclient ens192` command to allow the virtual machine to connect to a DHCP server and retrieve the IP address, MTU, and other information from the DHCP server. 
6.  Run the ip addr command again to view the information retrieved from the DHCP server. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154886449736170_en-US.png)

7.  Ping the DHCP-assigned IP address and the gateway IP address to verify the network connection. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154886449736171_en-US.png)


