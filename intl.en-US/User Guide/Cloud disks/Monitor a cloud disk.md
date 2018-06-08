# Monitor a cloud disk {#concept_hvt_zkj_ydb .concept}

When using a cloud disk, consider the following performance parameters:

-   IOPS: Indicates Input/Output Operations per Second, which means the amount of write or read operations can be performed in one second. Transaction-intensive applications are sensitive to IOPS.

-   Throughput: Measures the data size successfully transferred per second, measured in MBps. Applications that require mass read or write operations are sensitive to throughput.


You can monitor the IOPS and throughput of a cloud disk in the ECS console. Alternatively, if you have installed CloudMonitor agent, you can monitor the disk in the CloudMonitor console.

To monitor the IOPS and throughput of a cloud disk in the ECS console, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select **Block Storage** \> **Cloud Disks**.
3.  Select a region.
4.  Find a cloud disk and click its ID to go to the Disk Details page.
5.  In the left-side navigation pane, click **Disk Monitoring**.
6.  On the Monitoring Information page, click the ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9684/5521_en-US.png) icon and set Start Time and End Time for monitoring information. You can check the monitoring information of a cloud disk for up to 15 days.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9684/5519_en-US.png)

7.  View the IOPS and throughput of the cloud disk.

    **Note:** Click a legend in the chart to view a single performance index of a cloud disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9684/5520_en-US.png)


