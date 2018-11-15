# Step 2. Create an instance {#task_zjx_p1f_5db .task}

This article introduces how to quickly create an instance using the console by taking the entry-level instance type family for example. For more information, see [Create an instance](../../../../reseller.en-US/User Guide/Instances/Create an instance/Create an instance of the same configuration.md#). To use the API for instance creation, see [RunInstances](../../../../reseller.en-US/API Reference/Instances/RunInstances.md#).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs). 
2.  In the left-side navigation pane, click **Instances**. 
3.  On the Instances page, click **Create Instance** to enter the Custom purchase page. 
4.  Follow these steps to finish Basic Configurations. 
    1.  Select **Billing Method**. In this example, select **Pay-As-You-Go**. 
    2.  Select a region, such as China East 1. Select a zone, or allow one be allocated randomly, as by default. 

        **Note:** After an instance is created, you cannot change its region and zone.

    3.  Select an instance type and specify the quantity of instances. The available [Instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#) are determined by the region selected. In this example, select **All Generations** \> **x86-Architecture** \> **Entry-Level \(Shared\)** \> **Compact Type xn4**.
    4.  Select an image. In this example, the Public Image is selected. 
    5.  Select a storage space. In this example, only a system disk is used, and the 40 GiB Ultra Cloud Disk is selected, which is the default. 
5.  Click **Next: Networking** to finish the networking and security group configuration. 
    1.  Select **VPC** as the network type. In this example, select the default VPC and VSwitch. 
    2.  Set the network billing method. In this example, select **Assign public IP** and **Pay-By-Traffic**.
    3.  Select a security group. You can use the default security group if you do not create one. 
    4.  Add an Elastic Network Interface \(ENI\). Skip this step if the selected instance type does not support ENI. 
6.  Click **Next: System Configurations**. Set configurations as needed. We recommend that you set **Log on Credentials** and an **Instance Name**. In this example, select **Password** and set the instance name to ecs-01.
7.  Click **Next: Grouping**. You can set the options here as needed. In the case of multiple instances, we recommend that you add labels for ease of administration. 
8.  Click **Next: Preview**. Confirm the selected configuration. You can also click the edit icon to return and modify the configurations. 
9.  Read and confirm **Terms of Service**, then click **Create Instance**. 

Click **Console** to return to the ECS console. It generally takes one to five minutes to complete instance creation. Click the refresh button to check if the instance is created. If the newly created ECS instance is shown in a **Running** status, the instance is created successfully.

