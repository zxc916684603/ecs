# Obtain information about the ENIs and their vmnics {#task_bsv_hhz_lgb .task}

This topic describes how to obtain information about the ENIs and their vmnics.

1.  Open an SSH session to each host and log on with root privileges. 
2.   Run the `esxcli network nic list` command to list all physical network adapters installed and loaded on the host. In this example, the vmnics on the host with network management utilities are shown in the following figure.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737861_en-US.png)

The vmnics on the other host are shown in the following figure.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737862_en-US.png)

 
3.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
4.  Choose **Elastic Computer Service** \> **Networks and Security** \> **ENI**. 
5.  Search the ENIs by their names. 
    -   The eni-nsx-management ENIs are shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737863_en-US.png)

    -   The eni-vmotion ENIs are shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737864_en-US.png)

    -   The eni-vtep ENIs are shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737865_en-US.png)

    -   The eni-ext ENI is shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105073/154886293737866_en-US.png)

6.  By comparing MAC addresses, locate each ENI, its vmnic, and the corresponding PCI device. 
7.  To retrieve information more easily later, create a data table as follows. 

    |Host|ENI|IP Address|MAC Address|ENI ID|PCI Device|
    |----|---|----------|-----------|------|----------|
    |host1 \(provides network utilities\)|eni-nsx-management: \(vmnic6\)|192.168.10.26|00:16:3e:06:63:96|eni-uf63lgnvlnoou16xnri4|0000:61:00.0|
    |eni-nsx-management: \(vmnic5\)|192.168.10.25|00:16:3e:08:99:26|eni-uf6i3wsd3qr46bmh37ol|0000:60:00.0|
    |eni-nsx-management: \(vmnic7\)|192.168.10.24|00:16:3e:08:ec:a9|eni-uf62khufqdz7x61fye6f|0000:62:00.0|
    |eni-vtep \(vmnic2\)-uplink|192.168.40.205|00:16:3e:08:f0:45|eni-uf6fzbx9n6b5mxm4ptas|0000:5d:00.0|
    |eni-vtep \(vmnic3\)|192.168.40.204|00:16:3e:08:e0:4f|eni-uf6b0mic4u0xryb1wl6t|0000:5e:00.0|
    |eni-ext \(vmnic4\)-uplink|192.168.50.143|00:16:3e:00:1c:37|eni-uf63lgnvlnoou35yrthc|0000:5f:00.0|
    |eni-vmotion \(vmnic1\)-uplink|192.168.20.109|00:16:3e:04:a7:55|eni-uf69povioymkn3y02gkw|0000:5c:00.0|
    |host2|eni-vmotion \(vmnic2\)-uplink|192.168.20.108|00:16:3e:08:2d:56|eni-uf610bu3dy95icu5vud2|0000:5d:00.0|
    |eni-vtep \(vmnic1\)|192.168.40.203|00:16:3e:06:7a:b2|eni-uf6i3wsd3qr46dli79nt|0000:5c:00.0|


