# Assign Multiple IP Addresses to Ext ENI {#task_qqv_4ch_4gb .task}

This topic describes how to apply and assign multiple IP addresses to theeni-ext ENI.

1.  Browse [AlibabaCloud OpenAPI Explorer](https://api.aliyun.com). 
2.  Click **Elastic Compute Service** in the left-side navigation pane. 
3.  Enter DescribeRegions in the search box and search. 
4.  In the **DescribeRegions** page, select the region same as the VPC's from the **RegionID** drop-down menu, then click **Submit Request**. 
5.   Record the region ID that is displayed in the response code, as shown in the following picture:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119944/154857615438116_en-US.png)

 
6.  Click **Elastic Compute Service** in the left-side navigation pane and enter AssignPrivateIpAddresses in the search box. 
7.  In the **AssignPrivateIpAddresse** page, complete the following procedures:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119944/154857615438119_en-US.png)

 
    1.  Select the region same as the VPC's from the **RegionID** drop-down menu.
    2.  To assign the private IP addresses to the ENI, obtain the ENI ID from the ENI page in ECS console \(eni-ext ENI is selected in this example\), enter the ENI ID in the **NetworkInterfaceId** field.
    3.  Enter the number of private IP addresses in the **SecondaryPrivateIpAddressCount** field.
    4.  Click **Submit Request**.
8.  Click **Elastic Compute Service** in the left-side navigation pane and enter DescribeNetworkInterfaces in the search box. 
9.   In the **DescribeNetworkInterfaces** page, complete the following procedures: 
    1.  Select the region same as the VPC's from the **RegionID** drop-down menu.
    2.  Enter the ENI ID in the **NetworkInterfaceId** field.
    3.  Click **Submit Request**.
    4.  Obtain the assigned private IP addresses marked as falsefrom the response code and write them down for further use.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83055/154857615435508_en-US.png)


