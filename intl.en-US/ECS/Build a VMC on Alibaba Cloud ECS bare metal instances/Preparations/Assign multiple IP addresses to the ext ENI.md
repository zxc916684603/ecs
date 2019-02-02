# Assign multiple IP addresses to the ext ENI {#task_qqv_4ch_4gb .task}

This topic describes how to assign multiple IP addresses to the eni-ext ENI.

1.  Browse [AlibabaCloud OpenAPI Explorer](https://api.aliyun.com). 
2.  In the left-side navigation pane, click **Elastic Compute Service**. 
3.  Search DescribeRegions in the search box. 
4.  On the **DescribeRegions** page, select the region to which the VPC belongs from the **RegionID** drop-down list, and then click **Submit Request**. 
5.   Record the region ID that is displayed in the response code.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119944/154886282438116_en-US.png)

 
6.  In the left-side navigation pane, click **Elastic Compute Service** and enter AssignPrivateIpAddresses in the search box. 
7.   On the **AssignPrivateIpAddresse** page, set the parameters as follows:![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119944/154886282438119_en-US.png)

 
    1.  Select the region to which the VPC belongs from the **RegionID** drop-down list.
    2.  To assign the private IP addresses to the ENI, obtain the ENI ID from the ENI page in ECS console \(eni-ext ENI is selected in this example\), and then enter the ENI ID in the **NetworkInterfaceId** field.
    3.  Enter the number of private IP addresses in the **SecondaryPrivateIpAddressCount** field.
    4.  Click **Submit Request**.
8.  In the left-side navigation pane, click **Elastic Compute Service** and enter DescribeNetworkInterfaces in the search box. 
9.  On the **DescribeNetworkInterfaces** page, set the parameters as follows: 
    1.  Select the region to which the VPC belongs from the **RegionID** drop-down list.
    2.  Enter the ENI ID in the **NetworkInterfaceId** field.
    3.  Click **Submit Request**.
    4.  Obtain the assigned private IP addresses marked as false from the response code.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83055/154886282435508_en-US.png)


