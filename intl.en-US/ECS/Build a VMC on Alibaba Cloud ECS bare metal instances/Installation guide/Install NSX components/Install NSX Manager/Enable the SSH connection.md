# Enable the SSH connection {#task_lv4_rl2_kgb .task}

This topic describes how to enable the SSH connection when you deploy the NSX Manager OVF template.

1.  In the left-side navigation pane, right-click NSX Manager, and the click **Open Console**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154886386035900_en-US.png)

 
2.  Run the `service ssh status` command to view the SSH service status. 
3.  \(Optional\) Run the following commands to enable the SSH service: 

    ```
    service ssh start
    systemctl enable ssh
    ```


