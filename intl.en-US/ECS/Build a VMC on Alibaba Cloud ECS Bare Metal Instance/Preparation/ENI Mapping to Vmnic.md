# ENI Mapping to Vmnic {#task_bsv_hhz_lgb .task}

This topic describes how to find each ENI its corresponding vmic and other relevant information.

1.  Open an SSH session to each host and log in with root privileges. 
2.   Enter the command `esxcli network nic list` to list all physical network adapters installed and loaded on the host. In this example, vmnics on the host that provides network management utilities are as shown in the following picture:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857616937861_en-US.png)

Vmnics on the other host are as shown in the following picture:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037862_en-US.png)

 
3.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
4.  Click **Elastic Computer Service** \> **Networks and Security** \> **ENI**. 
5.  Search the ENIs by their names. 
    -   eni-nsx-management ENIs are as shown in the following picture:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037863_en-US.png)

    -   eni-vmotion ENIs are as shown in the following picture:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037864_en-US.png)

    -   eni-vtep ENIs are as shown in the following picture:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037865_en-US.png)

    -   eni-ext ENI is as shown in the following picture:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037866_en-US.png)

6.  By comparing the MAC address, find each ENI its corresponding vmnic and PCI device. 
7.  To retrieve information more easily in further procedures, create a data table as shown in the following picture:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154857617037868_en-US.png)

 

