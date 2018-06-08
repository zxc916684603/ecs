# Change the private IP of an ECS instance {#task_bng_thn_xdb .task}

After creating a VPC ECS instance, you can change the private IP address and also can change the VSwitch of the ECS instance.

1.   Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home). 
2.   On the left-side navigation pane, click **Instances**. Click a region and then click the ID of the target ECS instance. 
3.   In the **Actions** column, click **More \> ** \> **Stop**. 
4.   When the instance is stopped, click the instance ID to go to the Instance Details page. 
5.   In the **Configuration Information** panel, click **More \>** \> **Modify Private IP Address**. 
6.   In Modify Private IP Address dialog, select a VSwitch, and then click **Modify**. 

    Ensure the zone of the selected VSwitch and the current VSwitch is the same.

    **Note:** Enter the new IP address if you do not want to change the VSwitch of the ECS instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9658/5483_en-US.png)

7.   Go back to the instance page, and in the **Actions** column, click **More \>** \> **Restart**to make the new private IP take effect. 

