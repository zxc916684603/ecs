# Prepare the network {#task_fzn_k5s_ggb .task}

The topic describes how to create a private network on Alibaba Cloud. The example in this topic shows how to create a VPC and six VSwitches.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/). 
2.  Select the VPC region. The VPC and cloud resources to be deployed must be located in the same region. 
3.  Create a VPC. For more information, see [Manage a VPC](../../../../../intl.en-US//Manage a VPC.md#). 

    **Note:** In this tutorial, the created VPC name is "vmware-on-xdragon", and the **IPv4 CIDR Block** is set to 192.168.0.0/16.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154892229535457_en-US.png)

4.  Go back to the VPC console, and then select the VPC region to which the VSwitch belongs. 
5.  In the left-side navigation pane, click **VSwitches**. 
6.  Create six VSwitches. For more information, see [Manage VSwitches](../../../../../intl.en-US//Manage VSwitches.md#). In this tutorial, set the required fields as follows. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154892229535458_en-US.png)

    **Note:** 

    -   The VSwitch, ECS Bare Metal \(EBM\), and ESXi host must be located in the same **Zone**.
    -   The names and IPv4 CIDR blocks are list in the following table.

        |VSwitch name|IPv4 CIDR block|
        |:-----------|:--------------|
        |ecsvm|192.168.60.0/24|
        |external|192.168.50.0/24|
        |vtep\_overlay|192.168.40.0/24|
        |vmotion|192.168.20.0/24|
        |management|192.168.10.0/24|


Six VSwitches are created. They are all controlled by the VPC **vmware-on-xdragon**.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83713/154892229535498_en-US.png)

