# Enable the SSH connection {#task_lv4_rl2_kgb .task}

If the SSH connection is not enabled during the NSX Manager OVF template deployment, follows this topic.

1.  In the left-side navigation pane, right-click the NSX Manager, and choose **Open Console**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154857759335900_en-US.png)

 
2.  Run the `service ssh status` to view the SSH service run status. 
3.  \(Optional\) Run the following commands to enable the disabled SSH service: 

    ```
    service ssh start
    systemctl enable ssh
    ```


