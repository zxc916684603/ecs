# Modify the VMkernel adapter MAC address {#task_sw4_4y1_hgb .task}

This topic describes how to modify the VMkernel adapter MAC address for each ESXi host.

1.   Check the MAC address that corresponds to the VMkernel adapter of the host that provides network management utilities.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84997/154857728435627_en-US.png)

 
2.   Check the MAC address that corresponds to the VMkernel adapter of the other host.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84997/154857728435629_en-US.png)

 
3.  Check the MAC address that corresponds to the physical adapter of the host that provides network management utilities. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84997/154857728435628_en-US.png)

4.  Check the MAC address that corresponds to the physical adapter of the other host.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84997/154857728435630_en-US.png)

 
5.  Open SSH sessions to both ESXi hosts, and then run the vi /etc/vmware/esx.conf command. 
6.  Find the corresponding MAC address of the VMkernel adapter, and then modify it to the MAC address of the physical adapter. 
7.  Restart both ESXi hosts to validate the modification. 

