# Create an NFS datastore {#task_iyb_tm5_ggb .task}

This topic describes how to mount an NFS volume and use it as a VMFS datastore.

1.  Log on to the [NAS console](https://nas.console.aliyun.com/#/ofs/list) to create a file system. For more information, see [Create a file system](../../../../../intl.en-US/Quick Start/Create a file system.md#) and [Add a mount point](../../../../../intl.en-US/Quick Start/Add a mount point.md#). 
2.  Click the name of the file system, and then go to the details page to obtain the server address of the file system. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687935493_en-US.png) 
3.  Log on to VMware vSphere Web Client. 
4.  Right-click the host that provides network management utilities, and select **Storage** \> **New Datastore**. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83719/154857687935472_en-US.png) 
5.  Select NFS for the datastore type. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687935486_en-US.png) 
6.  Select NFS 3 for the NFS version. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687935487_en-US.png) 
7.  Specify the datastore name and the folder. Enter the server address of the file system obtained in step 2. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687935488_en-US.png) 
8.  Review the datastore settings and click**Finish** to mount the NFS volume to the host that provides network management utilities. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687935489_en-US.png) 
9.   To mount the NFS volume to the other host, click the storage icon in the navigator panel of vSphere Web Client, right-click the NFS volume, and then click **Mount Datastore to Additional Hosts**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687938162_en-US.png)

 
10. Select the host on which you want to mount the datastore, and then click **OK** to mount the NFS volume on the host.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83765/154857687938163_en-US.png)

 

