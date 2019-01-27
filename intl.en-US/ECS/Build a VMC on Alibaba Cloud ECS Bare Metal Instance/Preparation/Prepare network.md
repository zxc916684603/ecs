# Prepare network {#task_fzn_k5s_ggb .task}

The topic describes how to create a private network on Alibaba Cloud. The topic example shows how to create a VPC and 6 VSwitches.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/). 
2.  Select the VPC region. The VPC and cloud resources to be deployed must be located in the same region. 
3.  Refer to the VPC document [Manage a VPC](../../../../../intl.en-US//Manage a VPC.md#) to create a VPC. 

    **Note:** In this tutorial, the created VPC name is "vmware-on-xdragon", and the **IPv4 CIDR Block** is set to 192.168.0.0/16.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154857516535457_en-US.png)

4.  Go back to the VPC console, and select the VPC region that the VSwitch belongs. 
5.  In the left-side navigation pane, click **VSwitches**. 
6.  Refer to the VPC document [Manage VSwitches](../../../../../intl.en-US//Manage VSwitches.md#) to create 6 VSwitches. In this tutorial, the required fields are entered as follows: 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154857516635458_en-US.png)

    **Note:** 

    -   The VSwitch, EBM, and ESXi host must be located in the same **Zone**.
    -   The name and IPv4 CIDR block are as follows:

        |VSwitch name|IPv4 CIDR block|
        |:-----------|:--------------|
        |ecsvm|192.168.60.0/24|
        |external|192.168.50.0/24|
        |vtep\_overlay|192.168.40.0/24|
        |vmotion|192.168.20.0/24|
        |management|192.168.10.0/24|


After you complete the operation, 6 VSwitches are created with the following **Name** and **IPv4 CIDR Block**, and they are all controlled by the VPC **vmware-on-xdragon**:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154857516635498_en-US.png)

